---
title: "Unable to find swap space signature"
date: 2006-11-25
forum: General Help
---

### Post by Bosonator on 2006-11-25
Howdy,

My Kubuntu system recently had some trouble, which I fixed, but it involved modifying my fstab file, and a couple of others as well. Now when my computer boots, I get a message saying something like "Unable to find swap signature". Also, df doesn't show my swap space mounted at all. My machine runs ok, but I figure since I've given up some space for swap, I might as well be making the most of it! Can someone tell me if I need to change anything in my fstab to do that? 

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1	/		ext3 	defaults,errors=remount-ro 0 1
/dev/hdb5	/home 		ext3 	defaults 0 2
/dev/hdb6	none 		swap 	sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

#JMB 061123: commented this out because I removed a cdrom drive
#/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
#/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

##JMB 060610:
/dev/hda1       /media/WinXP	ntfs    nls=utf8,umask=0222 0       0


```

---

### Post by 56phil on 2006-11-26
I had the same problem. It was related to the edgy upgrade (UUID stuff), but judging from your fstab, you haven't done that upgrade. Am I right? Never mind; I just saw that you use edgy. Try this entry:
```
free -m
```
The last line should tell you your swap status.If it says:
```
swap: 0 0 0
```Then try:
```
sudo swapon -va
```This command will activate all found swap partitions. Then try 'free -m' again.

I hope this helps. If not, reply and we'll try something else. As you can see my post-edgy fstab is a little different:
```

prh@phil-laptop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          1010        852        157          0         73        465
-/+ buffers/cache:        313        697
Swap:         2353          0       2353
prh@phil-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1 -- converted during upgrade to edgy
UUID=d558c3d1-04b3-4c21-9ef3-c0fd3a03ff5f / ext3 defaults,errors=remount-ro 0 1
# /dev/hda5 -- converted during upgrade to edgy
UUID=7caa1bfa-715c-43cc-a875-9247bd7892e4 none swap sw 0 0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

you may have to get the UUID from the system and put it in your FSTAB.

---

### Post by Bosonator on 2006-11-26
Hi Phil,

When I enter ```
 sudo swapon -va 
``` I get the following: ```
  swapon on /dev/hdb6
swapon: /dev/hdb6: Invalid argument

```
So I guess that didn't work :(. 

Because you asked, my edgy fstab used to be like yours, but I was fixing something, and I did it by replacing all the UUID entries to actual file paths.

---

### Post by 56phil on 2006-11-26
ok try this wicked entry:
```

echo UUID=`sudo mount -fv / | cut -d' ' -f1 | tr -d [:digit:] | xargs sudo fdisk -l | grep swap | cut -d' ' -f1 | xargs sudo vol_id -u` none swap sw 0 0

```
It will recreate the line you need in your fstab file. Replace the swap line in your fstab with the result of the wicked entry. Then, try swapon -va again.

---

### Post by yoel.koenka on 2006-11-26
Hey all,
I'm having the same fstab after upgrading to Edgy but I can't use "sudo swapon -va". It says: "Invalid argument".
I didn't replace the UUIDs with paths so I guess I don't need to use the wicked line you've posted.
Can anyone tell me how to get my swap back (and bu that being able to hibernate my laptop)?
10x :)
Yoel.

---

### Post by CoolkcaH on 2006-11-26
Hi.
I have the same problem. When I did the "wicked" line I got the exact same thing I already had on fstab but I did copy/paste just to be sure and when I do sudo swapon -va I get this:

swapon on /dev/disk/by-uuid/2fc72bf0-b2ea-4713-b853-5e3627c645c7
swapon: /dev/disk/by-uuid/2fc72bf0-b2ea-4713-b853-5e3627c645c7: Invalid argument

This is the swap line on fstab:
UUID=2fc72bf0-b2ea-4713-b853-5e3627c645c7 none swap sw 0 0

Hope someone can work this out...

---

### Post by taurus on 2006-11-26
What's the output of this command from a terminal then?

```
sudo fdisk -l
```

---

### Post by 56phil on 2006-11-26
if the UUID is already in fstab, then do:
```

sudo mkswap /dev/<swap partition path>
sudo swapon -va

```
**[SIZE="4"]CAUTION:[/SIZE]** mkswap is a dangerous command. Make sure that the *swap partition path* is right. 

mkswap will generate a new UUID that will need to be put in fstab.

---

