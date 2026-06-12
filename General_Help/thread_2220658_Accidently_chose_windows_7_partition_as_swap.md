---
title: "Accidently chose windows 7 partition as swap"
date: 2014-04-28
forum: General Help
---

### Post by carlos28 on 2014-04-28
Hi guys, I was updating my ubuntu to 14.04 and something went wrong so I reinstlled ubuntu, I never used a swap partition but this time I did. I ment to choose an unallocated partition but chose my win 7 partition. I have a lenovo t430 with a triple boot system, fist partition was windows 7, second is win xp and third ubuntu and then a unallocated section. I am trying to use testdisk to recover the win 7 partition , but when I do a quick search it keeps showing the linux swap partition and no mention of the overrode win 7 partition.  

I would really appriciate any help, I new to ubuntu and love it but I still would like to recover my file from the windows 7 partition even it never works properly again, since I do not mind sticking with ubuntu.

---

### Post by HermanAB on 2014-04-28
Howdy,

The partition type was changed, so testdisk will show you the present partition type.

---

### Post by oldfred on 2014-04-28
Do not even use Ubuntu live installer. It mounts swap to speed up as DVD or flash is slower.
Use gparted or parted magic as they do not mount swap.

If swap was used you will not be able to recover Windows.

You can use tools just to reset partition type to NTFS, but not reformat it.
I know commands from Ubuntu, but not sure with other Linux repair tools.

 change sda1 to type 07 which is NTFS
sudo sfdisk --change-id /dev/sda 1 07

You may also be able to use fixparts and its t command.
```
fred@fred-Precise:~$ sudo fixparts /dev/sda
[sudo] password for fred: 
FixParts 0.8.1

Loading MBR data from /dev/sda

MBR command (? for help): ?
a    toggle the active/boot flag
c    recompute all CHS values
l    set partition as logical
o    omit partition
p    print the MBR partition table
q    quit without saving changes
r    set partition as primary
s    sort MBR partitions
t    change partition type code
w    write the MBR partition table to disk and exit

```

Also immediately change fstab to remove swap mount. Change sda5 to your Ubuntu install. And add # to front of swap line to convert to comment.
       sudo mkdir /mnt/sda5
sudo mount /dev/sda5 /mnt/sda5
gksudo gedit /mnt/sda5/etc/fstab

---

