---
title: "using a new swap space, linux keeps using old one"
date: 2008-02-10
forum: General Help
---

### Post by thefatmoop on 2008-02-10
recently i resized my partitions, and i redid grub, but now i'm having problems with getting the swap to work

i'm able to go into gparted and turn the swap on... but when i reboot it goes back to trying to mount my old swap that i origonally had. how do i make it use the new swap space on boot?

it's working and the swap is fine, but everytime i reboot it goes back to "no swap"

when fdisk was checking the 21 mount filesys routine check, i noticed a FAIL on the swap and i think it said something like "unable to find partition .../.../..." it went by too fast to read

---

### Post by seventhc on 2008-02-10
You only need one swap partition,
what is the output of
```
sudo fdisk -l
```

---

### Post by danwood76 on 2008-02-10
you probably need to update your fstab to use the new swap.
could you also post:
```

cat /etc/fstab

```

---

### Post by thefatmoop on 2008-02-10
```
 Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5ae1ea1c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12433    99868041   83  Linux
/dev/sda2           12434       12815     3068415   82  Linux swap / Solaris


beta@bessa :~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=3bcbcaf9-e143-4548-b00c-f85bf9421471 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=02CE4F96CE4F80C1 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda2
UUID=2C88743C8874071C /media/sda2     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda3
UUID=7e5798bf-91f2-4384-b335-fd2c9ab2db02 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
beta@bessa :~$ 

```

sounds like i would need to update it, should i turn swapon before updating?/ how do i update?

---

### Post by seventhc on 2008-02-10
OK, looks like 1 swap is showing.
The swap should go on at boot, what did you change in grub.


I never did an ubdate on fstab, so I'll let danwood76 tell you that. :)
It probably is whats needed.

---

### Post by thefatmoop on 2008-02-10
that's what i would think, but it never auto loads the swap

---

### Post by danwood76 on 2008-02-10
What you need to do is modify the swap entry like so:

```

sudo gedit /etc/fstab

```

this will open the fstab in gedit, with root access so you can save it.
then replace this line:
```

UID=7e5798bf-91f2-4384-b335-fd2c9ab2db02 none            swap    sw              0       0

```
with
```

/dev/sda2              none            swap    sw              0       0

```

just looking at your previous post.
have you completely removed the ntfs partitions from your disk?
If so you should remove these entries, but if you just place a # infront of them they will be ignored when the file is loaded.

so you should end up with:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=3bcbcaf9-e143-4548-b00c-f85bf9421471 /               ext3    defaults,errors=remount-ro 0       1

# /dev/sda1
#UUID=02CE4F96CE4F80C1 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda2
#UUID=2C88743C8874071C /media/sda2     ntfs    defaults,umask=007,gid=46 0       1

/dev/sda2              none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

```

I have spaced it out a little so you can see what I did.
obviously if the ntfs partitions still exist remove the '#' from the starts of those two lines

regards,
Danny

---

### Post by thefatmoop on 2008-02-10
so it worked but when i put it on hibernate it worked... then i took it off hibernate and the swap was an "unknown" partition and the computer was unable to read from it. now my main partition has the same "unable to read disk data" error from Gparted. Nothing seems to be wrong, and the graphical map of the harddrive seems normal. The computer boots and runs fine... o.o?

---

### Post by thefatmoop on 2008-02-10
```
 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0

# /dev/sda4
#UUID=3bcbcaf9-e143-4548-b00c-f85bf9421471 /               ext3    defaults,errors=remount-ro 0       1

# /dev/sda1
#UUID=02CE4F96CE4F80C1 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda2
#UUID=2C88743C8874071C /media/sda2     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda3

/dev/sda2              none            swap    sw              0       0

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0


