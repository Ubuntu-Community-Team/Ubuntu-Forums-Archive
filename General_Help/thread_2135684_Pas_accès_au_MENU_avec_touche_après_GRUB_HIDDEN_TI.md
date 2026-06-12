---
title: "Pas accès au MENU avec touche après GRUB_HIDDEN_TIMEOUT"
date: 2013-04-15
forum: General Help
---

### Post by 100305 on 2013-04-15
Bonjour à toutes et à tous,


J’ai recherché à rendre invisible la liste de menu des systèmes d’exploitations au démarrage de mon PC, en modifiant les variables situées dans /etc/default/grub ; 
GRUB _TIMEOUT 
GRUB_HIDDEN_TIMEOUT
  L’erreur commise, est d’avoir pris au sens propre et non figuré cette explication en anglais suivante  et avec cette commande :
  $ info -f grub
  ..We expect that most people who use GRUB_HIDDEN_TIMEOUT will want to have GRUB_TIMEOUT set to `0'..
  
et pas la mettre à 0 ! car maintenant que le « compte à rebours » du menu est nul il est bien normal qu’après y accéder, il ne se montre pas.
  
Je suis dans l’impossibilité de faire apparaitre donc et avec une saisie de touche le menu de liste des systèmes d’exploitations .

Ce qui a été fait ;
GRUB_TIMEOUT=0

décommenté la variable et attribué quatre seconde;
GRUB_HIDDEN_TIMEOUT=4

puis pour prendre en compte ces changements

update-grub
 
 
  
J'ai tout d'abord une question pour rétablir cette situation :

Est  t'il possible, simplement, de revenir à la configuration initiale "d'Ubuntu" et à partir d’un CD-Rom Debian en mode Rescue ?
  En effet, la partition de l’OS est bien visible ainsi  ( /dev/sdb7)?
 
 
  
Je veux dire par là précisément donc les choses suivantes;

éditer nano /etc/default/grub

modifier GRUB_TIMEOUT= 5

sauvegarder sous nano, Ctrl.


Et sinon pourquoi? Pour quelles raisons? Quels étapes seraient auxquels cas manquantes?

Merci par avance,
   
  Cordialement,

---

### Post by coffeecat on 2013-04-15
@100305, the common language of this forum is English. If you prefer to ask your question in French, the Ubuntu-France loco team has a forum here:

[http://forum.ubuntu-fr.org/](http://forum.ubuntu-fr.org/)

And their website is here:

[http://loco.ubuntu.com/teams/ubuntu-fr/](http://loco.ubuntu.com/teams/ubuntu-fr/)

---

### Post by GameX2 on 2013-04-15
> **100305 said:**
> Bonjour à toutes et à tous,


J’ai recherché à rendre invisible la liste de menu des systèmes d’exploitations au démarrage de mon PC, en modifiant les variables situées dans /etc/default/grub ; 
GRUB _TIMEOUT 
GRUB_HIDDEN_TIMEOUT
  L’erreur commise, est d’avoir pris au sens propre et non figuré cette explication en anglais suivante  et avec cette commande :
  $ info -f grub
  ..We expect that most people who use GRUB_HIDDEN_TIMEOUT will want to have GRUB_TIMEOUT set to `0'..
  
et pas la mettre à 0 ! car maintenant que le « compte à rebours » du menu est nul il est bien normal qu’après y accéder, il ne se montre pas.
  
Je suis dans l’impossibilité de faire apparaitre donc et avec une saisie de touche le menu de liste des systèmes d’exploitations .

Ce qui a été fait ;
GRUB_TIMEOUT=0

décommenté la variable et attribué quatre seconde;
GRUB_HIDDEN_TIMEOUT=4

puis pour prendre en compte ces changements

update-grub
 
 
  
J'ai tout d'abord une question pour rétablir cette situation :

Est  t'il possible, simplement, de revenir à la configuration initiale "d'Ubuntu" et à partir d’un CD-Rom Debian en mode Rescue ?
  En effet, la partition de l’OS est bien visible ainsi  ( /dev/sdb7)?
 
 
  
Je veux dire par là précisément donc les choses suivantes;

éditer nano /etc/default/grub

modifier GRUB_TIMEOUT= 5

sauvegarder sous nano, Ctrl.


Et sinon pourquoi? Pour quelles raisons? Quels étapes seraient auxquels cas manquantes?

Merci par avance,
   
  Cordialement,

You definitely could boot from a Live CD to restore the default value, if you want.
Is that what you're asking?

---

