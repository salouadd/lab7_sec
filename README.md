## TP : Analyse Dynamique d’une Application Android avec MobSF

### Objectif

L’objectif de ce TP est de mettre en place un environnement d’analyse de vulnérabilités et de malwares Android, puis de réaliser une analyse dynamique de l’application **DivaApplication.apk** à l’aide de **MobSF (Mobile Security Framework)**.

---

## Étape 1 : Démarrage de l’émulateur Android

Afin de permettre à MobSF d’interagir correctement avec l’émulateur — notamment pour installer des certificats, injecter des scripts Frida ou modifier certains composants système — il est nécessaire de lancer l’AVD (Android Virtual Device) avec les permissions d’écriture sur la partition système.

On commence par afficher la liste des émulateurs disponibles, puis on démarre l’AVD choisi (par exemple *Pixel_3_XL*) avec les options `-writable-system` et `-no-snapshot`.

### Lancement de l’émulateur

---

## Étape 2 : Configuration de l’environnement avec ADB

Une fois l’émulateur lancé, il faut vérifier qu’il est bien détecté par ADB et le préparer afin qu’il accepte les modifications effectuées par MobSF.

Les commandes suivantes permettent :

* de vérifier la connexion de l’émulateur ;
* d’activer les privilèges root ;
* de remonter la partition système en mode lecture/écriture.

```bash
adb devices
adb root
adb remount
```

### Configuration ADB

---

## Étape 3 : Analyse Statique avec MobSF

Avant de procéder à l’analyse dynamique, l’application **DivaApplication.apk** est analysée statiquement via MobSF.

Le tableau de bord fournit plusieurs informations importantes, notamment :

* les empreintes du fichier (MD5, SHA1 et SHA256) ;
* le score de sécurité global ;
* les composants exportés de l’application (Activities, Services, Content Providers), qui constituent une surface d’attaque potentielle.

### Analyse Statique MobSF

---

## Étape 4 : Analyse Dynamique

Après l’analyse statique, l’analyse dynamique est lancée. MobSF se connecte alors à l’émulateur configuré précédemment afin d’observer le comportement de l’application en temps réel.

L’interface d’analyse dynamique permet notamment de :

* surveiller l’écran de l’appareil en direct ;
* capturer et intercepter le trafic HTTP/HTTPS ;
* utiliser et modifier des scripts Frida pour contourner certaines protections, telles que :

  * le SSL Pinning ;
  * la détection du root ;
* monitorer les appels API et les comportements de l’application en temps réel.


