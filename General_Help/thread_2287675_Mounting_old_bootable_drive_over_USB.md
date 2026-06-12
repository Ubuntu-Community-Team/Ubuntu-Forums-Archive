---
title: "Mounting old bootable drive over USB"
date: 2015-07-21
forum: General Help
---

### Post by Brad wilkinson on 2015-07-21
I am having some problems mounting an older bootable drive that is now sitting in a USB drive enclosure.

I have followed the instructions here: [https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB) as well as here: [http://askubuntu.com/questions/285539/detect-and-mount-devices](http://askubuntu.com/questions/285539/detect-and-mount-devices) but I still have a problem. 

After running lsblk I get the drive identified as sde
> NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0   1.8T  0 disk 
&#9500;&#9472;sda1   8:1    0   1.8T  0 part /
&#9500;&#9472;sda2   8:2    0     1K  0 part 
&#9492;&#9472;sda5   8:5    0     8G  0 part [SWAP]
sde      8:64   0   1.8T  0 disk 
&#9500;&#9472;sde1   8:65   0   1.8T  0 part 
&#9500;&#9472;sde2   8:66   0     1K  0 part 
&#9492;&#9472;sde5   8:69   0     8G  0 part 
sr0     11:0    1  1024M  0 rom  

and then I use sudo lshw and get 
>      *-scsi:4
          physical id: 6
          bus info: usb@3:3
          logical name: scsi35
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             product: 2105
             vendor: ASMT
             physical id: 0.0.0
             bus info: scsi@35:0.0.0
             logical name: /dev/sde
             version: 0
             serial: 00000000000000000000
             size: 1863GiB (2TB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=6 sectorsize=512 signature=000ddd7b
           *-volume:0
                description: Linux filesystem partition
                physical id: 1
                bus info: scsi@35:0.0.0,1
                logical name: /dev/sde1
                capacity: 1855GiB
                capabilities: primary bootable
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@35:0.0.0,2
                logical name: /dev/sde2
                size: 8188MiB
                capacity: 8188MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sde5
                   capacity: 8188MiB
                   capabilities: nofs

This tells me sde is DOS partitioned, and that /dev/sde1 is primary bootable, but it doesn't tell me what file system type it is, and just straight DOS is not a option when you go and read man mount.

What am I missing so I can tell what file system type to tell it to mount for this volume?

---

### Post by sudodus on 2015-07-21
Check what is mounted with

```
df
```

and if nothing is mounted at **/mnt**, try mounting like this

```
sudo mount /dev/sde1 /mnt
```

If that does not work, run this command to get more information in a wide terminal window (you can select 'full screen')

```
sudo lsblk -fm
```

and after that use the following command to mount it (replace [COLOR="#FF0000"]**ext4**[/COLOR] with whatever you found with the previous command)

```
sudo mount -t [COLOR="#FF0000"]ext4[/COLOR] /dev/sde1 /mnt
```

---

### Post by Bucky Ball on 2015-07-21
*Thread moved to **General Help**.*

sde1? I presume it is EXT* from this:

```
description: **Linux filesystem partition**
physical id: 1
bus info: scsi@35:0.0.0,1
logical name: **/dev/sde1**
capacity: 1855GiB
capabilities: primary bootable
```

Create a mount point and try to mount it:

```
sudo mkdir /mnt/sde1
sudo mount /dev/sde1 /mnt/sde1
```

Open Gparted, if you have it, and check the filesystem.

---

### Post by Brad wilkinson on 2015-07-21
Hello sudodus, 

I tried what you suggested, and this is the output from the terminal:
```
bradley@UbuntuDesktop:~$ df
Filesystem      1K-blocks     Used  Available Use% Mounted on
/dev/sda1      1914492284 87015764 1730202872   5% /
none                    4        0          4   0% /sys/fs/cgroup
udev              4067804        4    4067800   1% /dev
tmpfs              815720     1408     814312   1% /run
none                 5120        0       5120   0% /run/lock
none              4078592      644    4077948   1% /run/shm
none               102400       32     102368   1% /run/user
bradley@UbuntuDesktop:~$ sudo mount /dev/sde1 /mnt
[sudo] password for bradley: 
mount: you must specify the filesystem type
bradley@UbuntuDesktop:~$ sudo lsblk -fm
NAME   FSTYPE LABEL MOUNTPOINT NAME     SIZE OWNER GROUP MODE
sda                            sda      1.8T root  disk  brw-rw----
&#9500;&#9472;sda1 ext4         /          &#9500;&#9472;sda1   1.8T root  disk  brw-rw----
&#9500;&#9472;sda2                         &#9500;&#9472;sda2     1K root  disk  brw-rw----
&#9492;&#9472;sda5 swap         [SWAP]     &#9492;&#9472;sda5     8G root  disk  brw-rw----
sde                            sde      1.8T root  disk  brw-rw----
&#9500;&#9472;sde1                         &#9500;&#9472;sde1   1.8T root  disk  brw-rw----
&#9500;&#9472;sde2                         &#9500;&#9472;sde2     1K root  disk  brw-rw----
&#9492;&#9472;sde5 swap                    &#9492;&#9472;sde5     8G root  disk  brw-rw----
sr0                            sr0     1024M root  cdrom brw-rw----
```

Since sde1 doesn't have a FSTYPE listed, I tried EXT2, 3 and 4, and got the following answer:
```
mount: wrong fs type, bad option, bad superblock on /dev/sde1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

Hello Bucky Ball. I added GParted to my system, and upon looking at sde1 it is listed as "Filesystem: Unknown" and comes with the following warning messages:
```
Unable to detect file system! Possible reasons are:
- The file system is damaged
- The file system is unknown to GParted
- There is no file system available (unformatted)
- The device entry /dev/sde1 is missing
```

In GParted there is an option Device->Attempt Data Rescue but I have not tried that yet.

Is there anything else I should try?

---

### Post by sudodus on 2015-07-22
Have you got any idea of what file system it could be?

The structure makes me think it has been running a linux operating system, with /dev/sde1 as the root partition, (in analogy with your /dev/sda1). Is that correct?

It seems to me, that the file system is damaged.

If you have very important data on it, you should start by making a cloned copy with ***ddrescue***, and do the rest of the operations on the cloned copy.

Otherwise you can go directly to recovery operations, or if there is nothing unique on that older bootable drive, you can make a new partition table and partitions with file systems and make a fresh installation with ***gparted***.

Recovery tools: [testdisk and photorec](http://www.cgsecurity.org/)

---

### Post by Brad wilkinson on 2015-07-22
sudodus, it is my previous Ubuntu system drive, so it should have a standard Ubuntu install on it.

However it is likely I damaged the file system with my amateur attempts to fix the system (in the end I think it was only a dead bios battery......)

I shall however follow your further instructions. I'll get back to you later. Thanks for the help so far!

---

### Post by sudodus on 2015-07-22
Good luck :-)

If I would be away from the keyboard, when you need help, there are several other people who can help ...

---

### Post by steeldriver on 2015-07-22
The `file` utility may be able to detect the filesystem type of the raw block device:

```

sudo file -sL /dev/sde1

```

---

### Post by Brad wilkinson on 2015-07-22
sudodus I have downloaded ddrescue and read through the info ddrescue and found something that might be a problem:
```
Recoverable formats
     As ddrescue uses standard library functions to read data from the
     device being rescued, only mountable device formats can be rescued
     with ddrescue. DVDs can be mounted and they can be rescued,
     "compact disc digital audio" CDs can't, "video CDs"[1] maybe.
     [1] [http://en.wikipedia.org/wiki/Video_CD](http://en.wikipedia.org/wiki/Video_CD)
```

and 
```
   If the damaged drive is not listed in /dev, then you cannot rescue
it.  At least not with ddrescue.
```
which suggests that ddrescue will not work in this situation as I cannot mount the disk to /dev/

Is there another way to copy (clone?) the drive to a second 2TB usb drive before I try running Gparted->Device->Attempt Data Rescue on the disk?

steeldriver I used your suggestion and this is the result:
```
bradley@UbuntuDesktop:~$ sudo file -sL /dev/sde1
[sudo] password for bradley: 
/dev/sde1: AIX core file fulldump 32-bit, \377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377 64-bit, \377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377\377
```

does this mean anything to you? it looks like it might be file permission levels (r-w-e) to me.

Also - how is it reading *_anything_* from /dev/sed1? it doesn't exist?

---

### Post by steeldriver on 2015-07-22
... I think it just confirms the partition is corrupted: octal \377 is hex FF or decimal 255 so it's just indicating a sequence of FF bytes

---

### Post by sudodus on 2015-07-23
You see /dev/sde, and that is enough for ddrescue to work.

I agree with steeldriver, the info you have provided indicates that the partition is corrupted.

So if the data are very valuable I suggest that the first step is to make a cloned copy of the whole drive /dev/sde (not only the partition) to another drive of at least the same size. And then try to recover data from the cloned copy.

The file system might or might not be possible to recover with ***testdisk***. If testdisk succeeds, fine!

If testdisk fails, because too much is damaged, there might still be file data on the hard disk's surface. A lot of these data can be identified by ***photorec***, and files can be created on another drive. But the directory structure and the file names are lost.

---

### Post by Brad wilkinson on 2015-07-24
Back again....

So I have a second 2Gig HDD in a USB caddy, and now I can see:
```
NAME   FSTYPE LABEL MOUNTPOINT NAME     SIZE OWNER GROUP MODE
sda                            sda      1.8T root  disk  brw-rw----
&#9500;&#9472;sda1 ext4         /          &#9500;&#9472;sda1   1.8T root  disk  brw-rw----
&#9500;&#9472;sda2                         &#9500;&#9472;sda2     1K root  disk  brw-rw----
&#9492;&#9472;sda5 swap         [SWAP]     &#9492;&#9472;sda5     8G root  disk  brw-rw----
sde                            sde      1.8T root  disk  brw-rw----
&#9500;&#9472;sde1                         &#9500;&#9472;sde1   1.8T root  disk  brw-rw----
&#9500;&#9472;sde2                         &#9500;&#9472;sde2     1K root  disk  brw-rw----
&#9492;&#9472;sde5 swap                    &#9492;&#9472;sde5     8G root  disk  brw-rw----
sdf                            sdf      1.8T root  disk  brw-rw----
sr0                            sr0     1024M root  cdrom brw-rw----
```

where sde is the damaged disk, and sdf is the brand-spanking-new disk. I then went to the [GNU ddrescue manual]("http://www.gnu.org/software/ddrescue/manual/ddrescue_manual.html") and typed in the first line from example 1 in section 7. I get the following result:
```
bradley@UbuntuDesktop:~$ ddrescue -f -n /dev/sde /dev/sdf logfile
ddrescue: Can't open input file: Permission denied
bradley@UbuntuDesktop:~$ ddrescue -d -f -n /dev/sde /dev/sdf logfile
ddrescue: Can't open input file: Permission denied
```

The second line is from me reading through all the options and trying the -d flag which has the following description:
```
Use direct disc access to read from infile, bypassing the kernel cache. (Open the file with the O_DIRECT flag). Use it only on devices or partitions, not on regular files. Sector size must be correctly set for this to work. Not all systems support this. 
```

In both cases it didn't work.

Is something I did wrong? I would suspect I have set the wrong flags, but I don't actually understand what most of the descriptions mean on the Manual page.

---

### Post by sudodus on 2015-07-24
You must run ddrescue with superuser privileges, when booting from a drive that is not involved in the cloning, so you have

boot drive: (often a live CD/DVD or USB drive, but can also be an internal HDD, in your case /dev/sda)
source drive: /dev/sde
target drive:/dev/sdf

and run

```
sudo ddrescue -f -n /dev/sde /dev/sdf logfile
```

---

### Post by Brad wilkinson on 2015-07-29
Ok so the sudo ddrescue blah blah worked (note to self: don't use USB2 next time ~36hrs)

I now have a cloned drive that testdisk can see as ext4, and run checks on and so forth.

What exactly do I need to do to repair it so the rest of the computer will see sde as an ext4 disk now?

This is the log file from Testdisk. Maybe it will tell you what I need to do?

[ATTACH=CONFIG]263455[/ATTACH]

---

### Post by sudodus on 2015-07-29
I'm no testdisk expert - have used it only once or twice - but if I remember correctly it suggests repair actions - and I suggest that you "let it do it's magic."

[COLOR="#FF0000"]If someone with more experience is reading this, please chip in an help :-)[/COLOR]

As always, I can suggest that you search for tips via the internet.

-o-

There are several suggested repair actions in the log file

```
[COLOR="#0000FF"]grep fsck testdisk.txt[/COLOR]
recover_EXT2: "e2fsck -b 32768 -B 4096 device" may be needed
recover_EXT2: "e2fsck -b 32768 -B 4096 device" may be needed
recover_EXT2: "e2fsck -b 98304 -B 4096 device" may be needed
recover_EXT2: "e2fsck -b 163840 -B 4096 device" may be needed
recover_EXT2: "e2fsck -b 229376 -B 4096 device" may be needed
recover_EXT2: "e2fsck -b 294912 -B 4096 device" may be needed
recover_EXT2: "e2fsck -b 32768 -B 4096 device" may be needed
recover_EXT2: "e2fsck -b 98304 -B 4096 device" may be needed
recover_EXT2: "e2fsck -b 163840 -B 4096 device" may be needed
recover_EXT2: "e2fsck -b 229376 -B 4096 device" may be needed
recover_EXT2: "e2fsck -b 294912 -B 4096 device" may be needed
recover_EXT2: "e2fsck -b 819200 -B 4096 device" may be needed
recover_EXT2: "e2fsck -b 884736 -B 4096 device" may be needed
recover_EXT2: "e2fsck -b 1605632 -B 4096 device" may be needed
recover_EXT2: "e2fsck -b 2654208 -B 4096 device" may be needed
recover_EXT2: "e2fsck -b 4096000 -B 4096 device" may be needed
[COLOR="#FF0000"]fsck.ext4 -p -b superblock -B blocksize device[/COLOR]
```

If you get no other advice, I suggest that you start with the last (red) command line

```
fsck.ext4 -p -b superblock -B blocksize device
```

where you enter the correct values for blocksize and device (if you know the blocksize).

---

