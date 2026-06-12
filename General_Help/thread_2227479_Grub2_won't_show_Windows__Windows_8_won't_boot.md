---
title: "Grub2 won't show Windows / Windows 8 won't boot"
date: 2014-06-02
forum: General Help
---

### Post by toby5 on 2014-06-02
Hi

So my computer has now been like this for a few days now and I can't seem to fix this at all. Here is some backstory:

I installed Lubuntu on my SSD which must have contained the boot file for Windows therefore causing me to overwrite it or something. I have tried many methods to try and fix this but Grub2 won't let me do anything. I can't run Windows Installation disk. I can't find new boot file. I literally am stuck and every reply I have seen just seems far too complicated and over-explained for me. It really is becoming frustrating as there are programmes on Windows I need to use but can't because I am stuck.

tl;dr

Can't boot Windows, boot file missing, simple walkthrough please.

All replies are really appreciated!

Not sure if this helps: [http://paste.ubuntu.com/7552233/](http://paste.ubuntu.com/7552233/)

Thanks!!

---

### Post by toby5 on 2014-06-02
help please

---

### Post by mörgæs on 2014-06-02
Please stop bumping your thread.

---

### Post by oldfred on 2014-06-02
You are missing the BCD in sdb2 and have boot flag on sdb1. 

I would use Boot-Repair to restore a Windows boot loader to sdb, but it may not see the Windows install until you have restored/created a BCD in sdb2. Windows repairs will not work on sdb2 unless you move boot flag to sdb2 first.

So use gparted to move boot flag from sdb1 to sdb2.

Then you can use a Windows repairCD or flash drive to fix the missing BCD. Some third party Windows tools may fix BCD.

       Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)
Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

      
 [http://www.sevenforums.com/tutorials/2676-bcdedit-how-use.html](http://www.sevenforums.com/tutorials/2676-bcdedit-how-use.html)

 Repair BCD
[https://neosmart.net/EasyBCD/](https://neosmart.net/EasyBCD/)

---

