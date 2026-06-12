---
title: "Mounting sdb8 --&gt;    /dev/vg1/lv1 /mnt/seagate"
date: 2018-01-19
forum: General Help
---

### Post by frappe792 on 2018-01-19
Hi guys,

need your help your help here. Not having much luck mounting an external hard drive (that I pulled out from an old seagate central). In disk management I see the drive with multiple partitions and the one I am trying to mount is partition 8 (2.0TB LVM2 PV). The device is listed as /dev/sdb8
Runninig sudo lvscan it returns
```
 ACTIVE            '/dev/vg1/lv1' [1.81 TiB] inherit
```
I made the directory in root /mnt/seagate, but when I try to mount
```
$ sudo mount /dev/vg1/lv1 /mnt/seagate
```
it returns
```
mount: /mnt/seagate: wrong fs type, bad option, bad superblock on /dev/mapper/vg1-
lv1, missing codepage or helper program, or other error.
```
Also tried 
```
$ sudo fuseext2 -o ro -o allow_other /dev/mapper/vg1-lg1 /
mnt/seagate
```
and it returned
```
fuse-umfuse-ext2: version:'0.4', fuse_version:'29' [main (fuse-ext2.c:331)]
fuse-umfuse-ext2: Failed to access '/dev/mapper/vg1-lg1' [main (fuse-ext2.c:341)]
```
I don't know why I'm getting these error messages and would appreciate any help I can get. Thanks!

---

### Post by DuckHook on 2018-01-20
Please refrain from using different sizes, colours and fonts. It makes your posts difficult to read, especially on small screen devices. Also, please post your output between [noparse]```
 and 
```[/noparse] tags for clarity. Or highlight the output and use the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the *Adv Reply* toolbar.

---

### Post by frappe792 on 2018-01-23
Bump

---

### Post by DuckHook on 2018-01-23
These instructions should help: [https://unix.stackexchange.com/questions/339011/how-do-i-mount-an-lvm-partition](https://unix.stackexchange.com/questions/339011/how-do-i-mount-an-lvm-partition)

---

### Post by frappe792 on 2018-01-23
Thanks, but they don't.

I still get this no matter what I do

```
[COLOR=#000000][FONT=&amp]mount: /mnt/seagate: wrong fs type, bad option, bad superblock on /dev/mapper/vg1-[/FONT][/COLOR]lv1, missing codepage or helper program, or other error.
```

---

### Post by DuckHook on 2018-01-23
> **frappe792 said:**
> ..no matter what I do..

Please post precisely what you do. Give details. We need to know if even a small typo is being made. To recap, steps are:
```
sudo apt-get install lvm2   #This step may or may not be required.
sudo pvscan                 #Use this to verify your LVM partition(s) is/are detected.
sudo vgscan                 #Scans for LVM Volume Group(s)
sudo vgchange -ay           #Activates LVM Volume Group(s)
sudo lvscan                 #Scans for available Logical Volumes
sudo mount /dev/YourVolGroup00/YourLogVol00 /YourMountPoint
```
Your results "bad superblock" do not bode well, but let's not jump to conclusions. It may simply be that you have not invoked vgchange properly and mount is not able to read an lvm.

Need those detailed steps you took.

---

### Post by frappe792 on 2018-01-25
[COLOR=#000000][FONT=monospace][SIZE=2][FONT=arial]
Hope this helps[/FONT][/SIZE]

[/FONT][/COLOR]```
[COLOR=#5454FF][FONT=monospace]**:~**[/FONT][/COLOR][COLOR=#000000][FONT=monospace]$ [/FONT][/COLOR][COLOR=#000000][FONT=&amp]sudo apt-get install lvm2

[/FONT][/COLOR][FONT=monospace][COLOR=#000000]Reading package lists... Done[/COLOR]
Building dependency tree        
Reading state information... Done
lvm2 is already the newest version (2.02.168-2ubuntu3).
The following packages were automatically installed and are no longer required:
  libfakekey0 linux-headers-4.13.0-25 linux-headers-4.13.0-25-generic linux-headers-4.13.0-29
  linux-headers-4.13.0-29-generic linux-image-4.13.0-25-generic linux-image-4.13.0-29-generic
  linux-image-extra-4.13.0-25-generic linux-image-extra-4.13.0-29-generic linux-tools-4.13.0-29
  linux-tools-4.13.0-29-generic
Use 'sudo apt autoremove' to remove them.
0 to upgrade, 0 to newly install, 0 to remove and 1 not to upgrade.
[/FONT][FONT=monospace]

[/FONT][COLOR=#000000][FONT=monospace]:[/FONT][/COLOR][COLOR=#5454FF][FONT=monospace]**~**[/FONT][/COLOR][COLOR=#000000][FONT=monospace]$ [/FONT][/COLOR][FONT=monospace]sudo pvscan

[/FONT][FONT=monospace][COLOR=#000000]PV /dev/sdb8   VG vg1             lvm2 [1.81 TiB / 0    free][/COLOR]
  Total: 1 [1.81 TiB] / in use: 1 [1.81 TiB] / in no VG: 0 [0   ]
[/FONT][FONT=monospace]
[/FONT][FONT=monospace][COLOR=#000000]:[/COLOR][COLOR=#5454FF]**~**[/COLOR][COLOR=#000000]$ [/COLOR][/FONT][FONT=monospace]sudo vgscan

[/FONT][FONT=monospace][COLOR=#000000]Reading volume groups from cache.[/COLOR]
  Found volume group "vg1" using metadata type lvm2[/FONT]

[COLOR=#000000][FONT=monospace]:[/FONT][/COLOR][COLOR=#5454FF][FONT=monospace]**~**[/FONT][/COLOR][COLOR=#000000][FONT=monospace]$ [/FONT][/COLOR][FONT=monospace][COLOR=#000000]sudo vgchange -ay[/COLOR]
  1 logical volume(s) in volume group "vg1" now active

[/FONT][FONT=monospace]
[/FONT][FONT=monospace][COLOR=#000000]:[/COLOR][COLOR=#5454FF]**~**[/COLOR][COLOR=#000000]$ sudo lvscan[/COLOR]
  ACTIVE            '/dev/vg1/lv1' [1.81 TiB] inherit


[/FONT][FONT=monospace][COLOR=#000000]:[/COLOR][COLOR=#5454FF]**~**[/COLOR][COLOR=#000000]$ sudo mount /dev/vg1/lv1 /mnt/seagate[/COLOR]
mount: /mnt/seagate: wrong fs type, bad option, bad superblock on /dev/mapper/vg1-lv1, missing co
depage or helper program, or other error.

[/FONT]
```[FONT=monospace]


[SIZE=2][FONT=arial]The directory has been created but it's empty

[/FONT][/SIZE][/FONT][SIZE=2][FONT=arial]:~/mnt/seagate$[/FONT][/SIZE]

---

### Post by frappe792 on 2018-01-29
Bump

---

