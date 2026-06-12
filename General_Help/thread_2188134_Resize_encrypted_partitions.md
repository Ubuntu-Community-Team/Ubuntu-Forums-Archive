---
title: "Resize encrypted partitions"
date: 2013-11-15
forum: General Help
---

### Post by noorez on 2013-11-15
I have read most of this guide but would still like a bit of help:

[https://help.ubuntu.com/community/ResizeEncryptedPartitions](https://help.ubuntu.com/community/ResizeEncryptedPartitions)

Here is what I have:

/dev/sda
 --/dev/sda1 2.00 MiB bios_grub
  --/dev/sda2 200 MiB boot
  -- /dev/sda3 238.28 GiB Luks
         ---lvm partitions

I have already reached the stage where I resized the phisical volume inside the LUKS container to 236.28GiB. I would now like to shrink the LUKS container but in such a way that I can now expand my boot partition to take up the 2.00GiB freed up. How can I go about doing this? The guide I pasted above is not very helpful when it comes to using fdisk (in my case I'll gave to use gdisk for GPT) to resize.

Any advice / help?

---

### Post by HandeH on 2014-03-23
First: backup your data!

I found it very difficult to apply this how to: Resize an Encrypted Partition (LUKS)
[http://ubuntuforums.org/showthread.php?t=726724](http://ubuntuforums.org/showthread.php?t=726724)
Reduction: Shrinking an encrypted partition

The physical reduction cannot be done and the fdisk part #5 lacks some information. The problems are: 
– On the point 3. the path might be /dev/mapper/luks-... not /dev/mapper/crypt1 or just crypt1. Also, the later command should be with "_": 
sudo mkswap -L swap_1 /dev/ubuntu-vg/swap_1 
– cryptsetup does not accept the -o parameter. 
– "cryptsetup luksClose crypt1" is not possible after opening the LUKS encryption in live session (12.10 or 13.04). Error: ioctl busy
[https://bugzilla.redhat.com/show_bug.cgi?id=809188](https://bugzilla.redhat.com/show_bug.cgi?id=809188)
So you have to reboot before using fdisk at part 5!
– if you reboot and go directly to fdisk part, the new sda2 and sda5 partitions do not automatically align nicely to start from the same sector they used to start (the sda5 is forced to start about 2048 or 2047 sectors further away). So you have to go to fdisk expert mode by commanding x. There move ('b') the sda5 to start at the proper sector (501760). 

The how to of bodhi.zazen lack some instructions on how to calculate the sizes. Usefull is the Disks tool (gnome-disks = palimpsest) which gets refreshed after pvresize commands. Still you have to somehow figure out and make notes on, what to input when using fdisk.

---

