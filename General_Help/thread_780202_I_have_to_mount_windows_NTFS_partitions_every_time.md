---
title: "I have to mount windows NTFS partitions every time i restart"
date: 2008-05-03
forum: General Help
---

### Post by DaveBG on 2008-05-03
Hi. I installed ubuntu 8.04 (i think we call it hardy here, i do not know why) and every time i restart it i do not have access to the windows partitions.

If i choose Places -> and choose windows drive its icon appears on the desktop and then all is OK but i have to click on all partitions to mount them every reboot. Is there a way to automate this during boot and also to remove the icons from the desktop as i have them in the Places menu?

---

### Post by Zorael on 2008-05-03
Sure. Post the terminal output of the following command.
```
$ sudo fdisk -l
```

As well as the contents of **/etc/fstab**.

---

### Post by ryanhaigh on 2008-05-03
You might want to look at this: 

[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

Im pretty sure ntfs-3g is included in the default install so there is no need for the install step.

Make sure you have universe enabled in system>software sources, then use whatever method you like to install ntfs-config. Run that program from the menu, it should prompt you for your admin password and you can go from there.

---

### Post by _godbout_ on 2008-05-03
Hey there,

I've got a kind of same problem, but for my FAT32 partition. It used to be mounted automatically under gutsy, but with hardy, it doesn't appear. I checked the fstab file, and it's not inside. I guess that I could add a correct line for the partition, but I don't know how to get the information to put in the file. 

Any idea?
Thanks :)

---

### Post by DaddyX3 on 2008-05-03
Like Zoreal said, we need to get some basic info from you guys before we can help you. Open up a terminal and copy the output of: 
```
sudo fdisk -l
```
and paste it back here. Also we need to see your fstab file:
```
gedit /etc/fstab
```
and paste back here. Thanks-

---

### Post by DaveBG on 2008-05-03
Here is mine:

```
dave@dave-desktop:~$ sudo fdisk -l
[sudo] password for dave: 

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd932d932

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3251    26113626    7  HPFS/NTFS
/dev/sda2            3252       30401   218082375    5  Extended
/dev/sda5            3252       30401   218082343+   7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0c070635

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         958     7695103+   7  HPFS/NTFS
/dev/sdb2             959       30401   236500897+   7  HPFS/NTFS

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe087b660

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       30401   244196001    7  HPFS/NTFS
dave@dave-desktop:~$ 
dave@dave-desktop:~$ 
dave@dave-desktop:~$ 

```


```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext3    loop,errors=remount-ro 0       1
/host/ubuntu/disks/boot /boot           none    bind            0       0
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

---

### Post by Hardrive on 2008-05-03
As root, add this to /etc/fstab.  Change /mnt/windows to wherever you want the NTFS directory mounted, as long as you create the directory.

```

/dev/sda1   /mnt/windows    ntfs-3g    rw,defaults 0 0

```

Then, test it by mounting it as root
```

sudo mount /mnt/windows

```

---

### Post by dale_nx26 on 2008-05-03
I use the Storage Device Manager, click on the partition/drive, and have the program auto configure it. It should auto mount it during startup. This is what I did to enable a library in rhythmbox so i don't have to import all my music over to Ubuntu.

---

### Post by doriard on 2008-05-03
Where is the Storage Device Manager? I used something similar in Kubuntu, now in Hardy I'm using Ubuntu and can't find the Storage Manager.

---

### Post by dale_nx26 on 2008-05-03
in the add/remove program (applications>add/remove). then search for it in the search box. After installed, go to system>administration>storage...Then choose the partition you want. It should ask to configure, let it (don't worry it won't change anything).

---

### Post by _godbout_ on 2008-05-04
Here is mine! 

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x71ec3339

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        5227    41985846   83  Linux
/dev/sda2            5228        5762     4297387+  82  Linux swap / Solaris
/dev/sda3   *        5763       13666    63488880    7  HPFS/NTFS
/dev/sda4           13667       19457    46516207+   b  W95 FAT32
guillaume@ChanChan-Destkop:~$ 

```

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=cc6c0107-c2bc-409c-9637-01443d6547ca /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda2
UUID=1eb16bdf-2949-49f7-b8d6-18df2c1f1976 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

I use to have all my partitions available and written in fstab under Gusty, but nothing anymore under Hardy!

---

### Post by koshari on 2008-05-04
godbout where do you want to mount your ntfs and fat32 partitions?

---