### Post by 56phil on 2006-11-26
Once you get swap working, check out this thread to get hibernate/suspend working -> [http://ubuntuforums.org/showthread.php?t=287962](http://ubuntuforums.org/showthread.php?t=287962) :)

---

### Post by CoolkcaH on 2006-11-26
I did this:

[https://launchpad.net/distros/ubuntu/+bug/66637/comments/23]("https://launchpad.net/distros/ubuntu/+bug/66637/comments/23")

Remember to do everything with sudo or else it will not work.

Everything is working now. I recommend anyone with this problem to try that.

---

### Post by yoel.koenka on 2006-11-26
You bunch of crazy horses!
Nobody told me doing mkswap on /dev/hda1 would erase my partition.
I nearly had an heart attack!
It's 01:35 AM now and I just got it fixed with a LiveCd of Edgy and the marvelous command "e2fsck /dev/hda1".
I did what you said and next thing I know, grub wouldn't mount my hard-drive.
Of course this all happened because I didn't know what mkswap does but maybe others don't as well so beware you guys. don't mess with /dev/***
You might get a fright... :)
Yoel.

---

### Post by wadehel on 2006-11-26
> **taurus said:**
> What's the output of this command from a terminal then?

```
sudo fdisk -l
```

mine shows this:

Disk /dev/hda: 20.5 GB, 20547841536 bytes
255 heads, 63 sectors/track, 2498 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2392    19213708+  83  Linux
/dev/hda2            2393        2498      851445    5  Extended
/dev/hda5            2393        2498      851413+  82  Linux swap / Solaris

What then?

---

### Post by taurus on 2006-11-26
> **wadehel said:**
> mine shows this:

Disk /dev/hda: 20.5 GB, 20547841536 bytes
255 heads, 63 sectors/track, 2498 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2392    19213708+  83  Linux
/dev/hda2            2393        2498      851445    5  Extended
/dev/hda5            2393        2498      851413+  82  Linux swap / Solaris

What then?
Your swap partition is not mounted, either!

```
free
```

---

### Post by wadehel on 2006-11-26
total       used       free     shared    buffers     cached
Mem:        904768     538344     366424          0      77764     246228
-/+ buffers/cache:     214352     690416
Swap:            0          0          0


What i have to do to fix this "Unable to find swap signature" thing?

---

### Post by taurus on 2006-11-26
Can I have a look at your /etc/fstab because that's where you mount your swap and everything else?

```
cat /etc/fstab
```

---

### Post by wadehel on 2006-11-26
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1 -- converted during upgrade to edgy
UUID=17b57e0f-48ab-40b8-87ef-d3a82bcb5b2e / ext3 defaults,errors=remount-ro 0 1
# /dev/hda5 -- converted during upgrade to edgy
UUID=83748ee4-c390-43cb-a68c-0747326ec47a none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by taurus on 2006-11-26
> **wadehel said:**
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1 -- converted during upgrade to edgy
UUID=17b57e0f-48ab-40b8-87ef-d3a82bcb5b2e / ext3 defaults,errors=remount-ro 0 1
# /dev/hda5 -- converted during upgrade to edgy
UUID=83748ee4-c390-43cb-a68c-0747326ec47a none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
Not sure why but we will need to edit your /etc/fstab.  From a terminal, type

```
sudo cp /etc/fstab  /etc/fstab.bak <- make a backup copy...
gksudo gedit /etc/fstab
```
Now, remove this line

```

UUID=83748ee4-c390-43cb-a68c-0747326ec47a none swap sw 0 0

```
and replace it with

```

/dev/hda5   none   swap   sw   0   0

```
Save it and try to mount it again...

```

sudo mount -a
free

```

---

### Post by wadehel on 2006-11-26
I changed my fstab like this:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1 -- converted during upgrade to edgy
UUID=17b57e0f-48ab-40b8-87ef-d3a82bcb5b2e / ext3 defaults,errors=remount-ro 0 1
# /dev/hda5 -- converted during upgrade to edgy
/dev/hda5   none   swap   sw   0   0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

Tried to mount it again using sudo mount -a
but when enter free it still like this:

             total       used       free     shared    buffers     cached
Mem:        904768     404188     500580          0      13400     217332
-/+ buffers/cache:     173456     731312
Swap:            0          0          0

I tried to reboot and still have the same error.
Any other suggestion?

---

### Post by wadehel on 2006-11-26
FYI, maybe it will help, this *Unable to find swap signature* error happen after two possible cause (i dont know which):
1. After i tried to hibernate and fail
2. My friend plug an mandriva/winxp HDD and boot it as master on my PC.

---

### Post by taurus on 2006-11-26
Maybe you need to reformat it again!!!

```

sudo mkswap /dev/hda5
sudo swapon /dev/hda5
free

```

---

### Post by 56phil on 2006-11-26
I don't know about your friend's HDD, but suspend/hibernate can cause the UUID of your swap partition to change. Follow the link in post #9 of this thread. to resolve that issue.

---

### Post by wadehel on 2006-11-30
> **taurus said:**
> Maybe you need to reformat it again!!!

```

sudo mkswap /dev/hda5
sudo swapon /dev/hda5
free

```

Reformat?!?!! WTF!!!? :confused:

But then i follow your advice and OMG! it works!!! :D:D:D
Sorry the very late reply, no signal :P

Thankyou very much!

---

### Post by ivangotoy on 2006-12-23
i accidentally noticed my machine was acting tiny bit slower these days , now i saw my swap was gone - 1.6 gigs of swap missing!!! i rebooted and saw that message about the swap signature abscence.
i googled for it and i find that forum thread , my experience which i would like to share having no idea if it will work for all people is : 

1. Open the gnome partition manager (gparted)

2. Mark the swap partition (which in my case had become somehow unknown file system)

3. Right click on the partition for swap (usually the  smallest one) 

4. Choose "format to" and then  "swap" 

5. Right click on the newly made swap and choose the "swapon" command (first swapon made my machine freeze and i rebooted) so on my second "swapon" my swap was detected properly - i met no need confguring any files whatever .

my machine is : ubuntu edgy eft which is an upgraded dapper 32 bit variant ( at least the dapper was a clean install) 
i hope that might be helpful for someone in similar situation as was mine

---

### Post by Bosonator on 2006-12-26
> **taurus said:**
> Maybe you need to reformat it again!!!

```

sudo mkswap /dev/hda5
sudo swapon /dev/hda5
free

```

I tried this, and the first step (mkswap) seems to work fine, but the next one gives me the error 

```

swapon: /dev/hdb6: Device or resource busy

```

In case it helps, here is the output of "free"
```
             total       used       free     shared    buffers     cached
Mem:        516056     340356     175700          0      13844     206900
-/+ buffers/cache:     119612     396444
Swap:      1028120          0    1028120

```

and of "sudo fdisk -l"

```

Disk /dev/hda: 20.5 GB, 20525137920 bytes
255 heads, 63 sectors/track, 2495 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2495    20041056    7  HPFS/NTFS

Disk /dev/hdb: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1         973     7815591   83  Linux
/dev/hdb2             974        4870    31302652+   5  Extended
/dev/hdb5             974        4742    30274461   83  Linux
/dev/hdb6            4743        4870     1028128+  82  Linux swap / Solaris

```

---

### Post by kevinsun on 2007-03-14
> **56phil said:**
> if the UUID is already in fstab, then do:
```

sudo mkswap /dev/<swap partition path>
sudo swapon -va

```
**[SIZE="4"]CAUTION:[/SIZE]** mkswap is a dangerous command. Make sure that the *swap partition path* is right. 

mkswap will generate a new UUID that will need to be put in fstab.

Thanks a LOT LOT LOT....

It did work!

Kevin.

---

### Post by koldsco on 2008-06-03
Sorry to reply to an old item, but im hoping to save a future me some time.

So I started with a similer problem as those above, after a number of upgrade-dists, I had:

> 
# /dev/hda1 -- converted during upgrade to edgy
UUID=dc987bed-8a0c-4155-910c-e0f0e2c2b8ed /boot ext3 defaults 0 2
# /dev/hda2 -- converted during upgrade to edgy
#UUID=d47266cb-c9ad-4fab-b0af-b154e95c615f none swap sw 0 0


In my fstab, and my swap was just not working, free was 0, and swapon summary blank. I attempted to rebuild the swap fs, swapon and off, etc... all to no avail. 

my partitions were correct, and so it should be working, but when I treid to mkswap I would get:

> 
# mkswap /dev/sda2 
/dev/sda2: Device or resource busy


After thrashing about, I noticed that ubuntu had recognized my disk as a raid like device, and I had md and device mapper on (perhaps I had done this myself, this system has been around for a long time, well, in system years). So I did:

> ls -al /dev/mapper
brw-rw----  1 root disk 254,  7 2008-04-14 11:01 sda1
brw-rw----  1 root disk 254,  8 2008-06-02 19:38 sda2
brw-rw----  1 root disk 254,  0 2008-04-14 11:01 sda3
 

And so, I did the following:

> 
swapoff -a
mkswap /dev/mapper/sda2
<it returns good looking stff with uuid and such>
swapon -a
free | grep Swap
Swap:      2931852          0    2931852


bam!

I seem to recall that one should not do things directly with the /dev/mapper, or maybe thats something else like it, but I think its all good.

So, for the future me out there, looking through forums, I hope this helps.

---

