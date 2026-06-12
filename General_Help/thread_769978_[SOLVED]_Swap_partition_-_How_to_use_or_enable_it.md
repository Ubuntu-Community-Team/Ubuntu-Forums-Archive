---
title: "[SOLVED] Swap partition - How to use or enable it?"
date: 2008-04-27
forum: General Help
---

### Post by danial-aalee on 2008-04-27
Hi Everyone - Good Morning,
This is a re-post for the same issue (I started a thread a few days ago).

Before I installed 8.04, I had partitioned my 60G drive to have a boot and main partition for Ubuntu, another for extras and one more for SWAP (details are below).  No problems with installation, started using KDE  and pretty much all is working fine (to my little knowledge) - few frustrations here and there but I guess that is part of learning.

Here is my dilemma ...
When I check the system monitor, it shows '_no swap space available_' and has nothing in there. My safe assumption is swap is not turned on. The reason I thought about swap was that once in a while system would go very slow and then pick up. I am using AMD 64X2 3800 with a 2G ram. 2 HD (60G + 200G). Just a mediocre system - nothing fancy.

60G drive is the boot drive for Ubuntu and XP. That particular drive has:

1. primary partition for XP (25G).
2. primary partition for Ubuntu Ext3 (10G).
3. Extended Partition
3a. logical partition for Extra items Ext3 10G (not in use - not sure how to use it)
3b. logical partition for Swap Ext3 2G (apparently not in use and I am trying)

When I used '*sudo swapon /dev/sda6*' command it returns "**Invalid argument**" error. I also used '*top*' an dthat also shows swap = 0.  All I can think of that it may be because swap partition is under an extended partition. I sure do not know the truth but tying to know. Oh furthermore, I used '*fdisk -l*' to figure out device and it is sda6. That is what I tried to use with 'swapon.  By the way, when I was partitioning hard drive, I was unable to make a Primary partition of 2G and therefore I made it as a logical partition (that was done in Win XP environment).

Alright, so this is my story for the time being, any helping hand please...

Danial

---

### Post by confused57 on 2008-04-27
You might want to open a Konsole, post the output of:
```
kwrite /etc/fstab
```

```
sudo fdisk -l
```
the -l is a lowercase "L"

A swap partition needs to be formatted as "swap"...formatting the partition from Windows would be a problem.  If you formatted the partition from Windows, you might be able to use Gnome partition editor(System---Administration---Gnome Partition Editor) in the Ubuntu live cd to format it as swap...then you can set the proper mountpoint in your /etc/fstab.  Your "extra" partition could be formatted ext3 and mounted in /etc/fstab to be used as a data partition.

Added: The extra ext3 partition could also be used to move your home directory to a separate /home partition:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by danial-aalee on 2008-04-27
Thanks a lot for your help...

I am able to use gpart and format it to linux swap (it was formatted as ext3) and now I am able to see the swap partition in system monitor. Thanks a bunch for your help.  One more quick question... Should I go ahead and use gksudo gedit /etc/fstab and the device or is it already done now as I did a swapon from gpart?

Slowly but surely I am learning - Thanks to all the great people hangs out here... just to help and walk us newbies thru the muddy waters... 

Danial

---

### Post by tyler_roach on 2008-04-27
To see if your swap memory has been activated, run

top

from a command line. It will say how much memory you have at the top.

---

### Post by mali2297 on 2008-04-27
You probably need to edit /etc/fstab so that the system recognize the swap partition at boot.

