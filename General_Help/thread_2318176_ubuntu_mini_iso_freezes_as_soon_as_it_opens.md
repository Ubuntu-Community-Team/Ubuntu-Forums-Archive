---
title: "ubuntu mini iso freezes as soon as it opens"
date: 2016-03-23
forum: General Help
---

### Post by jesse49 on 2016-03-23
So recently I have been having issues trying to boot from usb because of grub, so i decided to use the mini ubuntu iso with a disc i had laying around, the disc worked on my laptop after testing it, but when i use my desktop im able to boot i get to where i can choose how to install and i just hit install and then my keyboard doesnt work anymore, so I am assuming that it is freezing, because the keyboard works in bios and before going into the install, but as soon as it asks me to select my language it stops

used brasero to burn the iso

---

### Post by mastablasta on 2016-03-24
1. does md5sum checks OK?
2. is the desktop system UEFI?
3. can you drop to anoter TTY (crtl+alt+f2 for example) when it looks like it is freezing? 
4. what happens if you wait for some time?

---

### Post by Uinthe on 2016-03-24
After choosing Install just press space 1 time per second untill the next menu appears. After installing add this in /etc/boot/grub GRUB_CMDLINE_LINUX_DEFAULT
```
i8042.nomux i8042.reset=1
```

---

### Post by sudodus on 2016-03-24
The Ubuntu mini.iso file does not work in UEFI mode, but you can do (almost) the same things with the Ubuntu Server 64-bit iso file and it works in UEFI mode, (if the text mode graphics works).

Which version are you trying to use? Some versions, that are linked in Ubuntu wiki and help pages do not work. See this link to find working versions:

[***mini.iso***, minimal install, netboot iso]("http://ubuntuforums.org/showthread.php?t=2230389&p=13211730#post13211730")

---

