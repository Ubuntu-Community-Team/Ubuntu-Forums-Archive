---
title: "Synaptic error: can't find archive"
date: 2007-01-15
forum: General Help
---

### Post by Noelinho on 2007-01-15
I've got the following problem when I try to open Synaptic, as show in the image below:

[IMG]http://noelinho.jedimoose.org/images/synaptic_amnesia.jpg[/IMG]

What do I need to do to fix this and make Synaptic work again? I've tried apt-get update/upgrade/install flashplugin-nonfree, but it just gives me the same message in the terminal.

---

### Post by feest on 2007-01-15
try to search the package and remove it, now download it again and reinstall it. does this work?

---

### Post by Noelinho on 2007-01-17
I've not been able to find the package. I've attached my terminal output from when I try ro install the flashplugin-nonfree again:

```
noelinho@noelinho-desktop:~$ sudo aptitude install /home/noelinho/Desktop/flashplugin-nonfree_7.0.68~ubuntu3_i386.deb 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
E: Unknown pattern type: u
The following packages are BROKEN:
  flashplugin-nonfree 
The following packages have been automatically kept back:
  libgnomevfs2-dev libkadm55 libkrb5-dev 
The following packages have been kept back:
  gsfonts-x11 language-pack-af language-pack-am language-pack-an 
  language-pack-ar language-pack-az language-pack-be language-pack-bg 
  language-pack-bn language-pack-bs language-pack-ca language-pack-cs 
  language-pack-csb language-pack-de language-pack-el language-pack-en 
  language-pack-eo language-pack-es language-pack-et language-pack-eu 
  language-pack-fa language-pack-fi language-pack-fr language-pack-ga 
  language-pack-gl language-pack-gnome-af language-pack-gnome-am 
  language-pack-gnome-ar language-pack-gnome-ast language-pack-gnome-az 
  language-pack-gnome-be language-pack-gnome-bg language-pack-gnome-br 
  language-pack-gnome-bs language-pack-gnome-ca language-pack-gnome-cs 
  language-pack-gnome-de language-pack-gnome-el language-pack-gnome-en 
  language-pack-gnome-eo language-pack-gnome-es language-pack-gnome-et 
  language-pack-gnome-eu language-pack-gnome-fi language-pack-gnome-fil 
  language-pack-gnome-fr language-pack-gnome-fur language-pack-gnome-ga 
  language-pack-gnome-gl language-pack-gnome-hi language-pack-gnome-hr 
  language-pack-gnome-hu language-pack-gnome-id language-pack-gnome-ja 
  language-pack-gnome-pt language-pack-gnome-ru language-pack-gnome-zh 
  language-pack-gu language-pack-he language-pack-hi language-pack-hr 
  language-pack-hu language-pack-hy language-pack-id language-pack-ja 
  language-pack-pt language-pack-ru language-pack-zh libgnomevfs2-0 
  libgnomevfs2-bin libgnomevfs2-common libgnomevfs2-extra libkrb53 tzdata 
  vino 
0 packages upgraded, 0 newly installed, 0 to remove and 79 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
The following packages have unmet dependencies:
  flashplugin-nonfree: Depends: libruby (>= 1.6.7-3) but it is not installable
Resolving dependencies...
E: I wasn't able to locate a file for the flashplayer-nonfree package. This might mean you need to manually fix this package. (due to missing arch)
The following actions will resolve these dependencies:

Upgrade the following packages:
flashplugin-nonfree [7.0.25-5 (now) -> 7.0.68~ubuntu3 (edgy)]

Score is 0

Accept this solution? [Y/n/q/?] y
The following packages have been automatically kept back:
  libgnomevfs2-dev libkadm55 libkrb5-dev 
The following packages have been kept back:
  gsfonts-x11 language-pack-af language-pack-am language-pack-an 
  language-pack-ar language-pack-az language-pack-be language-pack-bg 
  language-pack-bn language-pack-bs language-pack-ca language-pack-cs 
  language-pack-csb language-pack-de language-pack-el language-pack-en 
  language-pack-eo language-pack-es language-pack-et language-pack-eu 
  language-pack-fa language-pack-fi language-pack-fr language-pack-ga 
  language-pack-gl language-pack-gnome-af language-pack-gnome-am 
  language-pack-gnome-ar language-pack-gnome-ast language-pack-gnome-az 
  language-pack-gnome-be language-pack-gnome-bg language-pack-gnome-br 
  language-pack-gnome-bs language-pack-gnome-ca language-pack-gnome-cs 
  language-pack-gnome-de language-pack-gnome-el language-pack-gnome-en 
  language-pack-gnome-eo language-pack-gnome-es language-pack-gnome-et 
  language-pack-gnome-eu language-pack-gnome-fi language-pack-gnome-fil 
  language-pack-gnome-fr language-pack-gnome-fur language-pack-gnome-ga 
  language-pack-gnome-gl language-pack-gnome-hi language-pack-gnome-hr 
  language-pack-gnome-hu language-pack-gnome-id language-pack-gnome-ja 
  language-pack-gnome-pt language-pack-gnome-ru language-pack-gnome-zh 
  language-pack-gu language-pack-he language-pack-hi language-pack-hr 
  language-pack-hu language-pack-hy language-pack-id language-pack-ja 
  language-pack-pt language-pack-ru language-pack-zh libgnomevfs2-0 
  libgnomevfs2-bin libgnomevfs2-common libgnomevfs2-extra libkrb53 tzdata 
  vino 
The following packages will be upgraded:
  flashplugin-nonfree 
1 packages upgraded, 0 newly installed, 0 to remove and 78 not upgraded.
Need to get 0B of archives. After unpacking 8192B will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Error!
E: I wasn't able to locate a file for the flashplayer-nonfree package. This might mean you need to manually fix this package. (due to missing arch)
E: Couldn't lock list directory..are you root?
noelinho@noelinho-desktop:~$ 

```

---

