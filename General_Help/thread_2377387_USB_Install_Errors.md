---
title: "USB Install Errors"
date: 2017-11-12
forum: General Help
---

### Post by ozhanaf on 2017-11-12
Hi everyone, 

I am having some major headaches installing ubuntu onto my  desktop. I have done this several times in the past but never run into  issues like this before. 

I am using a live USB to install Ubuntu  onto my system but unfortunately I keep coming across "errno 5  input/output". I've tried many different including adding "noapic apic=off nopmodeset" into the linux line in grub. I have tried using different hard drives (SSD and HDD). But to no avail. 

The only thing that seems off to me during the installation process is that I am consistenly getting the error 
FAT-fs (ssd1): error, invalid acces to FAT (entry 0x4000000000)

and

FAT-fs (ssd1): error, fat_get_cluster invalid cluster chain (i_pos_0)

Does any one have any advice? Please let me know if anyone would like more information, I am more than happy to provide as it is needed.

Thanks!

Ali

---

### Post by VMC on 2017-11-13
How did you install to you USB flash? Try the hybrid method:
First find USB number ```
lsblk
```then use that in assign sd#```
sudo dd if=<whatever>desktop-amd64.iso of=/dev/sd? bs=8M
```

edit:maybe I misunderstood. Did you install to USB correctly and failed to install to HD?

---

### Post by ozhanaf on 2017-11-13
Hey VMC,

Sorry for the late response. I pretty confident that I have installed the USB correctly. In fact I used several different programs to create it (etcher, rufus, live usb creator) but none of them have worked. Installing onto my HD has been the issue.

---

### Post by oldfred on 2017-11-13
What brand/model system?
Is this an UEFI install and the ESP - efi system partition which is FAT32 is the problem?

 dosfstools - dosfsck (aka fsck.msdos and fsck.vfat) utilities
Must be unmounted
sudo dosfsck -t -a -w /dev/sda1
The -a seems to help in clearing dirty bit
[https://bbs.archlinux.org/viewtopic.php?id=164185](https://bbs.archlinux.org/viewtopic.php?id=164185)

---

### Post by ozhanaf on 2017-11-13
Hey oldfred!

My mother board is an ASUS Z170A, this is an UEFI install. Just to be clear you suggest running "sudo dosfsck -t -a -w /dev/sda1" in the command line where I am given the option to "Try Ubuntu"?

---

### Post by oldfred on 2017-11-13
Yes, use live mode before installing.

With my Asus X97 I changed a lot of UEFI settings, some required, some optional. Your Z170 probably is very similar.
 Asus Z97 Motherboard Change UEFI from Windows (secure boot only) to other OS
[http://ubuntuforums.org/showthread.php?t=2298896](http://ubuntuforums.org/showthread.php?t=2298896)
Asus z97 screenshots:
[http://ubuntuforums.org/showthread.php?t=2258575&page=297](http://ubuntuforums.org/showthread.php?t=2258575&page=297)
Minor problems with using an ASUS Z97-A Motherboard
[http://askubuntu.com/questions/503168/minor-problems-with-using-an-asus-z97-a-motherboard](http://askubuntu.com/questions/503168/minor-problems-with-using-an-asus-z97-a-motherboard)
[http://askubuntu.com/questions/554735/good-z97-motherboard-for-ubuntu](http://askubuntu.com/questions/554735/good-z97-motherboard-for-ubuntu) 

My Gigabyte Z170 only required a few settings & I did not make a good list as it was only a couple, I think?
But I review list from my Z97 to make sure I have things reset ok.

---

