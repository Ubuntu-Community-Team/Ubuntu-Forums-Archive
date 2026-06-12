---
title: "Stuck up in &quot;Installing the base system&quot;"
date: 2007-06-04
forum: General Help
---

### Post by zappazzi on 2007-06-04
hi,

this is my 3rd attempt of installing ubunti using wubi and still got no luck. im stuck in "Installing the base system" around 6% :(

got this :
> 
Jun 4 14:04:27 main-menu[32406]: INFO: Falling back to the package description for migration-assistant
Jun 4 14:04:28 main-menu[32406]: INFO: Falling back to the package description for console-setup-udeb
Jun 4 14:04:28 main-menu[32406]: INFO: Falling back to the package description for migration-assistant
Jun 4 14:04:28 INFO: Menu item 'base-installer' selected
Jun 4 14:04:28 apt-install: Unexpected error; skipped processing of: console-setup
Jun 4 14:04:28 base-installer: apt-install or in-target is already running, so you cannot run either of
Jun 4 14:04:28 base-installer: them again until the other instance finishes. You may be able to use
Jun 4 14:04:28 base-installer: 'chroot /target...' instead.

help me please!

thanks,
zappazzi

---

### Post by zappazzi on 2007-06-04
still got errors.


additional info:

im using the latest Wubi-7.04-test3
HD: Seagate. NTFS 
OS: WindowsXP SP2

---

### Post by ago on 2007-06-04
Hmm never seen that before, can it be that the ISO is corrupted, you may want to download it again or try a different Ubuntu desktop

---

### Post by zappazzi on 2007-06-04
try different ubuntu desktop? what do u mean? sorry but im newbie linux user. :(

is ubuntu-7.04-desktop-i386 supported by Wubi test3?

---

### Post by ago on 2007-06-04
> **zappazzi said:**
> try different ubuntu desktop? what do u mean? sorry but im newbie linux user. :(

is ubuntu-7.04-desktop-i386 supported by Wubi test3?

Nope you need to download ubuntu-7.04-alternate-i386.iso ([http://releases.ubuntu.com/7.04/ubuntu-7.04-alternate-i386.iso](http://releases.ubuntu.com/7.04/ubuntu-7.04-alternate-i386.iso) )

Other desktops are Xubuntu / Kubuntu / UbuntuStudio... You need the equivalent ALTERNATE ISO.

Place the ISO in the same folder where you have wubi and select the matching desktop in the settings dialog. You can also have wubi to download the ISO for you but that might be slower.

---

### Post by zappazzi on 2007-06-04
k thanks i will download it again. :)

---

### Post by zappazzi on 2007-06-04
ago,

i tried installing the newly downloaded ubuntu alternate iso(i also check the iso image with md5sum to make sure it is correct.) once again but still got the errors.

Jun 4 21:34:07 main-menu[32406]: INFO: Falling back to the package description for migration-assistant
Jun 4 21:34:08 main-menu[32406]: INFO: Falling back to the package description for console-setup-udeb
Jun 4 21:34:08 main-menu[32406]: INFO: Falling back to the package description for migration-assistant
Jun 4 21:34:08 INFO: Menu item 'base-installer' selected
Jun 4 21:34:08 apt-install: Unexpected error; skipped processing of: console-setup
Jun 4 21:34:08 base-installer: apt-install or in-target is already running, so you cannot run either of
Jun 4 21:34:08 base-installer: them again until the other instance finishes. You may be able to use
Jun 4 21:34:08 base-installer: 'chroot /target...' instead.


here's my setup:
i have 2 harddisks. my Windows OS is in Harddisk(A) and im installing the ubuntu using Wubi in Harddisk(B). is it ok? or will it is necessary to install ubuntu on the same harddisk?


regards,
zappazzi

---

### Post by ago on 2007-06-04
Try A and see if it makes a difference, let it run for a bit. I will double check tonight on my side.

---

### Post by zappazzi on 2007-06-05
> **ago said:**
> Try A and see if it makes a difference, let it run for a bit. I will double check tonight on my side.

hi there ago,

yes i got the same errors. i let it run for 3 hours but still stuck at base system installation. :(


regards,
zappazzi

---

