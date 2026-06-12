---
title: "install cd customization"
date: 2005-10-26
forum: General Help
---

### Post by faz on 2005-10-26
Hi to all,
maybe this is not the right forum to post to, excuse me if I'm wrong :(

I'm trying to build a custom install cd just to add italian language support, I'm following some guides, expecially [https://wiki.ubuntu.com/InstallCDCustomizationHowTo](https://wiki.ubuntu.com/InstallCDCustomizationHowTo)

but I can't get it working...

I created this preseed file:
```
base-config	base-config/package-selection	string ~tubuntu-standard|~tubuntu-desktop|language-pack-it|language-pack-gnome-it|language-support-it|openoffice.org2-help-it
```

and this is my isolinux.cfg
```
DEFAULT /install/vmlinuz
APPEND   preseed/file=/cdrom/preseed/italian.seed vga=normal initrd=/install/initrd.gz ramdisk_size=16384 root=/dev/rd/0 rw --
```

and this is the new pool directory that I created
[IMG]http://www.heredium.it/avatar/pool.jpg[/IMG]

I updated the Packages/Release file and I singed it all with gpg.

The system boots fine and the installation process goes well but there are some problems:
[LIST=1]
[*]the installer hangs on "CONFIGURING APT" saying "error configuring APT", I can't get a better error log
[*]my packages are not installed and I can't get the 2nd stage going on
[/LIST]

I can't understand what kind of problem do the system have, can someone help me?
Thank you very much to all!

---

### Post by Jenda on 2005-10-26
My [wild] guess is that apt is trying to configure itself to a localised repo, and since the lacalisation aspect of the installation has been tinkered with, it's causing problems... just a guess.

---

### Post by faz on 2005-10-26
Thank you Jenda, anyway I'm trying another approach, changing the preseed file using: 

- "early command" to copy my debs somewhere 
- "late command" to install them

but I still have a question, I call "dpkg -i *" but the installation process ask for some user input that I would not have, I looked at the dpkg man but it seems not possible to use a "-y" option to do "all yes"...

are there some possibilities to avoid interactive dpkg package installation?

thank you again
faz

---

### Post by Jenda on 2005-10-26
Sorry, I don't know.

---

