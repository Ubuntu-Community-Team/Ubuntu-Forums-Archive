---
title: "[SOLVED] gparted help"
date: 2007-10-08
forum: General Help
---

### Post by questpro on 2007-10-08
I am using Ubuntu dual boot with windows xp.

 My hard disk consists: 70Gb windows partition and 10GB Ubuntu partition.

I did this using gparted live cd at the time of installing ubuntu.

 Now I would like to partition my 70GB into two partitions :

1. 20GB for windows xp

2. rest of 50GB for the data partition which can be used from the both operating systems.

My question is : What is the file system name for the data disk i am going to make. And I appreciate any other ideas!!

Thanks in advance:)

---

### Post by prince_niceguy on 2007-10-08
> **questpro said:**
> I am using Ubuntu dual boot with windows xp.

1. 20GB for windows xp
-- ntfs

2. rest of 50GB for the data partition which can be used from the both operating systems.

--- fat32 or ntfs... prefer fat32 as the driver is included in the kernel. but would take more space. 

My question is : What is the file system name for the data disk i am going to make. And I appreciate any other ideas!!

Thanks in advance:)

for linux use either ext3, jfs or xfs... only ext3 there is a windows driver to read ext3 partition...

---

### Post by dabl on 2007-10-08
Recommendation for partitions:

1. 20GB -- Win XP
2. 49.5GB (approx -- let this one float to the max available space left) -- DATA (shared, NTFS format)
3. 10GB -- Linux (ext3 format)
4. 0.5GB -- Linux swap

This will use your 4 available primary partitions.

If it happens you have a laptop and you want it to hibernate, then change the swap space to the same size as your RAM, and take the difference out of #2.

Install Win XP first, and use it to also format partition #2 (aka "D:") as NTFS.  Then install Ubuntu.  I recommend Alternate Install to see & mount partitions easier.  Let Grub write the boot menu where it defaults, which is the MBR where Win XP boots.

:)

---

### Post by questpro on 2007-10-08
I think I am confusing you about my situation. To put it more clearly-

I have 70gig ntfs partition used by my windows xp and 10gig used by Ubuntu.

I would like to make some 40gig  /data partition from 70gig ntfs I have.

Is it possible to use that /data partition in both the OS. I want to make this since I can not write to ntfs partition while using ubuntu. And also it is slow to copy or take data from windows ntfs partition.

Hope you understood my problem.

---

### Post by questpro on 2007-10-08
> **dabl said:**
> Recommendation for partitions:

1. 20GB -- Win XP
2. 49.5GB (approx -- let this one float to the max available space left) -- DATA (shared, NTFS format)
3. 10GB -- Linux (ext3 format)
4. 0.5GB -- Linux swap

This will use your 4 available primary partitions.

If it happens you have a laptop and you want it to hibernate, then change the swap space to the same size as your RAM, and take the difference out of #2.

Install Win XP first, and use it to also format partition #2 (aka "D:") as NTFS.  Then install Ubuntu.  I recommend Alternate Install to see & mount partitions easier.  Let Grub write the boot menu where it defaults, which is the MBR where Win XP boots.

:)


Thanks for your recommended partition sizes. I would do that.

But I am already using dual boot of XP and Ubuntu. Can't I resize now:confused:


Edit: I already defragmented the windows XP partition to use gparted live cd and to build the /data partition

---

### Post by prince_niceguy on 2007-10-08
yes you can ...

install ntfs-3g and it will make your drive read/write in linux. 

sudo aptitude install ntfs-3g


after installation change your fstab... replace ntfs with ntfs-3g an eg. is given below for your reference.

/dev/sda5   /data   ntfs-3g  defaults,locale=en_US.utf8    0    0

if you are confused then post your fstab and will post back your required fstab.

after that just reboot and your drives should be mounted in read write mode...

---

### Post by questpro on 2007-10-08
Thanks for the reply.

I have just tried using gparted live cd. And my drives are:

```

unallocated 30 gig 

/dev/hda1 ntfs  20 gig

/dev/hda2 extended
         hda5 ext3 13.7 gig
         hda6 linux-swap 1000.3Mb

unallocated 7.19 gig

/dev/hda4     ntfs    1 gig

```

And I struck here : I don't see any /data shared option to make "shared data disk"

Can I make the same thing using ntfs-3g as you told. I have never used this before.

EDIT: I would like to change the two unallocated partitions shown above to one/two "shared data" partitions.

---

### Post by questpro on 2007-10-08
> **prince_niceguy said:**
> yes you can ...
if you are confused then post your fstab and will post back your required fstab.
.


As I posted above, I did not use ubuntu for partitioning before. I already posted how my drives listed when using *gparted live cd*.

