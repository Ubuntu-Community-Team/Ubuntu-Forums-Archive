---
title: "[SOLVED]no boot device found (encrypted disk)"
date: 2017-09-17
forum: General Help
---

### Post by francis.boterblom on 2017-09-17
Hi everyone,

I have a strange problem, i have kubuntu 16.04 running with a full disk encryption. Worked fine for months. But after running a live Ubuntu from USB and starting Gparted on it, it does not find its boot device after restart. To be clear i only started Gparted but did not do any changes. 

I am puzzled of what went wrong....

any help is welcome.


Regards,

Francis

---

### Post by oldfred on 2017-09-17
Full disk encryption uses LVM, so you cannot edit LVM volumes with gparted. Only the container for the LVM which you cannot change as the LVM takes the entire physical partition.

So did you change boot flag if UEFI boot from ESP.
Or do something to /boot partition which is outside LVM partition.
Or if newer UEFI system did you switch boot modes in UEFI from/to UEFI or BIOS? So boot does not match install?

       Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)

I do not know LVM nor encryption, but post this:

sudo parted -l

---

### Post by francis.boterblom on 2017-09-18
Thanks for the help and information. Here is the requested info:

```
ubuntu@ubuntu:~$ sudo parted -l
Model: ATA SAMSUNG SSD PM85 (scsi)
Disk /dev/sda: 256GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size   File system  Name                  Flags
 1      1049kB  538MB   537MB  fat32        EFI System Partition  boot, esp
 2      538MB   1050MB  512MB  ext4
 3      1050MB  256GB   255GB



```

As answer on questions, no i did not change anything only started ubuntu live and started the gparted application, but closed soon not doing anything.


Regards,

Francis

---

### Post by francis.boterblom on 2017-09-18
Ok i solved it, after some more googling.
Apperently you have to add a boot option in your bios bootsequence for EUFI and point it to your EFI/ubuntu/shimx64.efi

See this: [https://askubuntu.com/questions/731931/uefi-not-finding-a-bootable-system-on-xps13](https://askubuntu.com/questions/731931/uefi-not-finding-a-bootable-system-on-xps13)

Regards,

Francis

---

