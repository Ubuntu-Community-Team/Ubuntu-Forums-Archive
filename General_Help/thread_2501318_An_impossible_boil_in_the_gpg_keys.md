---
title: "An impossible boil in the gpg keys"
date: 2024-10-02
forum: General Help
---

### Post by Minus63 on 2024-10-02
Hello

I have a 24.04LTS installed, I wanted to install tixeo, installation that did not work, so I launched the installation by following another tutorial and then I realized that there was a mess when I made an apt update

```
Atteint :1 http://archive.ubuntu.com/ubuntu noble InRelease
Atteint :2 https://linux.teamviewer.com/deb stable InRelease
Atteint :3 http://security.ubuntu.com/ubuntu noble-security InRelease
Atteint :4 http://archive.ubuntu.com/ubuntu noble-updates InRelease
Atteint :5 http://archive.ubuntu.com/ubuntu noble-backports InRelease
Atteint :6 https://packages.microsoft.com/repos/code stable InRelease
Atteint :7 https://download.virtualbox.org/virtualbox/debian noble InRelease
Err :7 https://download.virtualbox.org/virtualbox/debian noble InRelease
  Les signatures suivantes n'ont pas pu être vérifiées car la clé publique n'est pas disponible : NO_PUBKEY A2F683C52980AECF
Lecture des listes de paquets... Fait
W: https://packages.microsoft.com/repos/code/dists/stable/InRelease: The key(s) in the keyring /etc/apt/trusted.gpg.d/microsoft.gpg are ignored as the file is not readable by user '_apt' executing apt-key.
W: https://packages.microsoft.com/repos/code/dists/stable/InRelease: The key(s) in the keyring /etc/apt/trusted.gpg.d/oracle.gpg are ignored as the file is not readable by user '_apt' executing apt-key.
W: https://packages.microsoft.com/repos/code/dists/stable/InRelease: La clé est stockée dans l'ancien trousseau de clés trust.gpg (/etc/apt/trusted.gpg), voir la section DÉPRÉCATION dans apt-key(8) pour plus de détails.
W: https://download.virtualbox.org/virtualbox/debian/dists/noble/InRelease: The key(s) in the keyring /etc/apt/trusted.gpg.d/microsoft.gpg are ignored as the file is not readable by user '_apt' executing apt-key.
W: https://download.virtualbox.org/virtualbox/debian/dists/noble/InRelease: The key(s) in the keyring /etc/apt/trusted.gpg.d/oracle.gpg are ignored as the file is not readable by user '_apt' executing apt-key.
W: Une erreur s'est produite lors du contrôle de la signature. Le dépôt n'est pas mis à jour et les fichiers d'index précédents seront utilisés. Erreur de GPG : https://download.virtualbox.org/virtualbox/debian noble InRelease : Les signatures suivantes n'ont pas pu être vérifiées car la clé publique n'est pas disponible : NO_PUBKEY A2F683C52980AECF
W: Impossible de récupérer https://download.virtualbox.org/virtualbox/debian/dists/noble/InRelease  Les signatures suivantes n'ont pas pu être vérifiées car la clé publique n'est pas disponible : NO_PUBKEY A2F683C52980AECF
W: Le téléchargement de quelques fichiers d'index a échoué, ils ont été ignorés, ou les anciens ont été utilisés à la place.
```

I didn't give up and found this post: [https://forum.ubuntu-fr.org/viewtopic.php?id=2081887](https://forum.ubuntu-fr.org/viewtopic.php?id=2081887)
Oracle and Microsoft seem to be behind it all

so:

