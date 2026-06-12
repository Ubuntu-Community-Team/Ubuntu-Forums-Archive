---
title: "Menu to choose OS (probably GRUB) not showing after upgrading to windows8"
date: 2013-06-24
forum: General Help
---

### Post by dentrite7 on 2013-06-24
I am a not-so-techie business person in a very big trouble. I used Ubuntu 12.04 to store all my confidential and financial data and windows7 for general purpose. It worked perfectly fine. When I would turn my computer on, it used to show a menu to choose what to load. Now, I updated from windows 7 to windows 8 by a CD. The problem I am facing now is that windows 8 starts automatically without letting me choose between windows 8 and Ubuntu. I can't access the ubuntu drive (and my data) from windows because it is ext4. Please help me to get back ubuntu as i love it. or atlease to get my data back otherwise I'm dead. My boss will kill me.. I have already made loss of millions due to this start screen. I cant let my employers get hands on my laptop so please help me,...it is urgent.

---

### Post by sanderj on 2013-06-24
Windows install will overwrite GRUB.

Workaround: Get a Ubuntu CD, live-boot it, start the file browser Nautilus, and browse to your harddisk: you should see all your files.

---

### Post by cruz12141214 on 2013-06-24
just make sure that you do a cold boot after booting windows or it will keep booting windows

---

### Post by Impavidus on 2013-06-24
After you made backups of your files you can use [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair") to restore your bootloader and use your dual boot again.

---

### Post by oldfred on 2013-06-24
I also recommend Boot-Repair. You also need a Windows repairCD or flash drive as you need a repair flash drive for every system you have installed.

 WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)

---