Check the present UUID for the swap partition:
```

blkid /dev/sda6

```
That should give you an output with **UUID="some-numbers-and-letters"**. Use this when you add a line for the swap to /etc/fstab:
```

UUID=some-numbers-and-letters  none  swap  sw  0  0

```
Comment out any other line concerning swap (put a # in front).

If you get any problems, post your /etc/fstab and we will troubleshoot.

---

### Post by danial-aalee on 2008-04-27
Hi Everyone,

This is the latest copy of /etc/fstab (sorry not the best output format).
After my last night efforts, swap partition is there now but not in use now (it was when I turned on swapon from gparted) - so I made following changes.  I will reboot system and will get back to forum and post results.  Highlighted, bold text and extra lines are just to show the changes here in this post and not in actual fstab.  Please let me know if I had done wrong - 

Thanks a bunch for your help.... 
Danial

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=6dfd779e-99ab-4273-822c-c15654cbf3da /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=BA2092E22092A543 /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda2
UUID=1A901A3B901A1DB7 /media/hda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda5
UUID=82caae3a-557a-4ffe-8a25-7d4c0d064ffb /media/hda5     ext3    defaults        0       2
# /dev/hdc5
UUID=01C5B1E0C7899380 /media/hdc5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdc6
UUID=01C5B1E0CD332940 /media/hdc6     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdc7
UUID=01C5B1E0CFEAF640 /media/hdc7     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdc8
UUID=01C5B1E0D339D320 /media/hdc8     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdc9
UUID=D45CF9E25CF9BEF4 /media/hdc9     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1

[COLOR=Orange]*** this is where I made changes - and this line is added in this post only. ***  [/COLOR]
# /dev/hda6
#UUID=58dde756-80bf-49b9-a4d9-bdca6a5ca841 none            swap    sw              0       0
[COLOR=Orange]*** above line was originally there changed it to following line ***[/COLOR]

**[SIZE=2] UUID=58dde756-80bf-49b9-a4d9-bdca6a5ca841  swap    swap    defaults[/SIZE]**
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by confused57 on 2008-04-27
You might want to check the UUID's of all your partitions:
```
blkid
```
Mainly check if the UUID is correct for sda6(or hda6?).

Added:  Here's my swap entry in fstab(Dapper):
```
/dev/hda5       none            swap    sw              0       0
```

---

### Post by mali2297 on 2008-04-27
> **danial-aalee said:**
> 
[COLOR=Orange]*** this is where I made changes - and this line is added in this post only. ***  [/COLOR]
# /dev/hda6
#UUID=58dde756-80bf-49b9-a4d9-bdca6a5ca841 none            swap    sw              0       0
[COLOR=Orange]*** above line was originally there changed it to following line ***[/COLOR]

**[SIZE=2] UUID=58dde756-80bf-49b9-a4d9-bdca6a5ca841  swap    swap    defaults[/SIZE]**

Why have you changed **none swap sw 0 0** to **swap swap defaults**?
I think that you at least need to add the zeros.

---

### Post by danial-aalee on 2008-04-27
Hi There...

Okay, honestly, I don't know the exact format and these parameters - 
I will go ahead and changed it to: none swap sw 0 0
if you have a minute or two, can you tell me what is sw and 0 0 ?

I will post back in 5/10 minutes.

And YES - Thanks for your support and help.

Danial

---

### Post by mali2297 on 2008-04-27
Your options **swap swap defaults** would probably have been ok, but you need a total of six columns.

From [this source]("http://www.tuxfiles.org/linuxhelp/fstab.html"):
[QUOTE="How to edit and understand /etc/fstab"]
The 5th column in /etc/fstab is the dump option. Dump checks it and uses the number to decide if a filesystem should be backed up. If it's zero, dump will ignore that filesystem. If you take a look at the example fstab, you'll notice that the 5th column is zero in most cases.

The 6th column is a fsck option. fsck looks at the number in the 6th column to determine in which order the filesystems should be checked. If it's zero, fsck won't check the filesystem.
[/QUOTE]

---

### Post by danial-aalee on 2008-04-27
Thanks for explanation...

here I go again to change/modify and reboot....

will be back - hopefully with good results....

danial

---

### Post by danial-aalee on 2008-04-27
Thanks...

I guess now I am happy - all because of you guys.  After reboot, I am able to see swap is on in "top", and in "GPART" it show the option to turn it off (swapoff), so I guess it is runing it on startup now.

Now I will work on enabling my another partition **extra** formatted as ext3 ut not in use by system and thus my main partition for Ubuntu is getting to its max limit.  I remember one of you *[SIZE="3"]helping hands[/SIZE]* advised and sent a link to check out regarding that issue and alos to move home folder to that.  Little this evening, I will work on that.

last question for this thread... 
How do I closed this thread as completed/resolved/ happy puppy;) ???

[SIZE="3"]ONCE AGAIN, I THANK ALL OF YOU FOR YOUR PATIENCE, TIME AND GREAT HELP...[/SIZE]  :KS:KS:KS

Danial :guitar:

---

### Post by mali2297 on 2008-04-27
> **danial-aalee said:**
> 
last question for this thread... 
How do I closed this thread as completed/resolved/ happy puppy;) ???


Look under *Thread tools* at the top of the page.

---

