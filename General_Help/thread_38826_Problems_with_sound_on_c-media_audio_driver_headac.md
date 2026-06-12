---
title: "Problems with sound on c-media audio driver *headache*"
date: 2005-06-02
forum: General Help
---

### Post by Bandit@Linux on 2005-06-02
I'm having problems having sound in ubuntu it absolutely doesn't work, I have a c-media audio driver sound card, ubuntu has detected it but it doesn't seem to work, I've downloaded the audio driver file for it from here
URL:
[http://downloads.vnunet.com/download/driver/c-media+cmi8738+audio+driver+linux/_33677.html](http://downloads.vnunet.com/download/driver/c-media+cmi8738+audio+driver+linux/_33677.html)

It says to 
1. Backup the Config.in and Makefile in the sound driver directory
     (/usr/src/linux/driver/sound).

  2. Extract the tar file by 'tar xvzf cmpci-xx.tar.gz' in the above
     directory.

  3. Change directory to /usr/src/linux

  4. Config cm8338 driver by 'make menuconfig', 'make config' or
     'make xconfig' command.

  5. Please select Sound Card (CONFIG_SOUND=m) support and CMPCI
     driver (CONFIG_SOUND_CMPCI=m) as modules. Resident mode not tested.
     For driver option, please refer 'DRIVER PARAMETER'

  6. Compile the kernel if necessary.

  7. Compile the modules by 'make modules'.

  8. Install the modules by 'make modules_install'

It absolutely makes no sense to me, because my ubuntu system has no folder with /usr/src/linux to even "make menuconfig"  ](*,) plz help

---

