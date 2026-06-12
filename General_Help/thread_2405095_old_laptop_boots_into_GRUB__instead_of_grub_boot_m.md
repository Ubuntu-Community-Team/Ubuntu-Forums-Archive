---
title: "old laptop boots into GRUB_ instead of grub boot menu &amp; render keyboard inoperable"
date: 2018-11-01
forum: General Help
---

### Post by bijaydeyp on 2018-11-01
I have an old BIOS/MBR multi-booted system. 
 I was trying to install another linux os. Grub-2 of Ubuntu 14.04 was preinstalled on MBR as a primary bootloader. therefore, I  installed new os's bootloader on  saperate /boot partition, not touching the MBR. After installation when I reboot the system, boot-screen appears with GRUB(uppercase) followed by a blinking underscore i.e. **GRUB_  **which is unlike the typical GNU grub prompt i.e. **grub> ** or grub boot menu. the keyboard is also not working on it. Alt + Ctrl + Del not working. Only force power off.

 I have checked with a ubuntu live os. there, it is functioning as normal. Ubuntu's UUIDs of  root & swap partitions are intact as before occurring this problems. I can change my BIOS-setup options which indicates the keyboard is ok. I am not sure whether it is a hardware or software or firmware issue.

 Please, tell me how do I solve it ???

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
submitted at 06:07 AM
Some additional info..

I noticed shutdown or reboot not possible. system goes for shutdown or reboot, but then the display does not turn off. it shows a message
" Please remove installation media and close the tray (if any) then press ENTER" .

---

### Post by ajgreeny on 2018-11-01
Probably best to see all the details.

Go to **Boot-Repair** in my signature below and follow the instructions there to run the Boot-Info-Script.	 

**Do not run the default repair just yet** but simply copy back here the pastebin link you get which will show us a lot more about your system.

---

### Post by bijaydeyp on 2018-11-02
@[**[COLOR=#C61919][B]ajgreeny**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=27747") thanks for  your quick reply.
 I did as you said. I run the boot-repair for bootinfo summary. pastebin link here..
[http://paste.ubuntu.com/p/zzw3rrHdyb/[IMG]https://i.postimg.cc/t4zStkpG/IMG-20181101-191549.jpg[/IMG]]("http://paste.ubuntu.com/p/zzw3rrHdyb/")

---

### Post by yancek on 2018-11-02
Your boot repair output shows that you have syslinux bootloader installed to the MBR of your primary hard drive.  I think part of the problem is that you have a separate boot partition for Opensuse (sda10) and the system partition is on sda11.  If you look at the info in boot repair on sda10, you see conflicting information regarding core.img and different versions of Grub.  Opensuse also uses grub2 as its grub directory name whereas Ubuntu uses grub.

If you scroll about half way down the boot repair page, you will see the grub.cfg file entries which point to your Opensuse install on sda11 as well as the windows 7 and Ubuntu partitions so you know they were detected.  Do you still have Debian on sda8 as it does not show in the Opensuse grub.cfg file?

Given this information, I would suggest that you re-install Opensuse and this time install Grub to the MBR as it does detect your windows and Ubuntu.  If you want Ubuntu as the primary system, you can boot it from the Opensuse menu and then install Grub to the MBR from Ubuntu once booted.  I would also suggest NOT creating a separate boot partition.  Another option would be to boot the Ubuntu 14.04 install device if you still have it and install Grub to the MBR pointing to the Ubuntu partition.

I'm not sure how you got syslinux code in the MBR of all your drives or why you see GRUB on boot but that is obviously a big part of the problem.

---

### Post by bijaydeyp on 2018-11-02
@[**[COLOR=#000000]yancek[/COLOR]**]("https://ubuntuforums.org/member.php?u=1928724") Thanks a lot for analyzing the problem.

> Do you still have Debian on sda8 as it does not show in the Opensuse grub.cfg file? 						
yes. I still have sda8 for Debian_boot & sda9 for Debian_root.
 
Right now, I only have Ubuntu live-usb. I am posting here using it.
so, according to you how should I proceed for a safe recovery / restore i.e. by not hurting other partitions ??
considering that, I want to set up Ubuntu's grub as primary bootloader.

Any recommended tutorial / wiki / community help page ??

---

### Post by yancek on 2018-11-02
Probably the best resource is the Ubuntu wiki at the link below under Fixing a Broken System.  Read the various options available before beginning.

[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

---

