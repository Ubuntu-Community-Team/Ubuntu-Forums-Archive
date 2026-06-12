---
title: "Mounting fakeRAID1 NTFS"
date: 2007-11-24
forum: General Help
---

### Post by SoulRaver on 2007-11-24
o/ all
First some :popcorn: coz ya gona need some...

Symptom:
Problem mounting additional fakeRAID1 NTFS array.

Home remedies:
Loads of googeling that resulted in this:
Installed dmraid, all ntfs tools, etc

Used 'sudo dmraid -ay' to find and activate the RAID1
'sudo dmraid -r
/dev/sda: sil, "sil_afajeacfagaj", linear, ok, 488395630 sectors, data@ 0
/dev/sdd: isw, "isw_dfdcedcdfh", GROUP, ok, 976773166 sectors, data@ 0
/dev/sde: isw, "isw_dfdcedcdfh", GROUP, ok, 976773166 sectors, data@ 0'

As my MOBO is a MSI P-35 Platinum with the ICH9R chip the 'isw' denotes the Intel fakeraid. Just to check:
'cd /dev/mappper/
ls
control  isw_dfdcedcdfh_The Twins'

'sudo mkdir /media/TheTwinsR

Goodie.. lets mount:
'sudo mount -t ntfs /dev/mapper/isw_dfdcedcdfh_The Twins /media/TheTwinsR
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .'

:confused:

Anyone?

---

### Post by SoulRaver on 2007-11-24
Oh.. feel free to mention any info you may need...

---

### Post by Rizado on 2007-11-24
Please put the commands you write and the output in code thingie like:

```

$ ls -l

brw-rw---- 1 root disk 254,  0 2007-11-24 09:31 isw_bbdjfefhjf_HDS72161_RAID
brw-rw---- 1 root disk 254,  1 2007-11-24 09:31 isw_bbdjfefhjf_HDS72161_RAID1

```

Because right now atleast I can't tell what's output and what's input and what's your words.

Anyway, the only problem I can see right now is the space in the drive name, you should try to avoid them and if you have to use it put it between **"**

So run:
```
sudo mount -t ntfs "/dev/mapper/isw_dfdcedcdfh_The Twins" "/media/TheTwinsR"
```
Hopefully it'll work.

---

### Post by SoulRaver on 2007-11-24
> **Rizado said:**
> Please put the commands you write and the output in code thingie like:

```

$ ls -l

brw-rw---- 1 root disk 254,  0 2007-11-24 09:31 isw_bbdjfefhjf_HDS72161_RAID
brw-rw---- 1 root disk 254,  1 2007-11-24 09:31 isw_bbdjfefhjf_HDS72161_RAID1

```

Because right now atleast I can't tell what's output and what's input and what's your words.

Soz about that: will correc

---

### Post by SoulRaver on 2007-11-24
```
user@box:~$ sudo mount -t ntfs "/dev/mapper/isw_dfdcedcdfh_The Twins" "/media/TheTwinsR"
[sudo] password for user:
NTFS signature is missing.
Failed to mount '/dev/mapper/isw_dfdcedcdfh_The Twins': Invalid argument
The device '/dev/mapper/isw_dfdcedcdfh_The Twins' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
user@box:~$
```

Was what I got.. erph whada?

---

### Post by Rizado on 2007-11-24
> **SoulRaver said:**
> ```
user@box:~$ sudo mount -t ntfs "/dev/mapper/isw_dfdcedcdfh_The Twins" "/media/TheTwinsR"
[sudo] password for user:
NTFS signature is missing.
Failed to mount '/dev/mapper/isw_dfdcedcdfh_The Twins': Invalid argument
The device '/dev/mapper/isw_dfdcedcdfh_The Twins' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
user@box:~$
```

Was what I got.. erph whada?I'm guessing you had windows on that partition? Can you still start it?

Please run: ```
sudo fdisk -l "/dev/mapper/isw_dfdcedcdfh_The Twins"
``` and post the output.

The thing is "/dev/mapper/isw_dfdcedcdfh_The Twins" should be the drive like /dev/hda. Then the partitions are named "/dev/mapper/isw_dfdcedcdfh_The Twins1" and "/dev/mapper/isw_dfdcedcdfh_The Twins2"
Atleast this is how it is on my computer, I fear that your partitions has gone missing somehow...

---

### Post by SoulRaver on 2007-11-24
It does not have a windows *instalation* in it self just a large RAID1 backup storage for windows files. No trouble booting into windows.


```
user@box:/dev/mapper$ sudo fdisk -l "/dev/mapper/isw_dfdcedcdfh_The Twins"

WARNING: GPT (GUID Partition Table) detected on '/dev/mapper/isw_dfdcedcdfh_The Twins'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/mapper/isw_dfdcedcdfh_The Twins: 500.1 GB, 500104826880 bytes
255 heads, 63 sectors/track, 60800 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x49f63dcc

                               Device Boot      Start         End      Blocks   Id  System
/dev/mapper/isw_dfdcedcdfh_The Twins1               1       60801   488381440    7  HPFS/NTFS
user@box:/dev/mapper$
```

---

### Post by Rizado on 2007-11-24
Well there really should be a "/dev/mapper/isw_dfdcedcdfh_The Twins1". That's the name of the partition so I don't understand where it is. But anyway there's something you could try...

At the beginning of the drive is the partitiontable and stuff and that's what you try to mount as ntfs, which doesn't work because it's not the partition. But if we tell mount to skip the beginning it should work.

```
sudo mount -t ntfs -o offset=32256 "/dev/mapper/isw_dfdcedcdfh_The Twins" "/media/TheTwinsR"
```I use this method to mount a dmcrypt loopback device which windows xp in vmware uses as it's drive. (Might just make a guide for this some day)

If this doesn't work I don't know what will.  On the other hand if it does work you can add it to /etc/fstab. Should look something like ```
"/dev/mapper/isw_dfdcedcdfh_The Twins" /media/TheTwinsR ntfs-3g defaults,umask=0,offset=32256 0 0
```
I don't know if " works in fstab and how it reacts to spaces but if it doesn't work you could try to make a link. Symbolic or something else I don't know. **Using ntfs-3g will enable writesupport!**

---

### Post by SoulRaver on 2007-11-25
Bad news.. something broke somewhere. The machine wont even boot fully now. Stops somewhere in usb dedection (Or atleast thats what I think it is as it promts about my razer mouse found)

Doing a complete reinstall later on, right now need to get back to work, on vista :(

---

### Post by ToniBlixt on 2007-11-26
i managed to mount my ntfs raid0 partition by label, the name is Portal.
$ sudo mkdir /media/C
$ sudo mount -t ntfs /dev/disk/by-label/Portal /media/C/

---

### Post by SoulRaver on 2007-11-28
Ok so I tracked down what was the issue here;

Initramfs has a bug in it. There are workarounds for it tho they get broken by dmraid. It's a lesser known bug for compatability on betwene the initramfs and some fakeraid/SATA controllers (I got Intel's ICH9R Chipset - MSI P35 Platinum mobo).

This issue arose partly with 7.04 and more so with 7.10 distros as it was implemented.

Some of the suggested remedies are reinstalling initram-tools, using all_generic_ide modifier and some I can't recollect right now.

All the remedies work above, but break once I use dmraid to enable my fakeRAID1 array.

I really don't know to who or where I should post any kind of bugreport... if so needed

---

