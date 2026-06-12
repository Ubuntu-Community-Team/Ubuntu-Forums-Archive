---
title: "Help me fix my locales please!"
date: 2013-02-24
forum: General Help
---

### Post by GameX2 on 2013-02-24
Hi,

I've had problems with the chinese language that wouldn't delete from my system - apparently, many people have this problem.
I've managed to remove the chinese language, finally:

[http://ubuntuforums.org/showpost.php?p=12523782&postcount=13](http://ubuntuforums.org/showpost.php?p=12523782&postcount=13)

Now, the only language that show up in "Gnome-Language-Selector" is French (France).  I would like to display only French (Canada).

I've changed a few settings, using localepurge and modifying languages files, because the English language is still used by a few applications, such as Ubuntu Tweak.  I cannot fully remove it!

What I get when I enter sudo locale-gen in the Terminal:

```
Generating locales...
  en_US.UTF-8... Can't open particularisation files « en_US »: No such file or directory
failed
  fr_BE.UTF-8... done
  fr_CA.UTF-8... Can't open particularisation files « en_CA »: No such file or directory
failed
  fr_CH.UTF-8... Can't open particularisation files « de_CH »: No such file or directory
failed
  fr_FR.UTF-8... done
  fr_LU.UTF-8... done
Generation complete.

```

Please help! :(
I have no clue where I should start to fix this, I've tried multiple solutions, but I can't fully remove English, and change language from French (France) to French (Canada). :(

Thanks !

---

### Post by matt_symes on 2013-02-24
Hi

Have you tried

```
sudo dpkg-reconfigure locales
```

Have you checked

```
/etc/default/locale 
```

to point to your default locale ?

what does

```
locale -a
```

return ?

Kind regards

---

### Post by GameX2 on 2013-02-24
> **matt_symes said:**
> Hi

Have you tried

```
sudo dpkg-reconfigure locales
```Have you checked

```
/etc/default/locale 
```to point to your default locale ?

what does

```
locale -a
```return ?

Kind regards

Thank you very much for your reply;

Here's what sudo dpkg-reconfigure locales return:

Generating locales...   en_US.UTF-8... Can't open particularisation files « en_US »: No such file or directory failed   fr_BE.UTF-8... up-to-date   fr_CA.UTF-8... Can't open particularisation files « en_CA »: No such file or directory failed   fr_CH.UTF-8... Can't open particularisation files « de_CH »: No such file or directory failed   fr_FR.UTF-8... up-to-date   fr_LU.UTF-8... up-to-date Generation complete.
The content of my /etc/default/locale :

```
LANG="fr_CA.UTF-8"
LANGUAGE="fr_CA.UTF-8"
LC_NUMERIC="fr_CA.UTF-8"
LC_TIME="fr_CA.UTF-8"
LC_MONETARY="fr_CA.UTF-8"
LC_PAPER="fr_CA.UTF-8"
LC_IDENTIFICATION="fr_CA.UTF-8"
LC_NAME="fr_CA.UTF-8"
LC_ADDRESS="fr_CA.UTF-8"
LC_TELEPHONE="fr_CA.UTF-8"
LC_MEASUREMENT="fr_CA.UTF-8"
```

locale -a return this:

```
C
C.UTF-8
fr_BE.utf8
fr_CA.utf8
fr_CH.utf8
fr_FR.utf8
fr_LU.utf8
POSIX
```

If it can help as well, here's how the file "/etc/environment" look like:

```
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
LANGUAGE="fr_CA.UTF-8"
LANG="fr_FR.CA.UTF-8"
LC_NUMERIC="fr_CA.UTF-8"
LC_TIME="fr_CA.UTF-8"
LC_MONETARY="fr_CA.UTF-8"
LC_PAPER="fr_CA.UTF-8"
LC_IDENTIFICATION="fr_CA.UTF-8"
LC_NAME="fr_CA.UTF-8"
LC_ADDRESS="fr_CA.UTF-8"
LC_TELEPHONE="fr_CA.UTF-8"
LC_MEASUREMENT="fr_CA.UTF-8"
```

And the file "~/.pam_environment" :
```

LANGUAGE=fr_CA.UTF-8
LANG=fr_CA.UTF-8
LC_NUMERIC=fr_CA.UTF-8
LC_TIME=fr_CA.UTF-8
LC_MONETARY=fr_CA.UTF-8
LC_PAPER=fr_CA.UTF-8
LC_NAME=fr_CA.UTF-8
LC_ADDRESS=fr_CA.UTF-8
LC_TELEPHONE=fr_CA.UTF-8
LC_MEASUREMENT=fr_CA.UTF-8
LC_IDENTIFICATION=fr_CA.UTF-8
```

Thank you very much.

---

### Post by matt_symes on 2013-02-24
Hi

In /etc/environment is this correct ?
```

LANG="fr_FR.CA.UTF-8"
```It's different than the others.

What programs are still appearing in English for you ? Not all programs are locale aware as far as i know.

BTW: What does this return ?

```
echo $LANG
echo $LANGUAGE
locale
```Kind regards

---

### Post by GameX2 on 2013-02-24
> **matt_symes said:**
> Hi

In /etc/environment is this correct ?
```

LANG="fr_FR.CA.UTF-8"
```It's different than the others and, as it's LANG, will override the others.

What programs are still appearing in English for you ? Not all programs are locale aware as far as i know.

BTW: What does this return ?

```
echo $LANG
echo $LANGUAGE
```Kind regards

Yes, /etc/environment file look correct:
```

PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
LANGUAGE="fr_CA.UTF-8"
LANG="fr_FR.CA.UTF-8"
LC_NUMERIC="fr_CA.UTF-8"
LC_TIME="fr_CA.UTF-8"
LC_MONETARY="fr_CA.UTF-8"
LC_PAPER="fr_CA.UTF-8"
LC_IDENTIFICATION="fr_CA.UTF-8"
LC_NAME="fr_CA.UTF-8"
LC_ADDRESS="fr_CA.UTF-8"
LC_TELEPHONE="fr_CA.UTF-8"
LC_MEASUREMENT="fr_CA.UTF-8"
```echo $LANG and echo $LANGUAGE both return this:

```
fr_CA.UTF-8
```As for the programs that still appear in English, there are more than I thought.  After doing a few tests:

- Ubuntu-Tweak (The interface is in English.  It used to be in French before the locales started to freak out).  A screenshot of the main windows strangely say the locale language is FR_CA, however.  That's weird:

[http://img15.imageshack.us/img15/5302/ubuntutweak001.png]("https://dl.dropbox.com/u/67605655/Ubuntu%20Tweak_001.png")

- GRUB-Customizer (This software used to display chinese caracthers, before I managed to delete the language);
- Audacity
- Pinta Image Editor
- VLC
- Screenlets
- GConf Editor
- Alacarte Menu Editor
- Shutter
- Guake Terminal
- Verbiste (A French verb checking tool.. Displayed in English. Oo)
- FileZilla (In preferences, the language is set to "Default System Language".  FileZilla apparently believe the default locale is English)

Other programs that are still in French:

- Baobab;
- GParted;
- LibreOffice;
- Firefox
- Chromium
- CCSM
- Software Center
- VirtualBox
- Evince
- Startup Disk Creator
- Xscreensaver
- FileRoller
- Brasero
- Rhythmbox
- Clementine
- Totem Player
- PlayOnLinux / Wine
- Gnome-Terminal
- EyeOfGnome
- Dropbox


Thank you!

EDIT: Synaptic also display in English.

---

### Post by matt_symes on 2013-02-24
Hi

I can't see too much wrong.

You could try setting

```
LC_ALL=fr_CA.UTF-8
```

in your locales and environment file.

Kind regards

---

### Post by GameX2 on 2013-02-24
> **matt_symes said:**
> Hi

I can't see too much wrong.

You could try setting

```
LC_ALL=fr_CA.UTF-8
```in your locales and environment file.

Kind regards

Hi,

I've modified my files as suggested;
My /etc/environment file now look like this:

```

PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
LANGUAGE="fr_CA.UTF-8"
LANG="fr_CA.UTF-8"
LC_ALL="fr_CA.UTF-8"
```

And my ~/.pam_environment like this:

```

LANGUAGE=fr_CA.UTF-8
LANG=fr_CA.UTF-8
LC_ALL=fr_CA.UTF-8
```

Unfortunately, I logged out, same problem.  I also ran again sudo dpkg-reconfigure locales and I still get this error:

```
Generating locales...
  en_US.UTF-8... Cannot open particularisation file « en_US »: No such file or directory
failed
  fr_BE.UTF-8... up-to-date
  fr_CA.UTF-8... Cannot open particularisation file « en_CA »: No such file or directory
failed
  fr_CH.UTF-8... Cannot open particularisation file « de_CH »: No such file or directory
failed
failed
  fr_FR.UTF-8... up-to-date
  fr_LU.UTF-8... up-to-date
```

Thanks to anyone who could help!

---

### Post by matt_symes on 2013-02-24
Hi

> fr_CA.UTF-8... Cannot open particularisation file « en_CA »: No such file or directory failedThat may be an issue then. Try reinstalling the locale files and regenerating.

```
sudo apt-get install --reinstall language-pack-{fr,en}
``````
sudo locale-gen fr_CA.UTF-8
``````
sudo dpkg-reconfigure locale
``````
sudo reboot
```Kind regards

---

### Post by GameX2 on 2013-02-24
Hi,

Thanks again for the help;

Here's the full output I received, when I ran your commands:

```
gamex@Portable-Ubuntu:~$ sudo apt-get install --reinstall language-pack-{fr,en}
[sudo] password for gamex: 
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
Les paquets supplémentaires suivants seront installés :
  firefox-locale-en language-pack-en-base
Les NOUVEAUX paquets suivants seront installés :
  firefox-locale-en language-pack-en language-pack-en-base
0 mis à jour, 3 nouvellement installés, 1 réinstallés, 0 à enlever et 0 non mis à jour.
Il est nécessaire de prendre 1 382 ko dans les archives.
Après cette opération, 5 082 ko d'espace disque supplémentaires seront utilisés.
Souhaitez-vous continuer [O/n] ? 
Réception de :1 http://ca.archive.ubuntu.com/ubuntu/ precise-updates/main language-pack-en-base all 1:12.04+20130128 [881 kB]
Réception de :2 http://ca.archive.ubuntu.com/ubuntu/ precise-updates/main language-pack-en all 1:12.04+20130128 [1 986 B]
Réception de :3 http://ca.archive.ubuntu.com/ubuntu/ precise-updates/main language-pack-fr all 1:12.04+20130128 [1 982 B]
Réception de :4 http://ca.archive.ubuntu.com/ubuntu/ precise-updates/main firefox-locale-en amd64 19.0+build1-0ubuntu0.12.04.1 [496 kB]
1 382 ko réceptionnés en 1s (876 ko/s)     
Sélection du paquet language-pack-en-base précédemment désélectionné.
(Lecture de la base de données... 234199 fichiers et répertoires déjà installés.)
Dépaquetage de language-pack-en-base (à partir de .../language-pack-en-base_1%3a12.04+20130128_all.deb) ...
Sélection du paquet language-pack-en précédemment désélectionné.
Dépaquetage de language-pack-en (à partir de .../language-pack-en_1%3a12.04+20130128_all.deb) ...
Préparation du remplacement de language-pack-fr 1:12.04+20130128 (en utilisant .../language-pack-fr_1%3a12.04+20130128_all.deb) ...
Dépaquetage de la mise à jour de language-pack-fr ...
Sélection du paquet firefox-locale-en précédemment désélectionné.
Dépaquetage de firefox-locale-en (à partir de .../firefox-locale-en_19.0+build1-0ubuntu0.12.04.1_amd64.deb) ...
Traitement des actions différées (« triggers ») pour « software-center »...
INFO:softwarecenter.db.update:translation information in database is up-to-date
Paramétrage de language-pack-fr (1:12.04+20130128) ...
Paramétrage de firefox-locale-en (19.0+build1-0ubuntu0.12.04.1) ...
Paramétrage de language-pack-en (1:12.04+20130128) ...
Paramétrage de language-pack-en-base (1:12.04+20130128) ...
Generating locales...
  en_AG.UTF-8... Ne peut ouvrir le fichier des particularisations « en_AG »: Aucun fichier ou dossier de ce type
failed
  en_AU.UTF-8... Ne peut ouvrir le fichier des particularisations « en_AU »: Aucun fichier ou dossier de ce type
failed
  en_BW.UTF-8... Ne peut ouvrir le fichier des particularisations « en_BW »: Aucun fichier ou dossier de ce type
failed
  en_CA.UTF-8... Ne peut ouvrir le fichier des particularisations « en_CA »: Aucun fichier ou dossier de ce type
failed
  en_DK.UTF-8... Ne peut ouvrir le fichier des particularisations « en_DK »: Aucun fichier ou dossier de ce type
failed
  en_GB.UTF-8... Ne peut ouvrir le fichier des particularisations « en_GB »: Aucun fichier ou dossier de ce type
failed
  en_HK.UTF-8... Ne peut ouvrir le fichier des particularisations « en_HK »: Aucun fichier ou dossier de ce type
failed
  en_IE.UTF-8... Ne peut ouvrir le fichier des particularisations « en_IE »: Aucun fichier ou dossier de ce type
failed
  en_IN.UTF-8... Ne peut ouvrir le fichier des particularisations « en_IN »: Aucun fichier ou dossier de ce type
failed
  en_NG.UTF-8... Ne peut ouvrir le fichier des particularisations « en_NG »: Aucun fichier ou dossier de ce type
failed
  en_NZ.UTF-8... Ne peut ouvrir le fichier des particularisations « en_NZ »: Aucun fichier ou dossier de ce type
failed
  en_PH.UTF-8... Ne peut ouvrir le fichier des particularisations « en_PH »: Aucun fichier ou dossier de ce type
failed
  en_SG.UTF-8... Ne peut ouvrir le fichier des particularisations « en_SG »: Aucun fichier ou dossier de ce type
failed
  en_US.UTF-8... Ne peut ouvrir le fichier des particularisations « en_US »: Aucun fichier ou dossier de ce type
failed
  en_ZA.UTF-8... Ne peut ouvrir le fichier des particularisations « en_ZA »: Aucun fichier ou dossier de ce type
failed
  en_ZM.UTF-8... Ne peut ouvrir le fichier des particularisations « en_ZM »: Aucun fichier ou dossier de ce type
failed
  en_ZW.UTF-8... Ne peut ouvrir le fichier des particularisations « en_ZW »: Aucun fichier ou dossier de ce type
failed
Generation complete.
Traitement des actions différées (« triggers ») pour « bamfdaemon »...
Rebuilding /usr/share/applications/bamf.index...
gamex@Portable-Ubuntu:~$ sudo locale-gen fr_CA.UTF-8
Generating locales...
  fr_CA.UTF-8... Ne peut ouvrir le fichier des particularisations « en_CA »: Aucun fichier ou dossier de ce type
failed
Generation complete.
gamex@Portable-Ubuntu:~$ sudo dpkg-reconfigure locales
Generating locales...
  en_AG.UTF-8... Ne peut ouvrir le fichier des particularisations « en_AG »: Aucun fichier ou dossier de ce type
failed
  en_AU.UTF-8... Ne peut ouvrir le fichier des particularisations « en_AU »: Aucun fichier ou dossier de ce type
failed
  en_BW.UTF-8... Ne peut ouvrir le fichier des particularisations « en_BW »: Aucun fichier ou dossier de ce type
failed
  en_CA.UTF-8... Ne peut ouvrir le fichier des particularisations « en_CA »: Aucun fichier ou dossier de ce type
failed
  en_DK.UTF-8... Ne peut ouvrir le fichier des particularisations « en_DK »: Aucun fichier ou dossier de ce type
failed
  en_GB.UTF-8... Ne peut ouvrir le fichier des particularisations « en_GB »: Aucun fichier ou dossier de ce type
failed
  en_HK.UTF-8... Ne peut ouvrir le fichier des particularisations « en_HK »: Aucun fichier ou dossier de ce type
failed
  en_IE.UTF-8... Ne peut ouvrir le fichier des particularisations « en_IE »: Aucun fichier ou dossier de ce type
failed
  en_IN.UTF-8... Ne peut ouvrir le fichier des particularisations « en_IN »: Aucun fichier ou dossier de ce type
failed
  en_NG.UTF-8... Ne peut ouvrir le fichier des particularisations « en_NG »: Aucun fichier ou dossier de ce type
failed
  en_NZ.UTF-8... Ne peut ouvrir le fichier des particularisations « en_NZ »: Aucun fichier ou dossier de ce type
failed
  en_PH.UTF-8... Ne peut ouvrir le fichier des particularisations « en_PH »: Aucun fichier ou dossier de ce type
failed
  en_SG.UTF-8... Ne peut ouvrir le fichier des particularisations « en_SG »: Aucun fichier ou dossier de ce type
failed
  en_US.UTF-8... Ne peut ouvrir le fichier des particularisations « en_US »: Aucun fichier ou dossier de ce type
failed
  en_ZA.UTF-8... Ne peut ouvrir le fichier des particularisations « en_ZA »: Aucun fichier ou dossier de ce type
failed
  en_ZM.UTF-8... Ne peut ouvrir le fichier des particularisations « en_ZM »: Aucun fichier ou dossier de ce type
failed
  en_ZW.UTF-8... Ne peut ouvrir le fichier des particularisations « en_ZW »: Aucun fichier ou dossier de ce type
failed
  fr_BE.UTF-8... done
  fr_CA.UTF-8... Ne peut ouvrir le fichier des particularisations « en_CA »: Aucun fichier ou dossier de ce type
failed
  fr_CH.UTF-8... Ne peut ouvrir le fichier des particularisations « de_CH »: Aucun fichier ou dossier de ce type
failed
  fr_FR.UTF-8... done
  fr_LU.UTF-8... done
Generation complete.
```

Please note that "Ne peut ouvrir le fichier des particularisations « en_US »: Aucun fichier ou dossier de ce type" mean as usual "Cannot open particularisation file "en_US": No such file or directory", in English.

I've rebooted (sudo reboot), but still no change.  English does not even appear in Gnome-Language-Selector. :/

---

### Post by matt_symes on 2013-02-24
Hi

Blimey. What changes did you make to your locales originally if reinstalling them did not fix it. :D

Can you post the output of 

```
cat /var/lib/locales/supported.d/* 
``````
ls -l /usr/lib/locale/*
``````
ls -l /var/lib/belocs
``````
ls -l /usr/lib/locale/locale-archive
```

```
cat /var/lib/locales/supported.d/local 
```

Kind regards

---

### Post by GameX2 on 2013-02-24
> **matt_symes said:**
> Hi

Blimey. What changes did you make to your locales originally if reinstalling them did not fix it. :D

Can you post the output of 

```
cat /var/lib/locales/supported.d/* 
``````
ls -l /usr/lib/locale/*
``````
ls -l /var/lib/belocs
``````
ls -l /usr/lib/locale/locale-archive
```Kind regards

Don't remember much what I did, sadly.
I remember I did " sudo apt-get install localepurge ".  I don't know if that was a good thing.

I've later followed these instructions to completely remove the Chinese language - that worked:

[http://ubuntuforums.org/showpost.php?p=12210991&postcount=3](http://ubuntuforums.org/showpost.php?p=12210991&postcount=3)

Here's the output of 

cat /var/lib/locales/supported.d/*
```
en_HK.UTF-8 UTF-8
en_DK.UTF-8 UTF-8
en_IN UTF-8
en_ZM UTF-8
en_ZW.UTF-8 UTF-8
en_NZ.UTF-8 UTF-8
en_PH.UTF-8 UTF-8
en_NG UTF-8
en_US.UTF-8 UTF-8
en_GB.UTF-8 UTF-8
en_AU.UTF-8 UTF-8
en_SG.UTF-8 UTF-8
en_BW.UTF-8 UTF-8
en_AG UTF-8
en_ZA.UTF-8 UTF-8
en_CA.UTF-8 UTF-8
en_IE.UTF-8 UTF-8
fr_CA.UTF-8 UTF-8
fr_LU.UTF-8 UTF-8
fr_CA.UTF-8 UTF-8
fr_CH.UTF-8 UTF-8
fr_BE.UTF-8 UTF-8
fr_FR.UTF-8 UTF-8
fr_CA.UTF-8 UTF-8
fr_CA.UTF-8 UTF-8
en_US.UTF-8 UTF-8
```

ls -l /usr/lib/locale/*
```
-rw-r--r-- 1 root root 2940272 fév 24 16:08 /usr/lib/locale/locale-archive

/usr/lib/locale/C.UTF-8:
total 1668
-rw-r--r-- 1 root root     131 oct  5 15:11 LC_ADDRESS
-rw-r--r-- 1 root root 1501202 oct  5 15:11 LC_COLLATE
-rw-r--r-- 1 root root  151984 oct  5 15:11 LC_CTYPE
-rw-r--r-- 1 root root     162 oct  5 15:11 LC_IDENTIFICATION
-rw-r--r-- 1 root root      23 oct  5 15:11 LC_MEASUREMENT
drwxr-xr-x 2 root root    4096 jan 31 21:17 LC_MESSAGES
-rw-r--r-- 1 root root     270 oct  5 15:11 LC_MONETARY
-rw-r--r-- 1 root root      62 oct  5 15:11 LC_NAME
-rw-r--r-- 1 root root      50 oct  5 15:11 LC_NUMERIC
-rw-r--r-- 1 root root      34 oct  5 15:11 LC_PAPER
-rw-r--r-- 1 root root      47 oct  5 15:11 LC_TELEPHONE
-rw-r--r-- 1 root root    1614 oct  5 15:11 LC_TIME
```

ls -l /var/lib/belocs
```
total 24
-rw-r--r-- 1 root root  798 fév 24 16:08 hashfile
-rw-r--r-- 1 root root 4131 fév 24 16:08 hashfile.new
-rw-r--r-- 1 root root   64 fév 24 16:07 hashfile.old
-rw-r--r-- 1 root root   71 fév 24 16:08 list
-rw-r--r-- 1 root root 2126 fév 24 16:08 locales.dep
```

ls -l /usr/lib/locale/locale-archive
```
-rw-r--r-- 1 root root 2940272 fév 24 16:08 /usr/lib/locale/locale-archive
```


***

Thanks! :)

---

### Post by matt_symes on 2013-02-24
Hi

Can you post the output of

```
ls /usr/share/i18n/locales/
```

```
ls -l /usr/share/i18n/locales/ | wc -l
```

Kind regards

---

### Post by GameX2 on 2013-02-24
Hi,

```
ls /usr/share/i18n/locales/
```

```
ast_ES  crh_UA      fr_CH       gez_ER@abegede  iso14651_t1         nan_TW@latin  sid_ET                 translit_compat    translit_wide
bem_ZM  csb_PL      fr_FR       gez_ET          iso14651_t1_common  nds_DE        tig_ER                 translit_font      unm_US
ber_DZ  eo          fr_FR@euro  gez_ET@abegede  iso14651_t1_pinyin  nds_NL        tlh_GB                 translit_fraction  wae_CH
ber_MA  fil_PH      fr_LU       hne_IN          kok_IN              nso_ZA        translit_circle        translit_hangul    wal_ET
bho_IN  fr_BE       fr_LU@euro  hsb_DE          lij_IT              pap_AN        translit_cjk_compat    translit_narrow    yue_HK
brx_IN  fr_BE@euro  fur_IT      i18n            mai_IN              POSIX         translit_cjk_variants  translit_neutral
byn_ER  fr_CA       gez_ER      ia              mhr_RU              shs_CA        translit_combining     translit_small
```

```
ls -l /usr/share/i18n/locales/ | wc -l

```

```
62
```

Thanks, I really appreciate it.  I've tried many things (Maybe even too much..), and I cannot solve the problem myself.

---

### Post by matt_symes on 2013-02-24
Hi

> I remember I did " sudo apt-get install localepurge "

Maybe that is the problem. I have never come across "Can't open particularisation files" error before.

From the terminal

```
sudo apt-get remove --purge localepurge
```

```
sudo apt-get purge locales
```

```
sudo mv /usr/share/i18n/locales/ /usr/share/i18n/locales_old
```

```
sudo apt-get install locales
```

```
sudo dpkg-reconfigure locales
```

Tell me how it goes.

Kind regards

---

### Post by GameX2 on 2013-02-24
Thanks.  Here's the full output:

```
sudo apt-get remove --purge localepurge


Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
Les paquets suivants seront ENLEVÉS :
  localepurge*
0 mis à jour, 0 nouvellement installés, 1 à enlever et 0 non mis à jour.
Après cette opération, 172 ko d'espace disque seront libérés.
Souhaitez-vous continuer [O/n] ? 
(Lecture de la base de données... 234816 fichiers et répertoires déjà installés.)
Suppression de localepurge ...
Purge des fichiers de configuration de localepurge ...

  To reinstall all the packages which localepurge has been taking care
  of before, you can use the following command:

    apt-get --reinstall install $(dpkg -S LC_MESSAGES | cut -d: -f1 | tr ', ' '
' | sort -u)

  For your further usage, the file "/var/tmp/reinstall_debs.sh"
  contains an enhanced version of the command line printed out above.

Traitement des actions différées (« triggers ») pour « man-db »...



gamex@Portable-Ubuntu:~$ sudo apt-get purge locales



Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
Le paquet suivant a été installé automatiquement et n'est plus nécessaire :
  firefox-locale-en
Veuillez utiliser « apt-get autoremove » pour les supprimer.
Les paquets suivants seront ENLEVÉS :
  language-pack-en* language-pack-en-base* language-pack-fr* language-pack-fr-base* language-pack-gnome-fr* language-pack-gnome-fr-base*
  libreoffice-help-en-gb* libreoffice-help-fr* libreoffice-l10n-en-gb* libreoffice-l10n-en-za* libreoffice-l10n-fr* locales* ubuntu-minimal*
0 mis à jour, 0 nouvellement installés, 13 à enlever et 0 non mis à jour.
Après cette opération, 100 Mo d'espace disque seront libérés.
Souhaitez-vous continuer [O/n] ? 
(Lecture de la base de données... 234806 fichiers et répertoires déjà installés.)
Suppression de libreoffice-help-en-gb ...
Suppression de libreoffice-help-fr ...
Suppression de libreoffice-l10n-en-gb ...
Suppression de libreoffice-l10n-en-za ...
Suppression de libreoffice-l10n-fr ...
Suppression de ubuntu-minimal ...
Suppression de language-pack-fr-base ...
Purge des fichiers de configuration de language-pack-fr-base ...
Suppression de language-pack-en-base ...
Purge des fichiers de configuration de language-pack-en-base ...
dpkg : avertissement : lors de la suppression de language-pack-en-base, le répertoire « /var/lib/locales/supported.d » n'était pas vide, donc il n'a pas été supprimé.
Suppression de language-pack-gnome-fr-base ...
Purge des fichiers de configuration de language-pack-gnome-fr-base ...
Suppression de locales ...
Purge des fichiers de configuration de locales ...
Suppression de language-pack-en ...
Suppression de language-pack-gnome-fr ...
Suppression de language-pack-fr ...
Traitement des actions différées (« triggers ») pour « software-center »...
WARNING:softwarecenter.db.update:setlocale failed with 'unsupported locale setting'
INFO:softwarecenter.db.update:no translation information in database needed
Traitement des actions différées (« triggers ») pour « bamfdaemon »...
Rebuilding /usr/share/applications/bamf.index...
Traitement des actions différées (« triggers ») pour « man-db »...
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory



gamex@Portable-Ubuntu:~$ sudo mv /usr/share/i18n/locales/ /usr/share/i18n/locales_old



mv: cannot stat `/usr/share/i18n/locales/': No such file or directory



gamex@Portable-Ubuntu:~$ sudo apt-get install locales


Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  firefox-locale-en
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  locales
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 3359 kB of archives.
After this operation, 9372 kB of additional disk space will be used.
Get:1 http://ca.archive.ubuntu.com/ubuntu/ precise/main locales all 2.13+git20120306-3 [3359 kB]
Fetched 3359 kB in 6s (514 kB/s)                                                                                                                              
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
    LANGUAGE = "fr_CA.UTF-8",
    LC_ALL = "fr_CA.UTF-8",
    LC_TIME = "fr_CA.UTF-8",
    LC_MONETARY = "fr_CA.UTF-8",
    LC_ADDRESS = "fr_CA.UTF-8",
    LC_TELEPHONE = "fr_CA.UTF-8",
    LC_NAME = "fr_CA.UTF-8",
    LC_MEASUREMENT = "fr_CA.UTF-8",
    LC_IDENTIFICATION = "fr_CA.UTF-8",
    LC_NUMERIC = "fr_CA.UTF-8",
    LC_PAPER = "fr_CA.UTF-8",
    LANG = "fr_CA.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
Selecting previously unselected package locales.
(Reading database ... 230873 files and directories currently installed.)
Unpacking locales (from .../locales_2.13+git20120306-3_all.deb) ...
Processing triggers for man-db ...
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
Setting up locales (2.13+git20120306-3) ...
/bin/bash: warning: setlocale: LC_ALL: cannot change locale (fr_CA.UTF-8)
Generating locales...
  en_US.UTF-8... /usr/sbin/locale-gen: line 177: warning: setlocale: LC_ALL: cannot change locale (fr_CA.UTF-8)
done
  fr_BE.UTF-8... /usr/sbin/locale-gen: line 177: warning: setlocale: LC_ALL: cannot change locale (fr_CA.UTF-8)
done
  fr_CA.UTF-8... /usr/sbin/locale-gen: line 177: warning: setlocale: LC_ALL: cannot change locale (fr_CA.UTF-8)
done
  fr_CH.UTF-8... /usr/sbin/locale-gen: line 177: warning: setlocale: LC_ALL: cannot change locale (fr_CA.UTF-8)
done
  fr_FR.UTF-8... /usr/sbin/locale-gen: line 177: warning: setlocale: LC_ALL: cannot change locale (fr_CA.UTF-8)
done
  fr_LU.UTF-8... /usr/sbin/locale-gen: line 177: warning: setlocale: LC_ALL: cannot change locale (fr_CA.UTF-8)
done
Generation complete.



gamex@Portable-Ubuntu:~$ sudo dpkg-reconfigure locales




Generating locales...
  en_US.UTF-8... up-to-date
  fr_BE.UTF-8... up-to-date
  fr_CA.UTF-8... up-to-date
  fr_CH.UTF-8... up-to-date
  fr_FR.UTF-8... up-to-date
  fr_LU.UTF-8... up-to-date
Generation complete.
```

Note that:

sudo mv /usr/share/i18n/locales/ /usr/share/i18n/locales_old
.. Was unsuccesful.  I think we're on the right track.  Purging the locales freed 100MB, and when I start "Gnome-Language-Selector", I get the message "Language is incompatible" for language-pack-fr.  Should I press "Install" ?

Ubuntu is reverted to English, for now.

Thanks!

---

### Post by matt_symes on 2013-02-24
HI

Can you post the output of

```
cat /etc/default/locale
``` 

```
 locale
``` 
> I get the message "Language is incompatible" for language-pack-fr.  Should I press "Install" ?
We can look at that in a moment

Kind regards

---

### Post by GameX2 on 2013-02-24
Hi,

cat /etc/default/locale

```
LANG="fr_CA.UTF-8"
LANGUAGE="fr_CA.UTF-8"
LC_NUMERIC="fr_CA.UTF-8"
LC_TIME="fr_CA.UTF-8"
LC_MONETARY="fr_CA.UTF-8"
LC_PAPER="fr_CA.UTF-8"
LC_IDENTIFICATION="fr_CA.UTF-8"
LC_NAME="fr_CA.UTF-8"
LC_ADDRESS="fr_CA.UTF-8"
LC_TELEPHONE="fr_CA.UTF-8"
LC_MEASUREMENT="fr_CA.UTF-8"
```
locale :

```
LANG=fr_CA.UTF-8
LANGUAGE=fr_CA.UTF-8
LC_CTYPE="fr_CA.UTF-8"
LC_NUMERIC="fr_CA.UTF-8"
LC_TIME="fr_CA.UTF-8"
LC_COLLATE="fr_CA.UTF-8"
LC_MONETARY="fr_CA.UTF-8"
LC_MESSAGES="fr_CA.UTF-8"
LC_PAPER="fr_CA.UTF-8"
LC_NAME="fr_CA.UTF-8"
LC_ADDRESS="fr_CA.UTF-8"
LC_TELEPHONE="fr_CA.UTF-8"
LC_MEASUREMENT="fr_CA.UTF-8"
LC_IDENTIFICATION="fr_CA.UTF-8"
LC_ALL=fr_CA.UTF-8
```Regards,

EDIT: Small typing mistake for this:

	 	 		 			 				> I get the message "Language is incompatible" for language-pack-fr.  Should I press "Install" ? 			 		

The actual message is:
> 
The language support is not installed completely
Some translations or writing aids available for your chosen languages are not installed yet. Do you want to install them now?

Details:
language-pack-fr
libreoffice-l10n-fr
libreoffice-help-fr
language-pack-gnome-fr

I haven't pressed anything, I'll wait.

---

### Post by matt_symes on 2013-02-24
Hi

I think we are getting there.

Please reboot your PC.

Wow So that's what localepurge is

[http://crunchbanglinux.org/wiki/howto/localepurge](http://crunchbanglinux.org/wiki/howto/localepurge)

Kind regards

---

### Post by matt_symes on 2013-02-24
Hi

According to the text from purging localepurge above you need to run this command

```
sudo apt-get --reinstall install $(dpkg -S LC_MESSAGES | cut -d: -f1 | tr ', ' ' ' | sort -u)
```

It will take a while to run as it's going to reinstall all the programs that locale purge stripped the language files from. This is why some of your programs where in English.

Kind regards

---

### Post by GameX2 on 2013-02-24
Done, I've rebooted.  The interface is now fully in English, as well as the softwares.
What's weird, is that "Gnome-Language-Selector" only display "French (France)" as installed.  I still get the popup:
> 
The language support is not installed completely
Some translations or writing aids available for your chosen languages are not installed yet. Do you want to install them now?

Details:
language-pack-fr
libreoffice-l10n-fr
libreoffice-help-fr
language-pack-gnome-fr 			 		

I don't know if it's related, but Dropbox displayed a popup, apparently showing that it's not installed, randomly.
As for PlayOnLinux, all my Windows programs refuse to start!

I don't related if it's related to the backup tool I've used (It use Rsync), or the English language switch.
I just hope this will get fixed when the language return back to French.

Thanks!

---

### Post by GameX2 on 2013-02-24
> **matt_symes said:**
> Hi

According to the text from purging localepurge above you need to run this command

```
sudo apt-get --reinstall install $(dpkg -S LC_MESSAGES | cut -d: -f1 | tr ', ' ' ' | sort -u)
```It will take a while to run as it's going to reinstall all the programs that locale purge stripped the language files from. This is why some of your programs where in English.

Kind regards

Done, here's the output:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reinstallation of plymouth-manager is not possible, it cannot be downloaded.
Reinstallation of playonlinux is not possible, it cannot be downloaded.
The following package was automatically installed and is no longer required:
  firefox-locale-en
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 56 reinstalled, 0 to remove and 0 not upgraded.
Need to get 112 MB/113 MB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? 
Get:1 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/ precise/main boot-sav all 3.197~ppa32~precise [383 kB]
Get:2 http://ca.archive.ubuntu.com/ubuntu/ precise-updates/main dpkg amd64 1.16.1.2ubuntu7.1 [1 830 kB]
Get:3 http://ppa.launchpad.net/cdemu/ppa/ubuntu/ precise/main cdemu-client all 1.5.0-1ubuntu0~precise1~ppa2 [27,0 kB]
Get:4 http://ppa.launchpad.net/cdemu/ppa/ubuntu/ precise/main gcdemu all 1.5.0-1ubuntu0~precise1~ppa5 [35,9 kB]
Get:5 http://ppa.launchpad.net/ubuntu-on-rails/ppa/ubuntu/ precise/main gedit-gmate amd64 0.10~uorppa6 [185 kB]
Get:6 http://ppa.launchpad.net/gloobus-dev/gloobus-preview/ubuntu/ precise/main gloobus-preview amd64 0.4.5-ubuntu11~ppa290-12.04 [817 kB]
Get:7 http://ca.archive.ubuntu.com/ubuntu/ precise/main e2fsprogs amd64 1.42-1ubuntu2 [966 kB]
Get:8 http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu/ precise/main grub-customizer amd64 3.0.4-0ubuntu1~ppa1p [739 kB]
Get:9 http://ca.archive.ubuntu.com/ubuntu/ precise-updates/main libc-bin amd64 2.15-0ubuntu10.3 [1 181 kB]
Get:10 http://ca.archive.ubuntu.com/ubuntu/ precise-updates/main apt amd64 0.8.16~exp12ubuntu10.7 [1 092 kB]
Get:11 http://ca.archive.ubuntu.com/ubuntu/ precise-updates/main libapt-pkg4.12 amd64 0.8.16~exp12ubuntu10.7 [934 kB]
Get:12 http://ppa.launchpad.net/bearoso/ppa/ubuntu/ precise/main snes9x-gtk amd64 1:1.53.81-1~precise1 [1 152 kB]
Get:13 http://ca.archive.ubuntu.com/ubuntu/ precise-updates/main libapt-inst1.4 amd64 0.8.16~exp12ubuntu10.7 [101 kB]
Get:14 http://ca.archive.ubuntu.com/ubuntu/ precise-updates/main language-selector-common all 0.79.1 [365 kB]
Get:15 http://ca.archive.ubuntu.com/ubuntu/ precise-updates/universe gstreamer0.10-plugins-bad amd64 0.10.22.3-2ubuntu2.2 [1 740 kB]
Get:16 http://ca.archive.ubuntu.com/ubuntu/ precise-updates/main update-notifier-common all 0.119ubuntu8.6 [222 kB]
Get:17 http://ca.archive.ubuntu.com/ubuntu/ precise/main debconf-i18n all 1.5.42ubuntu1 [226 kB]
Get:18 http://ca.archive.ubuntu.com/ubuntu/ precise/main iso-codes all 3.31-1 [3 547 kB]
Get:19 http://ca.archive.ubuntu.com/ubuntu/ precise/universe alacarte all 0.13.2-2ubuntu4 [94,2 kB]                                                           
Get:20 http://ca.archive.ubuntu.com/ubuntu/ precise/universe aptoncd all 0.1.98+bzr117-1.2 [222 kB]                                                           
Get:21 http://ca.archive.ubuntu.com/ubuntu/ precise-updates/universe audacity-data all 2.0.0-1ubuntu0.1 [2 628 kB]                                            
Get:22 http://ca.archive.ubuntu.com/ubuntu/ precise/universe bleachbit all 0.9.1-1 [327 kB]                                                                   
Get:23 http://ca.archive.ubuntu.com/ubuntu/ precise-updates/universe cheese-common all 3.4.1-0ubuntu2.1 [3 071 kB]                                            
Get:24 http://ca.archive.ubuntu.com/ubuntu/ precise/universe easytag amd64 2.1.7-1ubuntu2 [1 002 kB]                                                          
Get:25 http://ca.archive.ubuntu.com/ubuntu/ precise/main example-content all 46 [5 223 kB]                                                                    
Get:26 http://ca.archive.ubuntu.com/ubuntu/ precise/universe filezilla-common all 3.5.3-1ubuntu2 [2 996 kB]                                                   
Get:27 http://ca.archive.ubuntu.com/ubuntu/ precise/universe gconf-editor amd64 3.0.1-1ubuntu2 [1 143 kB]                                                     
Get:28 http://ca.archive.ubuntu.com/ubuntu/ precise/universe gedit-plugins amd64 3.3.4-0ubuntu1 [1 524 kB]                                                    
Get:29 http://ca.archive.ubuntu.com/ubuntu/ precise/universe gnome-applets-data all 3.4.1-0ubuntu1 [5 902 kB]                                                 
Get:30 http://ca.archive.ubuntu.com/ubuntu/ precise/universe gnome-color-manager amd64 3.4.0-1 [1 753 kB]                                                     
Get:31 http://ca.archive.ubuntu.com/ubuntu/ precise-updates/universe gnome-panel-data all 1:3.4.1-0ubuntu1.1 [2 621 kB]                                       
Get:32 http://ca.archive.ubuntu.com/ubuntu/ precise/universe gstreamer0.10-plugins-ugly amd64 0.10.18.3-1ubuntu1 [356 kB]                                     
Get:33 http://ca.archive.ubuntu.com/ubuntu/ precise/universe gtk-recordmydesktop all 0.3.8-4.1ubuntu1 [121 kB]                                                
Get:34 http://ca.archive.ubuntu.com/ubuntu/ precise/universe guake amd64 0.4.2-7 [153 kB]                                                                     
Get:35 http://ca.archive.ubuntu.com/ubuntu/ precise/universe gufw all 12.04.1-0ubuntu1 [224 kB]                                                               
Get:36 http://ca.archive.ubuntu.com/ubuntu/ precise/universe libmx-1.0-2 amd64 1.4.3-0ubuntu1 [331 kB]                                                        
Get:37 http://ca.archive.ubuntu.com/ubuntu/ precise/universe libquicktime2 amd64 2:1.2.3-4build2 [345 kB]                                                     
Get:38 http://ca.archive.ubuntu.com/ubuntu/ precise/universe libzvbi-common all 0.2.33-4 [35,7 kB]                                                            
Get:39 http://ca.archive.ubuntu.com/ubuntu/ precise/universe meld all 1.5.3-1ubuntu1 [410 kB]                                                                 
Get:40 http://ca.archive.ubuntu.com/ubuntu/ precise/universe menu amd64 2.1.46ubuntu1 [455 kB]                                                                
Get:41 http://ca.archive.ubuntu.com/ubuntu/ precise/universe nautilus-actions amd64 3.1.4-1build1 [14,7 MB]                                                   
Get:42 http://ca.archive.ubuntu.com/ubuntu/ precise/universe openshot all 1.4.0-1ubuntu1 [16,4 MB]                                                            
Get:43 http://ca.archive.ubuntu.com/ubuntu/ precise/universe pinta all 1.1-1 [675 kB]                                                                         
Get:44 http://ca.archive.ubuntu.com/ubuntu/ precise/universe pysdm all 0.4.1-0ubuntu3 [29,4 kB]                                                               
Get:45 http://ca.archive.ubuntu.com/ubuntu/ precise/universe screenlets-pack-all all 0.1.6-0ubuntu1 [16,9 MB]                                                 
Get:46 http://ca.archive.ubuntu.com/ubuntu/ precise/universe shutter all 0.88.1-1 [3 042 kB]                                                                  
Get:47 http://ca.archive.ubuntu.com/ubuntu/ precise/universe synaptic amd64 0.75.9ubuntu1 [2 419 kB]                                                          
Get:48 http://ca.archive.ubuntu.com/ubuntu/ precise/universe verbiste amd64 0.1.33-3 [88,9 kB]                                                                
Get:49 http://ca.archive.ubuntu.com/ubuntu/ precise-updates/universe vlc-data all 2.0.5-0ubuntu0.12.04.1 [9 466 kB]                                           
Get:50 http://ca.archive.ubuntu.com/ubuntu/ precise/main xdg-user-dirs amd64 0.14-0ubuntu2 [64,7 kB]                                                          
Get:51 http://ca.archive.ubuntu.com/ubuntu/ precise/universe backintime-common all 1.0.8-1 [171 kB]                                                           
Get:52 http://ca.archive.ubuntu.com/ubuntu/ precise/universe compizconfig-settings-manager all 0.9.5.92-0ubuntu3 [1 210 kB]                                   
Get:53 http://ca.archive.ubuntu.com/ubuntu/ precise-updates/universe cups-pk-helper amd64 0.2.1.2-1ubuntu0.1 [54,4 kB]                                        
Get:54 http://ca.archive.ubuntu.com/ubuntu/ precise/universe gm-notify all 0.10.3-0ubuntu2 [25,5 kB]                                                          
Get:55 http://ca.archive.ubuntu.com/ubuntu/ precise/universe screenlets all 0.1.6-0ubuntu1 [415 kB]                                                           
Fetched 112 MB in 45s (2 441 kB/s)
```Guess I should reboot..?

EDIT: Rebooted.  Interface is in English, Gnome-Language-Selector only show French (France) as installed, like before.

---

### Post by matt_symes on 2013-02-24
Hi

English is the fallback language "C". I would have expected the display to be in french by now.

**install those french laguage files now.**

can you post the output of

```
echo $LANGUAGE
echo $LANG
locale -a
```Kind regards

---

### Post by GameX2 on 2013-02-24
I  believe the reason why Dropbox and PlayOnLinux are getting weird (All  my PlayOnLinux programs crash :( ), it might be because both were  installed locally, from a DEB.
Interestingly, PlayOnLinux interface  remained in French.  Perhaps when the system will revert back to French,  this problem will be fixed as well.

---

### Post by GameX2 on 2013-02-24
Hi.


```
gamex@Portable-Ubuntu:~$ echo $LANGUAGE
fr_CA.UTF-8
gamex@Portable-Ubuntu:~$ echo $LANG
fr_CA.UTF-8
gamex@Portable-Ubuntu:~$ locale -a
C
C.UTF-8
en_US.utf8
fr_BE.utf8
fr_CA.utf8
fr_CH.utf8
fr_FR.utf8
fr_LU.utf8
POSIX
```

---

### Post by matt_symes on 2013-02-24
Hi

Install the french language packs.

Kind regards

---

### Post by GameX2 on 2013-02-24
Done.
I've rebooted and I'm back to French.  Gnome-Language-Selector display French (France) as the only installed language (Shouldn't it be shown "Français (France)" instead?.

Ubuntu-Tweak for example, still is in English.
Dropbox and PlayOnLinux aren't fixed (I hope that's because of the language switch, and not the backup testing..).

---

### Post by matt_symes on 2013-02-24
Hi

Reinstall Ubuntu-Tweak, dropbox and playonlinux.

Is the text in the terminal in french ?

Kind regards

---

### Post by GameX2 on 2013-02-24
Hi,

Yes, the output of the terminal is French.
Reinstalled Alacarte (Stuck in English).

.. Hey!  It's working !! :O
Alacarte is now displayed in French! :O

I did the same with Synaptic, and it's reverted back to French, as well.  I'll try reinstalling all the problematic packages from Synaptic, and I'll let you know the result.

I've tried reinstalling "Language-Selector-Gnome".  What I find a little odd, is that it still display "French (France)".  Not a big issue, but I believe it should normally display "Français (Canada)" instead?

I'll reinstall the wrong-language softwares.

THANKS ! :O

---

### Post by matt_symes on 2013-02-24
Hi

That's great news. :)

As you reinstall each problematic package it will download the french language files for it.

I think we should have installed the french language packs before running that apt-get command from localepurge.

Kind regards

---

### Post by GameX2 on 2013-02-24
> **matt_symes said:**
> Hi

That's great news. :)

As you reinstall each problematic package it will download the french language files for it.

I think we should have installed the french language packs before running that apt-get command from localepurge.

Kind regards

So far, everything is working great, all softwares I am aware of reverted back to French. :)

Could we ran the locale-purge command again, install the French language pack, and re-run the command?

What if some softwares dependencies still are configured in English?  Will that cause errors for the softwares?

I haven't managed to reinstall PlayOnLinux yet, that's not standard, since it was installed from a DEB - from the official website.

I should do a backup of the full .PlayOnLinux folder..
Hell, I do NOT want to reinstall Office 2010. XD

That's the worst thing ever. XD  That license check could easily freak out, if I reinstall Office completely (That's a legal license).

I'll backup the folder, and redownload the DEB from the website.
Funny, how the most painful and long thing on Linux is probably to install Windows programs, and especially make games work (I'm not a big gamer, I play 2002-03 games.  They all work!) !  Installing Office : stupid license check that's not working as it should ("You have exceeded the license activation number"  What?  Hey, I'm just reinstalling the software, and I get this?").

Oh, the worst clearly is to make PhotoShop work.  I've succeeded only once with CS5.  The software refused to start, after one launch..
I run Adobe programs on a Windows XP VM.  Less problematic.


I'll let you know how the PlayOnLinux reinstallation goes!

---

### Post by matt_symes on 2013-02-24
> **GameX2 said:**
> So far, everything is working great, all softwares I am aware of reverted back to French. :)

Great :D

> 
Could we ran the locale-purge command again, install the French language pack, and re-run the command?

That could be risky. locales can be a pain to fix if you have problems. Unless you really need to i would not bother.

> 
What if some softwares dependencies still are configured in English?  Will that cause errors for the softwares?

It should not cause problems. I think you will get all your software in French if you reinstall each software that is in English.

> 
I haven't managed to reinstall PlayOnLinux yet, that's not standard, since it was installed from a DEB - from the official website.

I should do a backup of the full .PlayOnLinux folder..
Hell, I do NOT want to reinstall Office 2010. XD

That's the worst thing ever. XD  That license check could easily freak out, if I reinstall Office completely (That's a legal license).

Hopefully you can reinstall it over the top after making a backup of the config files.

Good luck and post back if you have any issues

Kind regards

---

### Post by GameX2 on 2013-02-24
YES !!

Got it!
I backed up PlayOnLinux drives, wiped PlayOnLinux next, and reinstalled it from the official DEB.  Unfortunately, that did not fixed the program launching bug, after restoring my backed up configuration.  The Windows programs kept crashing - impossible to start.
Used Synaptic, I found all the softwares I installed myself, so I reinstalled the vast majority of them (Excluding libraries and plugins).  I've realised that I forgot many that were still stuck in English.

I restored an earlier backup of .PlayOnLinux folder (As soon as I got Office working, man, I backed up the whole folder... XD).  I also changed the file permissions.

In fact, I've tested a new backup tool, today (Never configured backup myself.  On our main Windows family PC, that always was my father who was configuring backup).  I find it interesting, but I just found something annoying..

I'm backing up my Home directory to an NTFS external drive.  This might be a Linux limitation, but on an NTFS partition, the file/folder permissions got erased!

So the permissions of the folder "PlayOnLinux" were set to "ReadOnly", that probably was the bug.  The scripts also weren't executables as they should have been.  When PlayOnLinux launch a program, it launch a script to configure Wine, but the permissions of these shortcuts/scripts got wiped.

Managed to fix this!  Still don't know why the Language Selector display French (France) instead of Français (France) (Is there even a difference between French France and French Canada, anyways?), but anyways, everything is displayed in French, now!

Now I need to find a working backup tool!
It's easy to screw up a Linux installation, that happened to me a few times..  So annoying.  Never imagine fixing locales would be THAT difficult!

Thank you !! :D

---