```
apt-key list
Warning: apt-key is deprecated. Manage keyring files in trusted.gpg.d instead (see apt-key(8)).
/etc/apt/trusted.gpg
--------------------
pub   rsa2048 2015-10-28 [SC]
      BC52 8686 B50D 79E3 39D3  721C EB3E 94AD BE12 29CF
uid          [ inconnue] Microsoft (Release signing) <gpgsecurity@microsoft.com>

/etc/apt/trusted.gpg.d/microsoft.gpg
------------------------------------
pub   rsa2048 2015-10-28 [SC]
      BC52 8686 B50D 79E3 39D3  721C EB3E 94AD BE12 29CF
uid          [ inconnue] Microsoft (Release signing) <gpgsecurity@microsoft.com>

/etc/apt/trusted.gpg.d/oracle.gpg
---------------------------------
pub   rsa4096 2016-04-22 [SC]
      B9F8 D658 297A F3EF C18D  5CDF A2F6 83C5 2980 AECF
uid          [ inconnue] Oracle Corporation (VirtualBox archive signing key) <info@virtualbox.org>
sub   rsa4096 2016-04-22 [E]

/etc/apt/trusted.gpg.d/ubuntu-keyring-2012-cdimage.gpg
------------------------------------------------------
pub   rsa4096 2012-05-11 [SC]
      8439 38DF 228D 22F7 B374  2BC0 D94A A3F0 EFE2 1092
uid          [ inconnue] Ubuntu CD Image Automatic Signing Key (2012) <cdimage@ubuntu.com>

/etc/apt/trusted.gpg.d/ubuntu-keyring-2018-archive.gpg
------------------------------------------------------
pub   rsa4096 2018-09-17 [SC]
      F6EC B376 2474 EDA9 D21B  7022 8719 20D1 991B C93C
uid          [ inconnue] Ubuntu Archive Automatic Signing Key (2018) <ftpmaster@ubuntu.com>

```

followed by:

```

apt-key --keyring /etc/apt/trusted.gpg export 2980AECF | sudo gpg --dearmour -o /etc/apt/trusted.gpg.d/oracle.gpg
apt-key --keyring /etc/apt/trusted.gpg del 2980AECF

apt-key --keyring /etc/apt/trusted.gpg export BE1229CF | sudo gpg --dearmour -o /etc/apt/trusted.gpg.d/microsoft-teams.gpg
apt-key --keyring /etc/apt/trusted.gpg del BE1229CF

```

```

ls -l /etc/apt/trusted.gpg.d/
total 20
-rw-r--r-- 1 root root  641 sept. 23 18:02 microsoft.gpg
-rw------- 1 root root  641 sept. 25 16:39 microsoft-teams.gpg
-rw------- 1 root root 2247 sept. 25 16:29 oracle.gpg
-rw-r--r-- 1 root root 1165 nov.  28  2023 ubuntu-keyring-2012-cdimage.gpg
-rw-r--r-- 1 root root 1167 nov.  28  2023 ubuntu-keyring-2018-archive.gpg
-rw------- 1 root root    0 sept. 25 11:10 virtualbox.asc

```

I update again and it's even worse

