---
title: "Burg on wrong disk"
date: 2015-02-11
forum: General Help
---

### Post by nalkubaxd5 on 2015-02-11
I have installed burg to wrong disk (/sda not to /sdb). Can anyone help me with reconfigurating or reinstalling this? When computer boots i can see GRUB2.

> 
sudo burg-emu
[IMG]http://i.imgur.com/Nzl70eJ.png[/IMG]

> 
sudo fdisk -l
[IMG]http://i.imgur.com/HgBLZ8S.png[/IMG]

---

### Post by yancek on 2015-02-11
You have two drives with four windows partition and one Linux.  Ubuntu is the Linux?  Which version of windows are you using and how is it installed?  What can you boot, windows, Ubuntu, both, neither?  You might download the boot repair and either run it from Ubuntu if it boots or put it on a CD and boot from it, just select the option to Create Bootinfo Summary and post the results here.

---

### Post by nalkubaxd5 on 2015-02-12
I'm using Ubuntu 14.04 and Windows 10 (I don't have UEFI). I can boot both of the systems. GRUB 2 is working fine.

Boot Info: [http://paste.ubuntu.com/10189250/](http://paste.ubuntu.com/10189250/)

/sda - disk 1 - only data for windows
/sda1 - "reserved by the system" - flagged as boot (how!? Windows plz?) - ntfs
/sda2 - data storage - ntfs

/sdb - disk 2 - Windows and Ubuntu
/sdb1 - Windows 10 partition - ntfs 
/sdb2 - data storage 2 -ntfs
/sdb3 - Ubuntu 14.04 partition - ext4

Do you want screenshots from GParted?

---

### Post by oldfred on 2015-02-12
I do not know nor recommend burg as it does not seem like it has been updated for ages.

But it looks like you installed Windows to sdb, but had sda as default boot drive in BIOS. Then Windows installs its (hidden) 100MB boot partition to the BIOS boot drive or sda in you case. Better to have Windows boot partition and Windows in MBR of Windows drive.

And with two drives then better to have Linux on other drive with grub in MBR of that drive. 
Then each drive can boot its system without the other. As you now have it configured, both drives have to work just to boot Windows.

---

### Post by nalkubaxd5 on 2015-02-12
Refresh?

---

