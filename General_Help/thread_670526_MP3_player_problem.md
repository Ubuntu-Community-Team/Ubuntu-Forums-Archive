---
title: "MP3 player problem"
date: 2008-01-17
forum: General Help
---

### Post by NT4.0 on 2008-01-17
I have a Ritmix RF-5200 MP3 player. Its firmware probably has a bug that shows up after a while (changing the mode from Music to Radio or Settings turns off the player). The only solution I found is to reinstall the firmware -- after it everything works fine for some time. Unfortunately, the firmware installer is for Windows only. Under Ubuntu, I formatted the player as FAT32 but it stopped working altogether and does not mount properly. In the Windows firmware installer archive, I found binary files bootmanager.sb, stmpsys.sb, and like that, which look like data to be written on the player. I wonder if I could install the firmware on the player manually, without the Windows installer (perhaps using dd or like that).

---

### Post by Het Irv on 2008-01-17
Have you tried using Wine or a VM to run the installer?

---

### Post by NT4.0 on 2008-01-17
I ran the firmware installer under Wine and it got installed into the Wine Program Files folder. However, running the firmware under Wine was not successful: it said the file bootmanager.sb could not be found, despite it was in the same directory. Inside the executable I found that bootmanager.sb was the boot manager and stmpsys.sb the player firmware. And virtual machines I have cannot see the devices in the USB.

---

### Post by NT4.0 on 2008-01-23
Still have not figured out the way to fix it. Has no one here ever had such a problem?

---