### Post by koshari on 2008-05-04
godbout if you want to mount the drives in the /mnt dir firstly create 2 placeholder directorys.

```
sudo mkdir /mnt/winnt

sudo mkdir /mnt/winfat32
```

then add the following lines to the end of your fstab file, 


```
/dev/sda3   /mnt/winnt    ntfs-3g    rw,defaults 0 0
/dev/sda4   /mnt/winfat32    vfat    rw,defaults 0 0
```

then run fstab to mount the new additiions, 

```
sudo mount -a
```

if there are any errors post them here

---------------------------------------

---

### Post by DaveBG on 2008-05-04
OK i mounted all my drives in /mnt now :)

Good they are not on desktop anymore too :)

10x!

---

### Post by Bastaard on 2008-05-04
Had the exact same problem which was easily solved: [http://ubuntuforums.org/showthread.php?p=4863122#post4863122](http://ubuntuforums.org/showthread.php?p=4863122#post4863122)

---

### Post by DaddyX3 on 2008-05-04
Are you all good now? Is this solved? I would not have done it exactly the way Hardrive posted, but if it worked .... GREAT!! :)

EDIT: Sorry, I somehow posted without seeing the whole 2nd. page to this thread:oops

---

### Post by Aat on 2008-05-04
I had this problem running gutsy, but solved it through the Storage Device manager.
But now I've upgraded to hardy, and my file-system gets mounted too.
So in nautilus I now see 'file system' and '58.2 GB Harddisk' (my Ubuntu partition) at the same time...
Any ideas how this is possible? And how I can fix that?

---

### Post by DaveBG on 2008-05-05
Yes my drives are mounted in the mnt now :)

---

### Post by _godbout_ on 2008-05-06
> **koshari said:**
> godbout if you want to mount the drives in the /mnt dir firstly create 2 placeholder directorys.

```
sudo mkdir /mnt/winnt

sudo mkdir /mnt/winfat32
```

then add the following lines to the end of your fstab file, 


```
/dev/sda3   /mnt/winnt    ntfs-3g    rw,defaults 0 0
/dev/sda4   /mnt/winfat32    vfat    rw,defaults 0 0
```

then run fstab to mount the new additiions, 

```
sudo mount -a
```

if there are any errors post them here

---------------------------------------

Hi Koshari,

Thanks for the help!
But it's still not really what I wanted to do. Now the icon for my fat partition disappeared, and the content in is the mnt/fat folder. I would like the icon to still be there in the Places menu and in Nautilus, but I want it already mounted.
Another point is that my French accent characters are destroyed, but I guess I can deal with that myself by looking for the character encoding option somewhere.

edit: Ok, funny, I solved the problem of the French accents. But I still have 2 problems :p
First, many of my folders (I don't know the logic in which ones) loses their first capital letter for a lowercase. If I have a look under Windows, everything is fine.
The second point is that, of course, the volume is mounted with the root rights. And now, when I try to do anything on my automounted partition, it doesn't work because I don't have the correct rights. How can I change that?!

edit2: Problem 1 solved with the dmask=000 option. But my folders are still messed up with the lowercase/uppercase, weird?!

Thanks!

---

### Post by Th3Professor on 2008-05-06
Another option:

Boot back into Windows and do a fresh "shut down".
Then boot back into *nix and it'll possibly show up.

Sometimes MS Windows doesn't properly shut down (such as during a crash or when it locks up and you have to force it). When this is the case, it will possibly not auto-mount when you've booted into your other OS.

A quick and easy fix for that is to simply boot back into MS Windows and do the proper shut down.

That may not always be the case but it is definitely one workable option.

---

### Post by wrgb2 on 2008-05-06
I used the NTFS Configuration Tool in Hardy to set this up - Add/Remove Appications>System Tools>NTSF Configuration Tool.  After setting them up with this tool, they are mounted automatically at restart.

Randy
[http://nocostsoftware.blogspot.com](http://nocostsoftware.blogspot.com)
[http://freebloggingtools.blogspot.com](http://freebloggingtools.blogspot.com)

---

### Post by _godbout_ on 2008-05-06
Ok, I succeeded to make the FAT32 partition mount automatically. To add the rights for writing I had to add the dmask option, and for the lowercase/uppercase folders stuff I had to add the shortname=mixed one.

Now, last question, is there a way to not display the icon on the desktop? :p

Thanks in advance :)

edit: I mean, without the gconf-editor trick. I want to remove the icon of my FAT32 partition, but I would like to keep the ones from any USB key plugged for example. Thanks!

---

