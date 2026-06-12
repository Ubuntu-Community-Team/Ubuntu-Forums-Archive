---
title: "Custom Boot Entry Problems"
date: 2016-02-26
forum: General Help
---

### Post by boundlessmind8 on 2016-02-26
Hello all,

     I have two iso images I would like to add to my GRUB configuration, because they do not seem to be able to run on a live USB (I have tried every conceivable option, including dd and unetbootin). When I run update-grub after adding the entries, I am told there is a syntax error in the configuration file. When I try to boot the entries in GRUB anyway, I get something like:

ERROR: Cannot find file: /home/ultimate-edition-4.6-x64-gamers.iso
ERROR: Cannot find 'loop' - no such file or directory
ERROR: You need to load the kernel first. 

Attached are the screenshots of the custom boot config file and the update-grub output.

     I have checked, double-checked, and triple-checked the locations of vmlinuz.efi and initrd.lz in the iso files and of the iso files themselves, so that is not the problem. I have tried everything I can think of, although I am by no means an expert. Thanks in advance for any help / insight you can provide : )

---

### Post by deadflowr on 2016-02-26
I believe you need to set the device path in the loopback loop, like
```
loopback loop (hd0,5)$isofile
```
(hd0 being hard drive disk one, and 5 being the fifth partition, change to match your own setup.)

Since the system will need to know where on the disk to look for the file.
quick Reference: [https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)

---

### Post by boundlessmind8 on 2016-02-26
So would the 'hd0' be the same as 'sda, sdb' etc? 

I can find the partition ID's, but don't see hd-anything when I run fdisk -l . 

Do I need to run a different command to double check this parameter?

---

### Post by deadflowr on 2016-02-26
sda would translate to hd0 for the hard drive.
And 1 should translate to 1 for the partitions 
so sda1 should be hd0,1.
and sda2 should be hd0,2
and so on and,

sdb1 should be hd1,1
and sdb2 should be hd1,2.

If the iso-file is in your current home folder (of the system you are running)
then simply run
```
df
```
it'll list the device name in the same line as the file-system ( the ** /** symbol equals the root file-system, typically what you would be looking for, unless you set it up differently)
You can also look at 
```
sudo blkid
```
It'll list information on partitions.
But probably less easy to understand than the df command will.

Does any of that make sense?

---

