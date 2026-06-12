---
title: "Unknown USB Flash ubuntu 10.04"
date: 2013-05-17
forum: General Help
---

### Post by AAEIV on 2013-05-17
[COLOR=#333333][FONT=Ubuntu Beta]Suddenly my Kingston DataTraveler 8GB is shown as unknown! The weird thing is that I can only "see" it through Disk Utility.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]GParted or sudo fdisk -l or sudo fdisk -lu cannot see it.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]I tried to format the entire drive as Master Boot record but I get an error saying[/FONT][/COLOR]

```
Error creating partition table: helper exited with exit code 1: In part_create_partition_table: device_file=/dev/sdc, scheme=0ped_device_get() failed[COLOR=#333333][FONT=Ubuntu Beta]the only way to be formatted is to select Don't Partition. [/FONT][/COLOR]
```

[COLOR=#333333][FONT=Ubuntu Beta]If I then try to partition the volume in ext4 I get the error[/FONT][/COLOR]

```
Error creating file system: helper exited with exit code 1: helper failed with:mke2fs 1.41.11 (14-Mar-2010)mkfs.ext4: Device size reported to be zero.  Invalid partition specified, orpartition table wasn't reread after running fdisk, due toa modified partition being busy and in use.  You may need to rebootto re-read your partition table.
```
[COLOR=#333333][FONT=Ubuntu Beta]
If I try to format the volume in NTFS I get the error[/FONT][/COLOR]

```
Error creating file system: helper exited with exit code 1: helper failed with:/dev/sdc is entire device, not just one partition.Refusing to make a filesystem here!
```
[COLOR=#333333][FONT=Ubuntu Beta]
If I select Empty nothing happens, but it is still registered as unknown.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]any ideas on how to fix it? I don't really care about the data;I just need my USB flash back![/FONT][/COLOR]

---

### Post by dino99 on 2013-05-17
try doing a cold boot with an other kernel

---

### Post by AAEIV on 2013-05-17
Thank you very much for your answer!
How to do what you suggested?

---

### Post by dino99 on 2013-05-17
cold boot : power off first to shut it down, then power on (as usual)
boot an other kernel : indeed you need a second kernel installed first, then from the grub menu, select it.

note: if you are using the 10.04 "desktop" , then you might consider it have reached its End Of Life (so no more maintenace/update)
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

### Post by AAEIV on 2013-05-17
Perhaps you misunderstood.
The problem is the USB flash drive, not the OS.
Any other flash drives has no problem of being recognized.

What I want is to know if there is a way to rebith my USB flash drive.

---