following is the output from the ubuntu terminal. 

Is this what you asked ?


```
 xxx@xxx:~sudo fdisk -l
Password:

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *        3188        6748    28603732+   7  HPFS/NTFS
/dev/hda2            6749        8660    15358140    5  Extended
/dev/hda4            9599        9729     1052226   d7  Unknown
/dev/hda5            6749        8532    14329948+  83  Linux
/dev/hda6            8533        8660     1028128+  82  Linux swap / Solaris
```

---

### Post by prince_niceguy on 2007-10-08
can you tell me which /dev/hda<number> you want to use for the data. Which ever you want just format them to ntfs/fat32.

after that login into linux and hopefully these drives should be auto mounted if not, then put them in fstab using following command

$ sudo cp /etc/fstab /etc/fstab.bk

$ sudo gedit /etc/fstab

/dev/hda3   /media/sda3   vfat    iocharset=utf8,umask=000  0    0
/dev/hda1   /windows   ntfs-3g  defaults,locale=en_US.utf8    0    0


where sda3 or sda1 should be substituted with the number your fdisk gives. also make sure the folder which you are going to mount is present. for e.g. in the above one disk /dev/hda3 is mounted to folder /media/sda3. so folder /media/sda3 should be created first. It can be anything. you need stick to the folder name given above.

---

### Post by questpro on 2007-10-09
> **prince_niceguy said:**
> can you tell me which /dev/hda<number> you want to use for the data. Which ever you want just format them to ntfs/fat32.

after that login into linux and hopefully these drives should be auto mounted if not, then put them in fstab using following command

$ sudo cp /etc/fstab /etc/fstab.bk

$ sudo gedit /etc/fstab

/dev/hda3   /media/sda3   vfat    iocharset=utf8,umask=000  0    0
/dev/hda1   /windows   ntfs-3g  defaults,locale=en_US.utf8    0    0


where sda3 or sda1 should be substituted with the number your fdisk gives. also make sure the folder which you are going to mount is present. for e.g. in the above one disk /dev/hda3 is mounted to folder /media/sda3. so folder /media/sda3 should be created first. It can be anything. you need stick to the folder name given above.


I can only create only one drive using gparted as max limit is 4. How to use the other partition? there are two unallocated partitions in my list.

EDIT: Please refer the post #7. You can see the 2 unallocated partitions. Actuallly, as I resized the XP partition I got one partition. And also I had windows recovery partition, I formatted that as well giving me total of 2 unallocated partitions.

EDIT: I would use hda3 and hda5 for the unallocated partitions. Because hda1,2,4 are being used already.

---

### Post by questpro on 2007-10-09
Thanks for the reply...

I formatted my two unallocated partitions to ntfs. And I could only make one of them to a new primary partition, because it allows only 4 partitions.

As I rebooted into windows, its pretty obvious that I can see the "drive D"  which is the primary partition I made. And I can not see the other ntfs partition I made.

And when I booted into Ubuntu7.04, I can see the "windiws drive D" as "disk" which I need to provide the password to enter into that. Is this called a "shared data disk" or do I make that *disk* anything else??

I am just wondered to see another disk labled hda3 with 1gig. I saw this space only when using gaparted cd. This does not appear when we boot into windows XP.  Do you have any adea about this partition and how to use this??

Now I have the 7.6gig ntfs left unused. I can not make the primary partition as it does not allow. And I can not make the extended or any other partition as its giving no more options when I boot with gparted live cd.

Thank you for reading all this. Thanks for the help in advance.

---

### Post by prince_niceguy on 2007-10-09
you cannot make more than 4 primary partition. create instead extended partition and then format it to ntfs.

with that you should be able to use your 7 Gb left on the disk.

---

### Post by questpro on 2007-10-10
> **prince_niceguy said:**
> you cannot make more than 4 primary partition. create instead extended partition and then format it to ntfs.

with that you should be able to use your 7 Gb left on the disk. 

But I dont see the option "extended" partition. Anyways I will try this out one more time. 

And I can not write to the other partition in ubuntu. I can see that as drive D in windows XP. 
Should I install ntfs-3g now. Is it works for Ubuntu7.04 gnome.

```


:~$ sudo fdisk -l
Password:

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *        3188        6748    28603732+   7  HPFS/NTFS
/dev/hda2            6749        8660    15358140    5  Extended
/dev/hda3               1        3187    25599546    7  HPFS/NTFS
/dev/hda4            9599        9729     1052226   d7  Unknown
/dev/hda5            6749        8532    14329948+  83  Linux
/dev/hda6            8533        8660     1028128+  82  Linux swap / Solaris

Partition table entries are not in disk order





```

---

### Post by questpro on 2007-10-10
> **prince_niceguy said:**
> yes you can ...

