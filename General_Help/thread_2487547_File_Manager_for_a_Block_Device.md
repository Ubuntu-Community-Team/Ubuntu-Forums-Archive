---
title: "File Manager for a Block Device"
date: 2023-06-08
forum: General Help
---

### Post by Quarkrad on 2023-06-08
My native file manager is *caja* but I'm happy using the terminal. I understand using *cd* to navigate to different directories and then using commands like *ls* to 'see' what is in that directory.  Can this be done with block devices?  I have a number of logical volumes - what terminal command could I use use to *cd* into a logical volume and then use* ls* and other terminal commands to manager files/directories in that block device?

---

### Post by dragonfly41 on 2023-06-08
I have not myself yet used LVM yet .. it is a backburner project for my next major dev reconfig.

But this thread is packed with tips. CLI cheatsheets.

[https://www.howtogeek.com/40702/how-to-manage-and-use-lvm-logical-volume-management-in-ubuntu/](https://www.howtogeek.com/40702/how-to-manage-and-use-lvm-logical-volume-management-in-ubuntu/)

I had use adblock extension in browser to see woods from the trees.

---

### Post by The Cog on 2023-06-08
File managers and ls (and the whole idea of directories) are related to the contents of a filesystem. A raw block device doesn't have those - it's just a collection of data blocks. Once you have formatted a block device by writing an empty filesystem to it (or maybe a partition table and a collection of filesystems) then the content of those filesystems can be mounted. Mounting a filesystem makes its contents (files and directories) available for use by the users.
So your issue is how to mount the block device. First question is what filesystem is it formatted with.

---

### Post by MAFoElffen on 2023-06-08
???

For Ubuntu Mate, in Caja, use menu item Go > Computer > Select a block device, which will mount that device, for you to explore.

From command line, you would mount a device to a folder tag within the filesystem... Then navigate and explore via the command line, while it is mounted to the filesystem.

I think once you have done that a few times, it will be less complicated and / or mystical than you are making that.

Block devices are just storage deivces, such as hard drives, cdroms, etc. You store information in files, in blocks at a time.

---

### Post by Quarkrad on 2023-06-09
My root is formatted ext4 - my whole system is ext4.  My root is physically on a logical volume /dev/vg01/root - fstab defines this as:

```
/dev/mapper/vg01-root /               ext4    noatime,errors=remount-ro 0       1
```

When in caja, if I go *Go > Computer >* I don't specifically see my root LV, if I select *File System* I see **/home** which is on /dev/vg01/home.  I understand why I'm seeing **/home** as I have selected the File System.  I just want to select /dev/vg01/root.

```
dad@dadubuntu:~$ sudo lvdisplay
  --- Logical volume ---
  LV Path                /dev/vg01/root
  LV Name                root
  VG Name                vg01
  LV UUID                Q9V1MZ-K1yj-KyPB-Ax2Q-Cehr-yrxK-L9uVH3
  LV Write Access        read/write
  LV Creation host, time ubuntu-mate, 2023-02-21 15:48:57 +0000
  LV Status              available
  # open                 1
  LV Size                40.00 GiB
  Current LE             10240
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           253:0
   
  --- Logical volume ---
  LV Path                /dev/vg01/home
  LV Name                home
  VG Name                vg01
  LV UUID                k2I519-SiTv-PXYV-LBTB-Bquo-3jm8-LVgvgU
  LV Write Access        read/write
  LV Creation host, time ubuntu-mate, 2023-02-21 15:49:35 +0000
  LV Status              available
  # open                 1
  LV Size                50.00 GiB
  Current LE             12800
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           253:1

```

---

### Post by The Cog on 2023-06-09
/dev/vg01/root is a block device, not a filesystem. A logical volume will look exactly like a raw hard disk (although its contents may actually be scattered across a number of physical volumes in a volume group).
You can view /dev/vg01/root with caja - you will fidn it in the /dev directory. Using caja, right-click it and look at the properties. Caja will tell you it's a block device. You can't use a file manager to read block devices - they are just binary data stores. You can either mount them (if they have a filesystem written on them) and then view the filesystem contents, or you could maybe use a binary editor to look at the individual bytes. Try this to see the values of the first few bytes (good luck understanding it):
```
sudo cat /dev/vg01/root | hd | head 
```
You cannot cd into a disk though. It isn't a filesystem and doesn't have any concept of directories. You can however write a filesystem to it, mount the filesystem and then view the filesystem contents in a file manager. In your case, it has an ext4 filesystem written to it.

It's like a car park. You can't just find a large area of tarmac (analogy: raw hard disk) and say "Where are the reserved parking spaces". You have to get a load of white paint and mark out all the parking spaces first (analogy: filesystem). And then you look at the white paint markings, not at the tarmac underneath to find the reserved spaces. Hope the attempt at an analogy is not too insulting.

---

### Post by Quarkrad on 2023-06-09
No problem with analogies.  I'm trying to do something that cannot be done but I have resolved my issue but have another that I will ask in another thread of mine [https://ubuntuforums.org/showthread.php?t=2487403](https://ubuntuforums.org/showthread.php?t=2487403)

---

### Post by MAFoElffen on 2023-06-09
Then you do not want to look at block devices... You want to look at the raw device

RE: [https://en.wikipedia.org/wiki/Raw_device](https://en.wikipedia.org/wiki/Raw_device) (The first two paragraphs...)
> 
In computing, specifically in Unix and Unix-like operating systems, a raw device is a special kind of logical device associated with a character device file that allows a storage device such as a hard disk drive to be accessed directly, bypassing the operating system's caches and buffers (although the hardware caches might still be used). Applications like a database management system can use raw devices directly, enabling them to manage how data is cached, rather than deferring this task to the operating system.

In FreeBSD, all device files are in fact raw devices. Support for non-raw devices was removed in FreeBSD 4.0 in order to simplify buffer management and increase scalability and performance.[1]

In Linux kernel, raw devices were deprecated and scheduled for removal at one point, because the O_DIRECT flag can be used instead.[2] However, later the decision was made to keep raw devices support since some software cannot use the O_DIRECT flag.[3] Raw devices simply open block devices as if the O_DIRECT flag would have been specified. Raw devices are character devices (major number 162). The first minor number (i.e. 0) is reserved as a control interface and is usually found at /dev/rawctl. A command-line utility called raw[4] can be used to bind a raw device to an existing block device. These "existing block devices" may be disks or CD-ROMs/DVDs whose underlying interface can be anything supported by the Linux kernel (for example, IDE/ATA or SCSI).[5] 


---

### Post by TheFu on 2023-06-10
BTW, any file can be used as a block device and a file system can be placed into it, if you like.  This is thanks to be magic of Unix having only 2 main things
[LIST=1]
[*]files and 
[*]processes.
[/LIST]

To know which is what, it is really simple.  Anything that isn't a running process is a file.  Period.  Running processes have a program, owner running the process, and shows up in the process table - via ps or top or htop or .... 

**Everything else is a file.**  Directories are files.  Disk devices are files.  Disk partitions are files.  Logical Volumes are files.  ZFS pools are files.  Keyboards are files. Audio processors are files. A tty or ptty is a file. A socket is a file.  A NIC is a file.  You get the idea.  Files have an owner, permissions, ACLs. That applies to device files, regular files, directories, all files.  It is simple and liberating. It means we can do all sorts of things with "files" that aren't typically used as a file.  Sometimes our unique way of using a file it genius ..... or really, really, dumb.  Unix can't tell which so it allows whatever you can create.

A quick example is an ISO file.  We can copy that ISO file bit-for-bit onto a flash drive or CDROM or HDD and it will behave like a CDROM.  This is why we can "burn" an ubuntu installation to a USB flash drive using 
```
sudo cp /tmp/path/to/ubuntu.iso  /dev/sdz
```
Note, the target is the entire USB device, not a partition. That's because ISO files have a partition table built into them.  Any program that will move bits from A-->B _unmolested_ can be used for this purpose.  **cat** can be used or **dd** or **less** or **more** or Etcher.

We can create an ISO from any CD/DVD storage too.
```
sudo cp   /dev/sdy     /tmp/path/to/new.iso
```

Easy, peasy.

All thanks to "files" being the primary type of object on all Unix-like systems. That includes Android, iOS, OSX, Linux, BSD, and the commercial UNIX systems.

---

