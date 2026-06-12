---
title: "How to access your Windows drives from Ubuntu"
date: 2007-03-29
forum: General Help
---

### Post by ago on 2007-03-29
If you want to access your NTFS Windows drives follow these instructions:

[list=1]
[*] Make sure you have internet access (see the network icon on the top right)
[*] Open the "Applications" menu and select "Add/Remove..."
[*] In the listbox on the right select: "Show All Available Applications"
[*] Search for "NTFS" and select "NTFS Configuration Tool". Click OK to install it
[*] Run the configuration tool under Applications > System Tools > NTFS Configuration Tool 
[*] Select "Enable write support for internal device". Click OK to set it up.
[*] Once you reboot you will find your windows disks under /media (you can access that from Places > Computer > File System > media).[/list]

---

### Post by tuxcantfly on 2007-03-30
or, another way (from the terminal) would be to install the ntfs-3g package:
```

sudo apt-get update
sudo apt-get install ntfs-3g
```

then create a mountpoint:

```
sudo mkdir /media/windows
```

then figure out which drive is your windows drive:

```
sudo fdisk -l
```

which should return something like this:

```
geza@ubuntu:~$ sudo fdisk -l
Password:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
**/dev/sda1**   *           1       12158    97659103+   7  **HPFS/NTFS**
/dev/sda2           12159       15197    24410767+  83  Linux
/dev/sda3           30274       30401     1028160   82  Linux swap / Solaris
/dev/sda4           15198       30273   121097970   83  Linux

Partition table entries are not in disk order
geza@ubuntu:~$ 
```

Then find the line saying HPFS/NTFS (shown in bold), and take the value under "device" (in this case /dev/sda1 which is shown in bold) and substitute it into the bold portion in this command:

```
sudo ntfs-3g **/dev/sda1** /media/windows
```

then you should be able to access it at /media/windows, when done, simply unmount using:
```

sudo umount /media/windows
```

---

### Post by cowlip on 2007-03-30
Great-- thank you!

---

### Post by dbgeezer on 2007-03-30
> **ago said:**
> [*] Search for "NTFS" and select "NTFS Configuration Tool". 

This was not in my app, but Tuxcantfly's solution worked well.  Thanks!

Which repository is ntfs-3g in?

---

### Post by cowlip on 2007-03-30
ntfs-3g is in Universe

---

### Post by Aquashark on 2007-03-31
i have a suggestion for these guide

can you mention how to automatically umount Windows drives at reboot/shutdown? so people won't have to umount them manually everytime to not get errors

---

### Post by ago on 2007-03-31
> **Aquashark said:**
> i have a suggestion for these guide

can you mention how to automatically umount Windows drives at reboot/shutdown? so people won't have to umount them manually everytime to not get errors

If you have errors, write a detailed report and we will handle it properly.

---

### Post by ago on 2007-03-31
> **dbgeezer said:**
> This was not in my app,

You have to select: "Show All Available Applications"

---

### Post by theslicknick6 on 2007-03-31
nick@nick-desktop:~$ sudo umount /media/hda1
umount: /media/hda1: device is busy
umount: /media/hda1: device is busy
 thats th error i get when trying to unmount the windows partition. I am assuming its in use somehow

I also get this in Gparted
The partition could not be unmounted from the following mountpoints:

/media/hda1

Most likely other partitions are also mounted on these mountpoints. You are advised to unmount them manually.


thanks for all your help with this

---

### Post by ago on 2007-03-31
> **theslicknick6 said:**
> 
I also get this in Gparted
The partition could not be unmounted from the following mountpoints:

/media/hda1

Most likely other partitions are also mounted on these mountpoints. You are advised to unmount them manually.

I have no problems umounting.

---

### Post by Drate on 2007-04-01
It's really not there man... I just did "all available applications" and it gave me nothing.

BTW, did I understand that this would allow me to *write* to my windows drive or just look at it?  Cuz I was already able to mount it without downloading that program.

---

### Post by gfsjgbhskbfv9sfh on 2009-08-21
bump

---

