---
title: "accidentally overwritten the mbr...."
date: 2008-06-25
forum: General Help
---

### Post by Mia_tech on 2008-06-25
I have a laptop with windows xp and ubuntu, while I was installing slax to my usb drive, I ran the install script from the hard drive partition over writing the mbr...now I don't want to reboot my computer, afraid to loose all my data and apps...data is not a big deal as I can backup and restore, is all the apps that I have installed in xp and ubuntu. Creating an image don't think is an option in this case as it will be creating it with the bad mbr...could someone suggest me what is the best course of action in my case?...could the mbr be restore or repair?...I believe that systemrescuecd has an utility for repairing and analyzing the mbr, I will give that a try meanwhile...hope I don't have to wipe my pc 

thanks in advance

---

### Post by attari on 2008-06-25
> **Mia_tech said:**
> I have a laptop with windows xp and ubuntu, while I was installing slax to my usb drive, I ran the install script from the hard drive partition over writing the mbr...now I don't want to reboot my computer, afraid to loose all my data and apps...data is not a big deal as I can backup and restore, is all the apps that I have installed in xp and ubuntu. Creating an image don't think is an option in this case as it will be creating it with the bad mbr...could someone suggest me what is the best course of action in my case?...could the mbr be restore or repair?...I believe that systemrescuecd has an utility for repairing and analyzing the mbr, I will give that a try meanwhile...hope I don't have to wipe my pc 

thanks in advance

Hmmm... The process is smooth as silk... Just do as instructed. I have personally tried restoring MBR after I reinstalled XP on another partition, but did not want to reinstall 7.10 Ubuntu so I followed the method stated below.

But first you will have to restore XP boot sequence. I suggest you insert XP installation CD and boot from it. Go to the repair option and choose to repair the installed XP. Now hopefully you will be able to boot from XP on your Harddisk. 

Next insert Live CD of Ubuntu 7.10 (or whatever distro release you use) and boot from it. Open root terminal in Live CD.

type: **sudo grub**
then press <enter>

Then type: **find /boot/grub/stage1**
then press <enter>

Note the output. In my case it was (hd0,2). 

Then type: **root (**
then press <tab> it will complete the first part **hd0,**
then type: **2)** (Or whatever is applicable for you)
then press <enter>


Also then type: **setup (hd0)**
then press <tab> 

Finally type: **quit**
then press <tab> 


Now you will be able to boot from your installed ubuntu partition.

---

