---
title: "Cannot burn iso to USB in Saucy"
date: 2013-10-29
forum: General Help
---

### Post by shane-animail on 2013-10-29
Wanted to give the latest ubuntu Gnome and Kubuntu a try, tried both Startup Disk Creator and uNetbootin.

Disk creator goes along til up to the point I would expect the password prompt to install but then just closes and trying to run from USB just takes me to the already installed grub menu.
uNetbootin completes the process but when I try to boot it it takes me to a command prompt.

I eventually had to use uNetbootin in Windows, which worked perfectly.

---

### Post by ptn107 on 2013-10-29
I just installed unetbootin_575-1ubuntu2 in Ubuntu 13.10 and wrote ubuntu-13.10-desktop-amd64.iso to a 64gb ext2 formatted usb drive sucessfully.  What version of ubuntu/unetbootin did you use?

---

### Post by sudodus on 2013-10-29
***Cloning with dd*** has a high success rate to make boot USB drives, provided you write to the correct drive. Otherwise you might wipe valuable data. But there are tools to help you write to the correct drive, for example the shell-script ***mkusb***. See this link [Howto make USB boot drives]("http://ubuntuforums.org/showthread.php?t=1958073")

---

### Post by Baldrick_NZ on 2013-10-30
Call me old-fashioned, but nothing beats burning Ubuntu to a DVD. 

The startup disk creator hasn't worked well for a long time, and unetbootin seems to be hit-and-miss. I hardly get any failure from a dvd. Maybe it's just operator error with USBs, but I definately get a better hit DVD hit rate.

---

### Post by shane-animail on 2013-10-30
I have always used the creator for ubuntu based distros and unetbootin for other distros and don't remember ever having an issue with them in the past (expect those hybrid ones like opensuse or mandriva, forget which).

I'm on my chromebook at moment so can't check app versions but software creator is the one in the default install and unetbootin installed from the regular saucy repos.

---

### Post by sudodus on 2013-10-30
You can read about current problems with usb-creator-gtk in 13.04 and 13.10 in this link

[https://help.ubuntu.com/community/Installation/FromUSBStick#Install_and_run_usb-creator](https://help.ubuntu.com/community/Installation/FromUSBStick#Install_and_run_usb-creator)

---

