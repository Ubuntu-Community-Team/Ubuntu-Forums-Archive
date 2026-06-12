---
title: "Sony PSP Help Me"
date: 2007-08-08
forum: General Help
---

### Post by draikxox on 2007-08-08
**_[COLOR="Blue"]Still looking for an answer that will work anyone know whats goin on. [/COLOR]_**


i cant get my comp to recognise my psp. if someone knows how to make it seen it would be great
i plug it into any of the usb ports an dthe psp recognises that there has been a connection made but lsusb doesnt even see the psp. nothing pops up or anything there is no reaction from my comp someone help me please.

---

### Post by benanzo on 2007-08-08
Go to **System -> Preferences -> Removable Drives and Media** and make sure that **Mount removable drives when hotplugged** is enabled.  It should mount it in **/media/usbdisk**.

---

### Post by draikxox on 2007-08-08
i have already tried that it still does not work

---

### Post by Nathan Otis on 2007-08-25
I gotta bump this one... I have checked System/Admin/Users & Groups. Everything there is marked correctly. I have checked System/ Prefs/ Removable drives and media and all settings are ok there as well.

When I start USB Mode on my PSP, Nothing happens.

When I go to Places/Computer, I can see the drive but it won't let me do anything... If I try to mount it through the prefs, I get the following message in Ubunut:

"Unable to mount the selected volume. The volume is probably in a format that cannot be mounted."

       mount: wrong fs type, bad option, bad superblock on /dev/sda1,

       missing codepage or other error

       in some cases useful info is found in syslog - try

       dmesg | tail  or so



error: could not execute pmount

What am I doing wrong?

Fixing this may take a while ... Thanks in advance for anyone who is willing to to stick this out to the end.

---

### Post by Nathan Otis on 2007-08-26
I've started a new thread with ALL the info I have so far. Please take a look:

[Sony PSP on Dapper (Won't Mount)]("http://ubuntuforums.org/showthread.php?p=3256456#post3256456")

Thank you.

---

