---
title: "New to dual booting"
date: 2014-05-14
forum: General Help
---

### Post by maazmahmood on 2014-05-14
I have a Windows 8 desktop machine, and would like to dual boot into Ubuntu. I want that Ubuntu to be on a physically separate drive, I don't want any Windows files on it, and I don't want any Ubuntu files in any other hard drive. Is this possible? If so how can I do it?

---

### Post by kc1di on 2014-05-14
Yes it's possible [here is a page]("http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot") that may be of help to you.

You should also read some material on dual booting with UEFI machines. 

this is a[ good source]("http://ubuntuforums.org/showthread.php?t=2147295")

---

### Post by maazmahmood on 2014-05-14
So from the first link you provided that will automatically know to keep all Ubuntu files in the Ubuntu physical drive?

---

### Post by grahammechanical on 2014-05-14
> **maazmahmood said:**
> So from the first link you provided that will automatically know to keep all Ubuntu files in the Ubuntu physical drive?

Yes. Just make sure that the bootloader is being installed onto the drive where Ubuntu is being installed. The installer defaults to sda. So, if you are putting Ubuntu on to sdb look for the panel and use the drop-down menu to select sdb as the location of the bootloader.

This has a benefit. You can use the BIOS/UEFI to select which drive has boot priority. If you select the Windows drive then windows will boot. But if you give the Ubuntu drive boot priority then you will get a boot menu offering either Ubuntu or Windows. It also means that updating Windows will not in some way break the Ubuntu bootloader as sometimes happens.

Regards.

---

### Post by Mark Phelps on 2014-05-14
When installing with multiple drives, the safest approach is to have all drives but the target drive disconnected.  That prevents accidentally installing the boot loader to the wrong drive.

---

### Post by maazmahmood on 2014-05-14
Ok I had another idea I have this case (Link provided). and on top is a SATA connector, along with a sata power connector, so theoretically I could cable an Internal Hard drive. My question is that I could install Ubuntu on that then set that as highest priority and when I wanted to boot to Ubuntu I just plug that in, what do you guys think?

---

### Post by oldfred on 2014-05-14
No need to change physical connections, except perhaps during install to make absolutely sure you do not have any parts of Ubuntu on Windows drive.

Ubuntu will let you boot Windows from grub menu if installed in the same boot mode UEFI or BIOS as Windows. UEFI & BIOS are not really compatible and once you start booting in one mode you cannot switch. Or from grub menu you cannot boot another install in different boot mode.

---

### Post by maazmahmood on 2014-05-15
These steps are clear however I'm curious as to why he created 2 partitions? Is that necessary? 
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)

---

### Post by oldfred on 2014-05-15
Default install is / (root) and swap. 
Many also like a separate /home or data partition(s). I have a shared NTFS data partition and Linux data partition.

If a full drive install / may be very large and it is a bit more efficient to have a smaller / of 20 or 25GB and additional partitions.

If  two drives, you may want to backup Windows vital data to Ubuntu drive and would then need a NTFS partition. And you could backup Linux data to the Windows drive but it would be better to have a Linux formatted partition.
Best not to write into Windows system partitions. You still need to have Windows 8 fast startup or always hibernation turned off if dual booting.

---

### Post by kc1di on 2014-05-15
He had a swap partition,  if your installing on a laptop and want it to hibernate or suspend you most likely need a swap area.  rule of thumb has always been create a swap 2x your installed ram. 
I also like to make a seperate partition for my /home directory. so it would look like this.
/ (root)
/swap 
/home.

---

### Post by maazmahmood on 2014-05-15
If I'm installing on just my desktop, but would still like to put it on hibernate/sleep should I put in the swap partition as well?

---

### Post by LastDino on 2014-05-16
> **maazmahmood said:**
> If I'm installing on just my desktop, but would still like to put it on hibernate/sleep should I put in the swap partition as well?


Yes. How much RAM do you've? 

Note:Generally hibernation is not recommended but w/e sails your ship.

---