if you are confused then post your fstab and will post back your required fstab.

after that just reboot and your drives should be mounted in read write mode...

I installed ntfs-3g.

How do I post my fstab. What is the command for that???

---

### Post by questpro on 2007-10-10
Yes, I have just read about fstab now. I created a back up for that. I wanted to add the line as you told. But I am confused as they UUID instead of dev /hda1....

can you put some more light on it. I am giving my fstab...

```



# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda5
UUID=aa247497-6383-4fbc-816c-8c7abfa857c7 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=E83C0F443C0F0CEE /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda2
UUID=4D5E-0E4A  /media/hda2     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda3
UUID=C0D0502CD0502AC4 /media/hda3     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda6
UUID=414e2878-517f-4ba8-bfbe-cfd698ba4cbc none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0







```
 

EDIT: I am getting so many errors when open the fstab file for editing. I used gksudo gedit /etc/fstab Whats wrong with this...I can not find any  file name extension for this. Please clarify...

EDIT: I was trying the wrong command. It is--- sudo nano /etc/fstab

Thanx:)

---

### Post by questpro on 2007-10-10
Ok,  After some googling, I got something i am unsure.

I was trying to use a NTFS PARTITION to work in BOTH operating systems XP and UBUNTU.

I found in one UBUNTU thread that I can not WRITE to the WINDOWS NTFS partition. So What do I need to do? Shall change the NTFS to FAT32 !!!???

---

### Post by prince_niceguy on 2007-10-10
here you go... here is the modified fstab of yours. let me know if this works. sorry I am checking my threads once in the day so delayed response.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda5
UUID=aa247497-6383-4fbc-816c-8c7abfa857c7 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=E83C0F443C0F0CEE /media/hda1     ntfs-3g  defaults,locale=en_US.utf8    0    0
# /dev/hda2
UUID=4D5E-0E4A  /media/hda2     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda3
UUID=C0D0502CD0502AC4 /media/hda3     ntfs-3g  defaults,locale=en_US.utf8    0    0
# /dev/hda6
UUID=414e2878-517f-4ba8-bfbe-cfd698ba4cbc none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

basically i have changed ntfs to ntfs-3g in the fstab and defaults against that line to the default given above.

---

### Post by prince_niceguy on 2007-10-10
also for the parition.. when you are creating the 4th partition make sure it is extended partition.

---

### Post by questpro on 2007-10-11
I still can not write to NTFS partition. I can read the contents, that i could do before editing the fstab as well.

---

### Post by forestpixie on 2007-10-11
sorry - missed the bit where you said you'd installed ntfs3g

---

### Post by questpro on 2007-10-11
> **forestpixie said:**
> sorry - missed the bit where you said you'd installed ntfs3g

OK. I have an NTFS partition which shows as drive D in windows XP. I would like to write to that partition from UBUNTU.

Now I installed ntfs-3g from the repository and edited the fstab according to post #17.

Yes, I can read that drive by prviding the password. (media/hda3) Can not write to it.

Any suggestions please...

---

### Post by prince_niceguy on 2007-10-11
can you print the following details of the command 

ls /media/hda3

i think it is currently owned by root.

do one thing create a folder in root partition say data

$ cd /
$ sudo mkdir data
$ sudo chmod 777 -R /data

change you fstab so that /media/hda3 is now changed to /data

now run the following command

$ sudo umount -a
$ sudo mount -a

Now you should be able to read write in to the /data folder which is your ntfs drive basically...

hope that helped...

---

### Post by questpro on 2007-10-12
thanks for the reply. I have some errors.  I am posting my terminal here.

```



xxxx@xxxx:~$ ls /media/hda3
BOOT.INI                NTDETECT.COM   System Volume Information
Documents and Settings  ntldr          WERUNTIME.INI
hpqpd.ini               Program Files  WINDOWS

xxxxi@xxxx:~$ cd /
xxxx@xxxxx:/$ ls
bin    dev     initrd.img      lib64       opt   srv  var
boot   etc     initrd.img.old  lost+found  proc  sys  vmlinuz
cdrom  home    lib             media       root  tmp  vmlinuz.old
data   initrd  lib32           mnt         sbin  usr

xxxx@xxxx:/$ sudo chmod 777 -R /data
Password:
xxxx@xxxx:/$ cd  
xxxx@xxxx:~$ sudo nano /etc/fstab
xxxx@xxxx:~$ sudo nano /etc/fstab
xxxx@xxxx:~$ sudo nano /etc/fstab

xxxx@xxxx:~$ sudo umount -a
umount: /dev: device is busy
umount: /proc/bus/usb: device is busy
umount: /var/run: device is busy
umount: /sys: device is busy
umount: /: device is busy

xxxx@xxxx:~$ sudo mount -a
[mntent]: line 1 in /etc/fstab is bad
mount: special device /dev/disk/by-uuid/4D5E-0E4A does not exist




``` 


