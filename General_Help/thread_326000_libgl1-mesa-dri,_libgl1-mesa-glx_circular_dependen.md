---
title: "libgl1-mesa-dri, libgl1-mesa-glx circular dependency?"
date: 2006-12-26
forum: General Help
---

### Post by bwobbones on 2006-12-26
Alright, 

  I tried to compile the 2.6.19.1 kernel using this set of instructions:

  [http://ubuntuforums.org/showthread.php?t=157560](http://ubuntuforums.org/showthread.php?t=157560)

  I've got a fairly huge problem though.  I used the apt-get command that was recommended: 

 > sudo apt-get install build-essential bin86 kernel-package libqt3-headers libqt3-mt-dev

  And ubuntu-desktop and xorg were removed!  Now when I try and install, ubuntu-desktop depends on xorg which depends on the libgl1-mesa libraries.  I try and install libgl1-mesa-glx which works, then sudo apt-get install xorg says

  > xorg: Depends: libgl1-mesa-dri but it is not going to be installed

  and when I install libgl1-mesa-dri and try xorg again I get:

  > xorg: Depends: libgl1-mesa-glx but it is not going to be installed

  and so on.  I'm afraid to reboot now in case I can't get the desktop back, can someone help?

---

### Post by bwobbones on 2006-12-26
Don't worry - cleaned up my sources.list and everything worked.

---

