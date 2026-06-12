---
title: "Partition/Grub problem"
date: 2013-02-28
forum: General Help
---

### Post by kjbox on 2013-02-28
To remove windows7 from my system I followed the instructions in:

[https://help.ubuntu.com/community/HowToRemoveWindows](https://help.ubuntu.com/community/HowToRemoveWindows)

I used Parted Magic for the operation.

All went well until the very last part. Ubuntu was originally installed on an extended partition called sda6 and windows os was on sda1. After deleting the windows partition I made a new partition at the begining of the harddrive (which is an ssd if that makes any difference). As extending an extended partition into unallocated space can't be done, as instructed, I copied the Ubuntu partition and pasted it onto the new partition. I then rebooted into the harddrive and Ubuntu opened as normal. I re-installed grub2 and then re-booted into Parted Magic. I deleted the extended partition containg the original Ubuntu, then created 2 new partions (intending to use them for /home and /data later on). I also created a new swap partition at the end of the drive.

Upon rebooting back to the harddrive I got an error message saying No Such Partition. I eventually figured out that this meant Grub was still pointing to a partition called sda6. I went back to parted magic and added partitions until I had re-created an extended partition called sda6 and copied Ubuntu from the new sda1 back onto the re-created sda6. Rebooting to the harddrive started Ubuntu as per normal (to my great relief!!!!).

So I now have 2 identical Ubuntu12.10 installations, one on sda1 and one on sda6.

How do I get Grub to recognise sda1 instead of sda6?

I assume it requires editing of grub.cfg but I do not want to mess around editing it without knowing precisely what I am doing.

Any help or suggestions greatly appreciated.

---

### Post by fdrake on 2013-02-28
first give us the output of :
```

sudo fdisk -l
sudo blkid

```

---

### Post by kjbox on 2013-02-28
Thanks for the reply. Here are the outputs.

only sda1 and sda6 contain anything sda3,4 and 5 were created just to allow me to recreate sda6

charles@charles-UX31E:~$ sudo fdisk -l
[sudo] password for charles: 

Disk /dev/sda: 256.1 GB, 256060514304 bytes
255 heads, 63 sectors/track, 31130 cylinders, total 500118192 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x13ba8fcf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    52146175    26072064   83  Linux
/dev/sda2       491925504   500117503     4096000   82  Linux swap / Solaris
/dev/sda3        52146990   184072769    65962890   83  Linux
/dev/sda4       184080384   335540223    75729920    5  Extended
/dev/sda5       184082432   238002175    26959872   83  Linux
/dev/sda6       238003038   321685559    41841261   83  Linux

Partition table entries are not in disk order


charles@charles-UX31E:~$ sudo blkid
/dev/sda1: LABEL="Ubuntu" UUID="c7232837-fed0-455d-95e1-70697c8bbfae" TYPE="ext4" 
/dev/sda2: UUID="10623995-048e-4032-996f-97bc6e034583" TYPE="swap" 
/dev/sda3: UUID="afddbfd3-241e-49a7-9984-8050e909e39f" TYPE="ext4" 
/dev/sda5: UUID="4caa0a54-3caf-44bd-80b6-4ead8f2136c5" TYPE="ext4" 
/dev/sda6: LABEL="Ubuntu" UUID="c7232837-fed0-455d-95e1-70697c8bbfae" TYPE="ext4" 
/dev/sr1: LABEL="Maxis Broadband" TYPE="iso9660" 
charles@charles-UX31E:~$

---

### Post by fdrake on 2013-02-28
ok from your description it looks like you need to install/fix grub in partition sda1? if so follow my tutorial:
[http://theguyonthe3rdfloor.wordpress.com/2013/02/28/how-to-install-grub-2/](http://theguyonthe3rdfloor.wordpress.com/2013/02/28/how-to-install-grub-2/)
you will need a ubuntu live cd (I am still working on writing the method without the install cd.)

in your situation the name shoiuld be:
[B]PARTITION= sda1
DISKNAME=sda[/B]

let me know if you encounter any problem.

---

### Post by kjbox on 2013-02-28
Thanks for that. I do not have a live cd at the moment, I will follow your tutorial as soon as I get/make one.

Acouple of things come to mind, since the installation on sda6 is just a copy of the one on sda1 presumably Grub is the same on both and Ubuntu does boot from sda6.

If I unmount sda1 would I not be able to update/install Grub there as if I was working from a live cd?

---

### Post by fdrake on 2013-02-28
> **kjbox said:**
> Thanks for that. I do not have a live cd at the moment, I will follow your tutorial as soon as I get/make one.

Acouple of things come to mind, since the installation on sda6 is just a copy of the one on sda1 presumably Grub is the same on both and Ubuntu does boot from sda6.

If I unmount sda1 would I not be able to update/install Grub there as if I was working from a live cd?
you can run the command i did in the live cd by booting into sda6 and then reboot and update the grub (from sda1 this time). same concept. let me know if works for you.

---

### Post by kjbox on 2013-02-28
Ok done the terminal commands, got 'installation finished no error reported' message.

I will change something on this desktop so that when I reboot I will know that I booted from sda1. Unless, that is, that anything I change here is automatically reflected in the Ubuntu on sda1. Is that the case and if so how can I tell which installation booted?

---

### Post by fdrake on 2013-02-28
> **kjbox said:**
> Ok done the terminal commands, got 'installation finished no error reported' message.

I will change something on this desktop so that when I reboot I will know that I booted from sda1. Unless, that is, that anything I change here is automatically reflected in the Ubuntu on sda1. Is that the case and if so how can I tell which installation booted?

when you reboot an update the grub bootloader, and restart the system on your grub menu you will see 2 linux system with the same kernel name and the same recovery name.the on on top should be the sda1 and the one below the other one.

No the changes you do are indipendent. If you make a change (desktop background for example ) on one , it won't change the other partition.

---

### Post by kjbox on 2013-03-04
Hi,

Sorry for the delay in replying, I have been away.

It did not work, I got an error message :

file '/mnt/new/boot/brub/i386-pc/normd.mod' not found. 

I was unable to boot up atall.

I had to wait a few days before I could get onto the internet with another pc and create a live dvd, I then ran your tutorial and all is fine now.

Thanks for your help.

---

### Post by oldfred on 2013-03-04
> /mnt/new/boot/[COLOR=#ff0000]brub[/COLOR]/i386-pc/normd.mod

Did you use brub or is that just a typo in your post. It should be grub.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by jamesastone2013 on 2013-12-09
Attention if you installed to an external HDD the problem lies with the drive. hdds take a minute to rev up. so you have to stall by entering the advanced settings menu then exiting and select your HDD it will boot into windows or Ubuntu from there depending on your boot priority. no problems so far.

---

