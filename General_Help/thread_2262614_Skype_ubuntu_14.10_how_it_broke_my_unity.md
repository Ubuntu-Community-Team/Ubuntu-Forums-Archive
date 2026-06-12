---
title: "Skype ubuntu 14.10 how it broke my unity"
date: 2015-01-26
forum: General Help
---

### Post by cybuss on 2015-01-26
Alright i installed skype tried to download from their webpage did not work
so i enabled the Canonical Partners source

did apt-get install skype

every went as normal for installation. then i tryed to launch. again no avail. it just started to blink, then nothing
so i launched skype with the terminal

skype: error while loading shared libraries: libGL.so.1: wrong ELF class: ELFCLASS64

did a bit of research. someone recommended running

sudo apt-get install --reinstall libgl1-mesa-glx:i386

so i ran it

everything worked fine. skype started and worked. i was listening to music downloading steam stuff.
then boom unity crashed. i tryed restarting the computer reinstalling unity and ubuntu desktop. nothing worked
so i reinstalled the nvidia driver from the shell. it works again but now skype is still complaining about the shared libraries

so does anyone have an idea on how to fix this?
just to clear up some information
this install is relatively fresh it is dual booted alongside windows. ubuntu installed using standard settings alongside windows, i have not tinkered with anything but installing the binary driver,

---

### Post by phidia on 2015-01-26
Have you used [this guide]("https://help.ubuntu.com/community/Skype") for skype?

---

### Post by mc4man on 2015-01-26
You could take a look here, 2nd answer seems better (wrapper script
[http://askubuntu.com/questions/519470/skype-4-3-0-37-stopped-working-after-installation-of-nvidia-340-32-drivers](http://askubuntu.com/questions/519470/skype-4-3-0-37-stopped-working-after-installation-of-nvidia-340-32-drivers)

---

### Post by cybuss on 2015-01-28
Unfortunately neither of your recommendations worked, 

ERROR: ld.so: object '/usr/lib/i386-linux-gnu/mesa/libGL.so.1' from LD_PRELOAD cannot be preloaded (cannot open shared object file): ignored.
/usr/bin/skype: error while loading shared libraries: libGL.so.1: wrong ELF class: ELFCLASS64

---