### Post by Locus Kiesselbachi on 2013-04-15
It looks like he has same problem as I did!
[Here!]("http://ubuntuforums.org/showthread.php?t=2134968")

---

### Post by 100305 on 2013-04-15
Yes excatly, 

I 've started this subjet on a famous Tchat Forum, beacause both operating systems are concerned by this error.

Below I le you know what i m planning to do but it is in French.
No Probleme to translate bue later;
Hope thez aoplogise anyway this is it 

Voici un résumé issu de cete page [size=50][https://www.isalo.org/wiki.debian-fr/R%C3%A9installer_Grub2](https://www.isalo.org/wiki.debian-fr/R%C3%A9installer_Grub2)[/size]pour modifier le cas échéant le fichier /etc/default/grub et la variable GRUB_TIMEOUT 
(le fichier Grub n’est pas endommagé ou a réparer, mais seulement à modifier)

_Première Etape_

Je lancer le Live CD de Debian et choisis en mode graphique, le mode Rescue

Je sélectionne la partition, que je connais, soit dans cet exemple, Ubuntu ;  /dev/sdb7  
pour pouvoir y accéder, en tant qu'administrateur et 'chrooter' le système de fichiers en question. C'est bien ça?

_Deuxieme Etape_

[size=85]```
# mkdir /mnt/chroot
# mount /dev/sdb7 /mnt/chroot

# mount --bind /dev/ /mnt/chroot/dev
# mount -t proc /proc /mnt/chroot/proc
# mount -t sysfs /sys /mnt/chroot/sys

# chroot /mnt/chroot
```[/size]

((Il peut parfois être nécessaire, en fonction de votre système ou du LiveCD à partir duquel vous avez démarré d'ajouter /bin/bash à la commande# chroot /mnt/chroot /bin/bash))

Vous êtes maintenant en tant que root sur votre système installé en dur.

Troisième Etape
[size=85]```
#nano /etc/default/grub
```[/size]

puis j'effectue les Modifications et enregistrement avec l’éditeur nano;

Enfin
[size=85]```
#update-grub
```[/size]

Merci de vos validations, en passant.


Cordialement,

> **Locus Kiesselbachi said:**
> It looks like he has same problem as I did!
[Here!]("http://ubuntuforums.org/showthread.php?t=2134968")

---

### Post by 100305 on 2013-04-15
Bonjour, 

Yes excatly, 

I 've started this subjet on a famous Tchat Forum, beacause both operating systems are concerned by this error.

Below I le you know what i m planning to do but it is in French.
No Probleme to translate bue later;
Hope thez aoplogise anyway this is it 

Voici un résumé issu de cete page [SIZE=1][https://www.isalo.org/wiki.debian-fr/R%C3%A9installer_Grub2](https://www.isalo.org/wiki.debian-fr/R%C3%A9installer_Grub2)[/SIZE]pour modifier le cas échéant le fichier /etc/default/grub et la variable GRUB_TIMEOUT 
(le fichier Grub n’est pas endommagé ou a réparer, mais seulement à modifier)

_Première Etape_

Je lancer le Live CD de Debian et choisis en mode graphique, le mode Rescue

Je sélectionne la partition, que je connais, soit dans cet exemple, Ubuntu ;  /dev/sdb7  
pour pouvoir y accéder, en tant qu'administrateur et 'chrooter' le système de fichiers en question.

_Deuxieme Etape_

[SIZE=3][SIZE=2]# mkdir /mnt/chroot
# mount /dev/sdb7 /mnt/chroot

# mount --bind /dev/ /mnt/chroot/dev
# mount -t proc /proc /mnt/chroot/proc
# mount -t sysfs /sys /mnt/chroot/sys[/SIZE]

[SIZE=2]# chroot /mnt/chroot[/SIZE][/SIZE]

((Il peut parfois être nécessaire, en fonction de votre système ou du LiveCD à partir duquel vous avez démarré d'ajouter /bin/bash à la commande# chroot /mnt/chroot /bin/bash))

Vous êtes maintenant en tant que root sur votre système installé en dur.

Troisième Etape
[SIZE=2]#nano /etc/default/grub[/SIZE]

puis j'effectue les Modifications et enregistrement avec l’éditeur nano; 

Enfin
[SIZE=2]#update-grub[/SIZE]

Merci de vos validations, en passant.


Cordialement,

> **Locus Kiesselbachi said:**
> It looks like he has same problem as I did!
[Here!]("http://ubuntuforums.org/showthread.php?t=2134968")

---

### Post by Elfy on 2013-04-15
Closed.

Please post in English here or go elsewhere to post in French.

Thanks.

---