```
apt update
Réception de :1 http://security.ubuntu.com/ubuntu noble-security InRelease [126 kB]
Atteint :2 http://archive.ubuntu.com/ubuntu noble InRelease
Atteint :3 https://linux.teamviewer.com/deb stable InRelease
Réception de :4 http://archive.ubuntu.com/ubuntu noble-updates InRelease [126 kB]
Atteint :5 http://archive.ubuntu.com/ubuntu noble-backports InRelease
Réception de :6 http://security.ubuntu.com/ubuntu noble-security/main Translation-en [81,6 kB]
Réception de :7 http://security.ubuntu.com/ubuntu noble-security/universe amd64 Packages [270 kB]
Réception de :8 http://security.ubuntu.com/ubuntu noble-security/universe Translation-en [113 kB]
Réception de :9 http://archive.ubuntu.com/ubuntu noble-updates/main amd64 Packages [531 kB]
Atteint :10 https://download.virtualbox.org/virtualbox/debian noble InRelease
Réception de :11 http://archive.ubuntu.com/ubuntu noble-updates/universe amd64 Packages [374 kB]
Err :10 https://download.virtualbox.org/virtualbox/debian noble InRelease
  Les signatures suivantes n'ont pas pu être vérifiées car la clé publique n'est pas disponible : NO_PUBKEY A2F683C52980AECF
Atteint :12 https://packages.microsoft.com/repos/code stable InRelease
1623 ko réceptionnés en 3s (473 ko/s)
Lecture des listes de paquets... Fait
W: https://download.virtualbox.org/virtualbox/debian/dists/noble/InRelease: The key(s) in the keyring /etc/apt/trusted.gpg.d/microsoft-teams.gpg are ignored as the file is not readable by user '_apt' executing apt-key.
W: https://download.virtualbox.org/virtualbox/debian/dists/noble/InRelease: The key(s) in the keyring /etc/apt/trusted.gpg.d/oracle.gpg are ignored as the file is not readable by user '_apt' executing apt-key.
W: Une erreur s'est produite lors du contrôle de la signature. Le dépôt n'est pas mis à jour et les fichiers d'index précédents seront utilisés. Erreur de GPG : https://download.virtualbox.org/virtualbox/debian noble InRelease : Les signatures suivantes n'ont pas pu être vérifiées car la clé publique n'est pas disponible : NO_PUBKEY A2F683C52980AECF
W: https://packages.microsoft.com/repos/code/dists/stable/InRelease: The key(s) in the keyring /etc/apt/trusted.gpg.d/microsoft-teams.gpg are ignored as the file is not readable by user '_apt' executing apt-key.
W: https://packages.microsoft.com/repos/code/dists/stable/InRelease: The key(s) in the keyring /etc/apt/trusted.gpg.d/oracle.gpg are ignored as the file is not readable by user '_apt' executing apt-key.
W: Impossible de récupérer https://download.virtualbox.org/virtualbox/debian/dists/noble/InRelease  Les signatures suivantes n'ont pas pu être vérifiées car la clé publique n'est pas disponible : NO_PUBKEY A2F683C52980AECF
W: Le téléchargement de quelques fichiers d'index a échoué, ils ont été ignorés, ou les anciens ont été utilisés à la place.

```

and the key list now looks like this:

```
apt-key list
Warning: apt-key is deprecated. Manage keyring files in trusted.gpg.d instead (see apt-key(8)).
/etc/apt/trusted.gpg
--------------------
pub   rsa2048 2015-10-28 [SC]
      BC52 8686 B50D 79E3 39D3  721C EB3E 94AD BE12 29CF
uid          [ inconnue] Microsoft (Release signing) <gpgsecurity@microsoft.com>

/etc/apt/trusted.gpg.d/microsoft.gpg
------------------------------------
pub   rsa2048 2015-10-28 [SC]
      BC52 8686 B50D 79E3 39D3  721C EB3E 94AD BE12 29CF
uid          [ inconnue] Microsoft (Release signing) <gpgsecurity@microsoft.com>

/etc/apt/trusted.gpg.d/microsoft-teams.gpg
------------------------------------------
pub   rsa2048 2015-10-28 [SC]
      BC52 8686 B50D 79E3 39D3  721C EB3E 94AD BE12 29CF
uid          [ inconnue] Microsoft (Release signing) <gpgsecurity@microsoft.com>

/etc/apt/trusted.gpg.d/oracle.gpg
---------------------------------
pub   rsa4096 2016-04-22 [SC]
      B9F8 D658 297A F3EF C18D  5CDF A2F6 83C5 2980 AECF
uid          [ inconnue] Oracle Corporation (VirtualBox archive signing key) <info@virtualbox.org>
sub   rsa4096 2016-04-22 [E]

/etc/apt/trusted.gpg.d/ubuntu-keyring-2012-cdimage.gpg
------------------------------------------------------
pub   rsa4096 2012-05-11 [SC]
      8439 38DF 228D 22F7 B374  2BC0 D94A A3F0 EFE2 1092
uid          [ inconnue] Ubuntu CD Image Automatic Signing Key (2012) <cdimage@ubuntu.com>

/etc/apt/trusted.gpg.d/ubuntu-keyring-2018-archive.gpg
------------------------------------------------------
pub   rsa4096 2018-09-17 [SC]
      F6EC B376 2474 EDA9 D21B  7022 8719 20D1 991B C93C
uid          [ inconnue] Ubuntu Archive Automatic Signing Key (2018) <ftpmaster@ubuntu.com>
```

I think I've made the situation worse by trying to get out of it on my own :(

Can you give me a hand to fix this?

Thanks in advance

---

### Post by Minus63 on 2024-10-04
up :(

---

### Post by Minus63 on 2024-10-07
up

---