```

---

### Post by danwood76 on 2008-02-11
Is the swap still listed as active in system monitor?

Gparted has crazy ideas about the allocation on my hard disk, I dont think its anything to worry too much about. Its all working fine.
Unless your needing to repartition any time soon?

---

### Post by WaveMyBlackFlag on 2008-02-11
Another lost user.  seems with my last upgrade, my swap partition has not been active.  
:confused::confused::confused::confused::confused::confused:
It took a while to figure why everything had seemed to slow down something rotten, I have random freezes that can take anywhere from 2 to 15 minutes to recover from (if there is one thing I have learned with this system, if it freezes, leave it alone... it comes out of it and somehow recovers...  I don't get it, but I don't complain....)

anyway, here is my problem, from what I can tell this is what is needed, if more is needed I'm good at copy and paste like any other half wit.

***

jacob@ubu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/hdb1 :
UUID=00fe1b12-d792-448b-b878-c396efcb8963 / ext3 defaults,errors=remount-ro 0 1
[COLOR="Red"][B]# Entry for /dev/ !! UNKNOW DEVICE !! :
UUID=539cef74-4f57-43ad-8f36-73d3fef6fddb none swap sw 0 0[/B][/COLOR]  <--(Thats my swap I assume.)

/dev/cdrom /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hdc /media/cdrom1 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0
jacob@ubu:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           504        490         13          0         10        139
-/+ buffers/cache:        340        163
[COLOR="Red"]**Swap:            0          0          0**[/COLOR]
jacob@ubu:~$

---

### Post by Dojan5 on 2008-02-11
That happened me too XDD
It was easy to fix though.
You maybe don't have he program installed or maybe yu do.
In System>Administration>GParted
Open it up and right-click your swap and click mount.
If you don't have it installed open up Add/Remove and search for GParted, install it and follow the above instructions.
Or you could use a Live CD since GParted is already installed on those, in same menu

---

### Post by thefatmoop on 2008-02-11
i've given up on it lol but no fdisk -l would loose the partition, in conky it would loose the partition and say "no swap".... AND gparted would say "partition unreadable" 

All this would only happen when i try to hibernate. ohh and the hibernate doesn't work. it just loads linux as if i just turned it on from a full shutdown. 

If i don't hibernate, the swap loads from boot and runs fine..I think it works fine otherwise... i just opened 2 virtual copies of vista and my laptop, although running SLOW, is running fine and didn't crash like when i had no swap. swap at 57%... First time i've seen it above 0% lol laptop was going to use vista...so disappointed with it i just made ubuntu the base os i'm glad i bought 2 gigs of ram

---

### Post by thefatmoop on 2008-02-11
> **WaveMyBlackFlag said:**
> Another lost user.  seems with my last upgrade, my swap partition has not been active.  
:confused::confused::confused::confused::confused::confused:
It took a while to figure why everything had seemed to slow down something rotten, I have random freezes that can take anywhere from 2 to 15 minutes to recover from (if there is one thing I have learned with this system, if it freezes, leave it alone... it comes out of it and somehow recovers...  I don't get it, but I don't complain....)

anyway, here is my problem, from what I can tell this is what is needed, if more is needed I'm good at copy and paste like any other half wit.

***

jacob@ubu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/hdb1 :
UUID=00fe1b12-d792-448b-b878-c396efcb8963 / ext3 defaults,errors=remount-ro 0 1
[COLOR="Red"][B]# Entry for /dev/ !! UNKNOW DEVICE !! :
UUID=539cef74-4f57-43ad-8f36-73d3fef6fddb none swap sw 0 0[/B][/COLOR]  <--(Thats my swap I assume.)

/dev/cdrom /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hdc /media/cdrom1 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0
jacob@ubu:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           504        490         13          0         10        139
-/+ buffers/cache:        340        163
[COLOR="Red"]**Swap:            0          0          0**[/COLOR]
jacob@ubu:~$


oops, owell 

Yeah you need to install Gparted from add/remove. if you have the swap listed, right click the swap partition and click "swapon" and within 30 secs it should come up under 
```
 sudo fdisk -l 
``` 
and if your system doesn't use the swap on bootup and you need to manually turn it on every boot (look at page 1) 

try hibernating and tell us if it works, or if like in my case your swap takes a poop

(remember that you must unmount a partition for gparted todo anything to it (no lock icon))

---

### Post by WaveMyBlackFlag on 2008-02-12
Well just to let you all know, I solved it whilst waiting for replies.  Was simple really, located which partition should be my swap using qparted...  then through the terminal used the "mkswap"  command (I think thats what it was called), remembered the UUID it spit out at me and changed it in fstab.  Bada-bing, swaptastic.

> jacob@ubu:~$ sudo fdisk -l

Disk /dev/hda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x27ceb680

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4996    40130338+   7  HPFS/NTFS

Disk /dev/hdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0c61ec87

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       14405   115708131   83  Linux
/dev/hdb2           14406       14593     1510110    5  Extended
/dev/hdb5           14406       14593     1510078+  82  Linux swap / Solaris
jacob@ubu:~$ 


SOO much more stable... no more crashes or what seem to be memory dumps.:guitar:

---

