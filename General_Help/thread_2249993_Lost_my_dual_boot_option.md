---
title: "Lost my dual boot option"
date: 2014-10-26
forum: General Help
---

### Post by NotWindows on 2014-10-26
Hey guys!

I lost my dual boot screen kinda by accident. I was running win xp and I installed windows 7 for some business apps and now can't get the dual boot option to get to Ubuntu. What can I do to get my dual boot option back?

Thanks,
NotWindows/Kevin

---

### Post by cariboo on 2014-10-26
Moved to General Help.

---

### Post by NotWindows on 2014-10-26
Hey Guys!

I lost my dual boot option after upgrading win xp to win 7 to run some business software. What can I do to get my dual boot option screen back?

Thanks,
Kevin

---

### Post by QIII on 2014-10-26
And merged.

Please do not start duplicate threads.

---

### Post by NotWindows on 2014-10-26
Accident

---

### Post by yancek on 2014-10-26
It's not an accident it is expected behavior with windows.  It always overwrites the master boot record and doesn't ask or inform you that it is being done.  If I understand correctly, you replaced your xp with windows 7 installing windows 7 to the same partition(s) on which you previously had xp, is that right?  Use your Ubuntu medium (or any other Linux system CD/DVD) and boot it.  When booted, open a terminal and run this command:  sudo fdisk -l(Lower Case Letter L in the command) which will show partition information and we will be able to see if your Ubuntu is still there.  If it is, you should be able to re-install Grub to boot Ubuntu and windows 7.

---

### Post by NotWindows on 2014-10-26
Yes you are correct on what happened!

If the Ubuntu install is still there what process do I need to do with grub to get the boot back?

Thanks for the reply!
Kevin

---

### Post by Mark Phelps on 2014-10-26
> what process do I need to do with grub to get the boot back?

First thing you need to do is follow the instructions that yancek provided you in post #6: > When booted, open a terminal and run this command: sudo fdisk -l(Lower Case Letter L in the command) which will show partition information

---

### Post by yancek on 2014-10-26
If you have some Linux partitions, go to the site below which explains re-installing Grub2 in various situations.  Particular interest to Section 2.2.  Or post the fdisk output here and someone will suggest an appropriate method.

[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

---

### Post by NotWindows on 2014-10-29
Can't find the terminal in Windows 7

---

### Post by QIII on 2014-10-29
You should not be looking for the terminal in Win 7.

Please read the post again.

---

### Post by NotWindows on 2014-10-29
My mistake! Got it! Just gettig back to this afterdays of being away from it!

---

### Post by NotWindows on 2014-10-29
Ok this is what  I have and assuming that my Liniux partition is still there.


  	 	 	 	   Device Boot      Start         End      Blocks   Id  System
 /dev/sda1   *          63   244188031   122093984+   7  HPFS/NTFS/exFAT
 /dev/sda2       244189182   488396799   122103809    5  Extended
 /dev/sda5       244189184   484206591   120008704   83  Linux
 /dev/sda6       484208640   488396799     2094080   82  Linux swap / Solaris

---

### Post by oldfred on 2014-10-29
#6 in those instructions posted on repair from a LiveCd are what you need.
You have to mount your install on sda5 and then install grub to sda.

> grub-install will restore missing files in the *grub*  folder but will not restore intentionally deleted or corrupted files.  To accomplish these tasks GRUB 2 must be completely removed and  reinstalled. 

sudo mount /dev/sdXY /mnt # Example: sudo mount /dev/sda5 /mnt
sudo grub-install --boot-directory=/mnt/boot /dev/sdX # Example: sudo grub-install --boot-directory=/mnt/boot /dev/sda

---

### Post by NotWindows on 2014-10-29
OldFred, Do I use your examples for my partitions?

---

### Post by yancek on 2014-10-29
> OldFred, Do I use your examples for my partitions? 		

That should work since your Ubuntu is on sda5.  If you need more detail check the link from my earlier post # 9.

---

### Post by NotWindows on 2014-10-30
That fixed my boot option!

Thank you all very much

---

