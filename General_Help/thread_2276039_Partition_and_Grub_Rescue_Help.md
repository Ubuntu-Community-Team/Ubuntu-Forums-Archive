---
title: "Partition and Grub Rescue Help"
date: 2015-04-29
forum: General Help
---

### Post by Jesse_Gooding on 2015-04-29
Hi all,

I've searched a lot on grub rescue and haven't found anything that has worked for me.

I decided to try to set up a dual boot with Ubuntu on a PC that had Windows 7.


During Ubuntu 14.04 installation I shrunk my windows partition.


Every time I would boot after the installation finished it would take me straight into Ubuntu.


I ran Boot Repair (link below) and rebooted, but at the grub menu Ubuntu was my only option. 
[http://paste.ubuntu.com/10918852/](http://paste.ubuntu.com/10918852/)

I thought I might have selected the wrong type for my windows partition, so in the Volumes section of the "Disk" menu I selected edit partition and changed the type to HPFS/NTFS (0x07). probably shouldn't have done this.


Next reboot I met with grub rescue. I have a flash drive with Ubuntu
I'm able to try Ubuntu without installing.


Before I changed the partition type I had 4 partitions showing in "volumes"
A Swap Partition, windows partition, Ubuntu partition, and a free space partition
Now I have the swap partition and free space, but just one "Linux (bootable)" type partition in /dev/sda2


I guess my first step would be figure out how to fix grub rescue.
Then I'd like to figure out how fix my partitions, because I'd like to keep windows 7.


If I have to lose Windows that's not the worst thing in the world, I'm just as interested in understanding this problem as I am in fixing it. I'll admit I have a very limited idea of what is going on, but you can probably tell that if you've read this far.


Before I go looking into how to clean out my hard drive and just reinstall Ubuntu I thought I'd see if anyone could help. Thanks for reading.

---

### Post by oldfred on 2015-04-30
Best to post the link that the Summary Report from Boot-Repair gives you.

       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

   Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Jesse_Gooding on 2015-04-30
Ah yeah I forgot to put up the link. It's in the original post now.

---

### Post by TheFadedBrit on 2015-04-30
It seems to me that you may have corrupted your windows install via the ubuntu one this has happend to me many times and i have just had to reinstall windows and then Linux after that.

There may be another way but thats the only way ive got windows back but you loose your previous files.

Hope this helps.

Faded

---

### Post by oldfred on 2015-04-30
Windows has to boot from a primary partition, and the only primary partitions you have are swap and the extended?

Always best to shrink Windows with Windows own disk tools and reboot immediately as it has to run chkdsk to fix itself to its new size.

---

### Post by Jesse_Gooding on 2015-05-01
Thanks for the info everyone. I think I'll try to format my hard drive and re-install Ubuntu and just worry about getting windows onto the PC later. Still have a laptop with windows for now. Hopefully I have better luck next time.

---

### Post by sammiev on 2015-05-01
Hi and welcome Jesse,
It's usually a little easier to install Windows first then Ubuntu.
You can also install and run Windows from a VM inside of Ubuntu.

---

