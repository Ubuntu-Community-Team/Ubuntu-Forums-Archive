---
title: "Installing Ubuntu"
date: 2013-01-25
forum: General Help
---

### Post by northwestern on 2013-01-25
I have been having very little success trying to get an external USB 3 external drive ( Ubuntu installed) to work on my Windows 8 laptop (UEFI).When I get the external drive working directly after installation it works perfectly, allowing me to update and re-boot back into Ubuntu. However when I try and reboot back into Windows 8 I get a black screen with a message about grub 2 this means I have to recover my laptop back to factory settings, after this the external drive with Ubuntu fails to boot. This has happened three times and I am beginning to get a little bit mad.
At the moment I have a USB pen drive with the Ubuntu 12.10 Iso, I can load this to try Ubuntu by going through the Windows other OS mode. When I do this and then plug in the external drive I can open up the files of the external drive.
Is it possible to use the Ubuntu on the pen drive to fix the boot on the external drive?, as this is the only way I can open the files.


Regards.
Northwestern

---

### Post by tgalati4 on 2013-01-25
You probably have multiple USB ports on your machine.  Choose the one with USB2.0 interface.  Then report back.

---

### Post by northwestern on 2013-01-25
Thanks for reply.
I put the pen drive containing Ubuntu ISO in one of the USB port, I then boot into window 8. By going into the "change PC settings" menu, and then pressing the "USB EFI pen drive" option the laptop reboots into the Ubuntu start screen. After choosing "try Ubuntu" it continues to boot.
I then plug in the external drive into another USB 3 port, after a few seconds the drive appears on the screen.
Is it possible to repair the boot of the external hard drive by using the "try Ubuntu" running from the pen drive?.
Regards
Northwestern

---

### Post by tgalati4 on 2013-01-25
Yes, of course.  If it boots into Ubuntu and you open a terminal:

```
sudo fdisk -l
sudo update-grub
```

Write down your disk drive assignments from the fdisk command.  You will need them later.

---

### Post by northwestern on 2013-01-26
Thanks for reply.
When I open the terminal and type in the following:
a) sudo fdisk -l
b) sudo update-grub
I get the following messages
These do not mean much to me, perhaps you can explain what I need to do.
When I boot up my lap top with the pendrive ISO my computer boots into window 8, then I have to change settings mode to boot Ubuntu.
 
If I try and boot up with my external drive I get the message "preparing automatic repair".
Hope this helps.
Regard
Northwestern

---

### Post by oldfred on 2013-01-26
If terminal output just copy & paste into your message. If long use code tags, by highlighting like a copy & click on # in edit panel above message.

May be best to see all the details of your install.
       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

    
Should not matter if internal or externel.
       UEFI dual boot two drives - HP
[http://ubuntuforums.org/showthread.php?t=2072950](http://ubuntuforums.org/showthread.php?t=2072950)
UEFI dual boot two drives see #14 on how edit UUID to Windows efi partiton
[http://ubuntuforums.org/showthread.php?t=2031836](http://ubuntuforums.org/showthread.php?t=2031836)

---

