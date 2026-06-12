---
title: "black screen blinking white underscore after grub menu"
date: 2014-12-29
forum: General Help
---

### Post by Quintyn on 2014-12-29
so as the title says i installed ubuntu on my dell optiplex 780 with a clean install the install took a bit then at the end asked to reboot so i did so now all it does is load up the grub menu i select ubuntu and it goes straigh to a black screen with blinking under score ( i apoligize for my english) im very new to ubuntu but i did a lost of looking around before posting i tryed pressing e in the grub menu and changing the splash blah blah to nomo whatever that did nothing  im stuck and i have no idea what to do please help thank you

---

### Post by agillator on 2014-12-30
How long have you waited for the boot to finish? An unaltered installation of Ubuntu will go to a blank screen with a flashing cursor and remain there while it boots. This takes however long it takes, but it can seem like forever. So, boot you system and be patient to see what it does. If it boots you all is ok.

To prevent the blank screen you need to change a line in the file /etc/default/grub. Remove "quiet" from the line reading CMDLINE_LINUX_DEFAULT="quiet splash". You can do this with a text editor after a normal boot, or you can boot from the live/install disk, mount your root partition, and use the text editor then. This will allow messages to be displayed during the boot process. This assures you it is proceeding normally (a few steps need some seconds to complete, so patience is necessary) and, should it hang, can give you some idea of the problem or at least where to look.

---