EDIT: Hey, /media/hda3 in my machine is 1gig windows swap. Only after I partitoned the space I could see that 1 gig.

I have one more partition of 24.4gig (Drive D of windows xp) which I dont see any drive name for that in UBUNTU. When click open that, it asks to enter tha password. Then its displayed as drive with name "disk" on the natilius. it does not work the same as /media/hda1 which is "*Windows drive C"*

---

### Post by questpro on 2007-10-12
I tried to do the same with my 24.4gig volume. But I wonder, I dont see any information about this volume, when I wanted to edit. Can you check this out for me please...

```


xxxx@xxxx:~$ ls /media/disk
System Volume Information

xxxx@xxxx:~$ sudo umount -a
umount: /dev: device is busy
umount: /proc/bus/usb: device is busy
umount: /var/run: device is busy
umount: /sys: device is busy
umount: /: device is busy

xxxx@xxxx:~$ sudo mount -a
[mntent]: line 1 in /etc/fstab is bad
mount: special device /dev/disk/by-uuid/4D5E-0E4A does not exist

xxxx@xxxx:~$ sudo nano /etc/fstab




```

Here when I see fstab, i did not see any entry for my 24.4gig.

---

### Post by prince_niceguy on 2007-10-12
just to get  a clearer picture..

how many hard drives are you having?
how many partitions on each drives?

how many partitions are visible in windows?
how many partitions visible in gparted?

if you can print a snapshot of gparted it would be easier i think.

---

### Post by questpro on 2007-10-12
> **prince_niceguy said:**
> just to get  a clearer picture..

how many hard drives are you having? *[COLOR="DarkOrchid"]Only one. Its with the laptop I am using.[/COLOR]*
how many partitions on each drives? *[COLOR="DarkOrchid"]3 primary, 1extended, 1 unallocated[/COLOR]*

how many partitions are visible in windows? [COLOR="DarkOrchid"]Drive C   ( /dev/hda1), Drive D (/dev/hda3)[/COLOR]
how many partitions visible in gparted? [COLOR="DarkOrchid"]Please refer the screenshot attached[/COLOR]

if you can print a snapshot of gparted it would be easier i think. [COLOR="DarkOrchid"]Please check the attachment[/COLOR]

Please check the screenshot attached. Thank you

---

### Post by prince_niceguy on 2007-10-12
OK...

first to get your 7 GB partition to use.

delete the 1 GB partition of the ntfs. Now you will 7 + 1 = 8 GB total partition as unallocated. You should be able to format it to the primary partition. you can choose ntfs or fat32 if you are planning to share it between windows and linux.

note down the /dev/hda<number> which comes for this disk... should be hda7.. but just confirm it.

now make the following folders in root using sudo

$ cd /
$ sudo mkdir windows
$ sudo mkdir data1
$ sudo mkdir data2

we will mount hda1 to windows (assuming it is where your windows install resides). 
hda3 to data1
hda7 or whatever is the last 8 gb drive to data2

gotta leave now.. will give the fstab how it will look in a while...

---

### Post by prince_niceguy on 2007-10-12
Here you go....

following would be your fstab... put this and reboot your computer... ensure you have created the folders mentioned above... windows, data1, data2

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0

# /dev/hda5 - your root partition
/dev/hda8 /               ext3     defaults 0       1

# /dev/hda6 - your swap for linux
/dev/hda6 none            swap    sw              0       0

#/dev/hda1 - your drive c
/dev/hda1   /windows   ntfs-3g  defaults,locale=en_US.utf8    0    0

#/dev/hda5 - your drive d
/dev/hda3   /data1   ntfs-3g  defaults,locale=en_US.utf8    0    0

#/dev/hda7 - your drive of 8 gb - change hda7 to the one which gparted gives.
/dev/hda7   /data1   ntfs-3g  defaults,locale=en_US.utf8    0    0

#/dev/scd0 - last but not the least your cd drive.
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by questpro on 2007-10-13
Thanks a lot. It worked.

I deleted the UUID completely and replaced as you explained. All three volumes were mounted, but I could not see them on the desktop. Then again I changed the mount point to /media/windows,disk1,disk2 

Thats it. thanks again. Its a lot of effort. I am attaching my screenshot for future reference.

---

### Post by prince_niceguy on 2007-10-13
glad it work... :-)

---

### Post by prince_niceguy on 2007-10-13
i generally do not keep them as disk on the desktop but folders in root as it is easier to then access them in nautilus ... but individual preferences i guess .. :-)

---

