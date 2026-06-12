---
title: "Hardy 8.04:  USB flash drive no longer automounts"
date: 2008-06-07
forum: General Help
---

### Post by lamps06 on 2008-06-07
When I first upgraded to hardy a month or so ago I could plug in my USB flash drive and it automounted fine.  I have since installed updates as they have become available and I just realized that I can no longer automount my drive.  It shows up when I use lsusb and if I go to Computer I see it listed as ¨USB Drive¨ but if I attempt to open it I get the error message:

¨Unable to mount location.  Can´t mount file.¨

Does anyone know why this is happening?  I have also noticed that my DVD-RW drive no longer works.  Well, it does not mount discs.  I cannot explore the contents of the disc, but I can still use VLC to play DVDs...

This is extremely frustrating so if anyone knows of a solution please let me know.  Thank you!

---

### Post by lamps06 on 2008-06-09
Bump?

---

### Post by prshah on 2008-06-10
> **lamps06 said:**
> 
I just realized that I can no longer automount my drive.  
I have also noticed that my DVD-RW drive no longer works.  Well, it does not mount discs.


looks like your fstab entries for the dvd drive and usb drive have got mixed up; Plug in your usb drive, then open a terminal (Applications-Accessories-Terminal), then give the following commands and post the output here. ```

dmesg | tail
cat /etc/fstab
sudo fdisk -l

``` for clues.

---

### Post by lamps06 on 2008-06-10
Here is the output of those three commands:

```
mateo@Athlon:~$ dmesg | tail
[  628.457329] sd 2:0:0:0: [sdd] Write Protect is off
[  628.457336] sd 2:0:0:0: [sdd] Mode Sense: 00 00 00 00
[  628.457340] sd 2:0:0:0: [sdd] Assuming drive cache: write through
[  628.458946] sd 2:0:0:0: [sdd] 4096000 512-byte hardware sectors (2097 MB)
[  628.459572] sd 2:0:0:0: [sdd] Write Protect is off
[  628.459578] sd 2:0:0:0: [sdd] Mode Sense: 00 00 00 00
[  628.459581] sd 2:0:0:0: [sdd] Assuming drive cache: write through
[  628.459587]  sdd: sdd1
[  628.535646] sd 2:0:0:0: [sdd] Attached SCSI removable disk
[  628.535712] sd 2:0:0:0: Attached scsi generic sg4 type 0
mateo@Athlon:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=76d54b02-d664-4962-be61-031be1f5495e /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=c797da93-e0fb-45b1-b703-25c2dcc930ff none            swap    sw              0       0
/dev/scd       /media/cdrom   udf,iso9660 user,noauto,exec,utf8 0       0

# /dev/sdb1
UUID=E8909F03909ED800
/dev/sdb1	/media/Media_Drive	ntfs	defaults 0 0

# /dev/sdc1
UUID=BAD0CD75D0CD3901
/dev/sdc1	/media/WinXP	ntfs	defaults	0	0
mateo@Athlon:~$ sudo fdisk -l
[sudo] password for mateo: 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000884cf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9327    74919096   83  Linux
/dev/sda2            9328        9729     3229065    5  Extended
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris

Disk /dev/sdb: 100.2 GB, 100256292864 bytes
255 heads, 63 sectors/track, 12188 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x004d212e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       12188    97900078+   7  HPFS/NTFS

Disk /dev/sdc: 30.7 GB, 30758289408 bytes
255 heads, 63 sectors/track, 3739 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x20202020

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        3738    30025453+   7  HPFS/NTFS

Disk /dev/sdd: 2097 MB, 2097152000 bytes
255 heads, 63 sectors/track, 254 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x91f72d24

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1         255     2047968+   b  W95 FAT32
Partition 1 has different physical/logical endings:
     phys=(253, 254, 63) logical=(254, 245, 55)

```


The /dev/sdd/ drive is my USB flash drive.  I do not include it in my fstab.  Any ideas as to what is going on?

---

### Post by lamps06 on 2008-06-11
For what it was worth I was able to create a /media/USB1 directory and manually mount the drive there using

```

sudo mount -t vfat /dev/sdd /media/USB1

```

But this is a pain.  Before Ubuntu would automount USB devices, I do not want to manually mount them...

---

### Post by punong_bisyonaryo on 2008-07-17
I'm currently having this same problem. I can mount manually, but for some weird reason it just stopped automounting this afternoon.

---

### Post by computer_freak_8 on 2008-07-18
I am having the opposite problem. I want to temporarily turn off automounting so I can write my partition changes to disk. 

In Ubuntu 7.10, there was an easy way to do this. You could go to System, Preferences, Removable Drives and Media. Now, in Ubuntu 8.04, the options for automounting are no longer there. 

Does anyone know where they went?

---

### Post by Seti on 2008-07-18
Same problem here, and I just used the same solution as you. Would be nice to know why this happened.

---

### Post by Seti on 2008-07-19
Looks like a reboot fixed this issue, when inserting my RCA Lyra MP3 player, Hardy automatically mounted it and opened Rhythmbox. Back to normal. I'm still curious to know what happened here, although I am way to busy to dedicate a lot of time to figuring it out.

---

### Post by punong_bisyonaryo on 2008-07-20
> **punong_bisyonaryo said:**
> I'm currently having this same problem. I can mount manually, but for some weird reason it just stopped automounting this afternoon.

Just found out something, which might be of a clue to some more experienced user to help us out: It seems that although my computre no longer auto-mounts, the drive that I plugged in will still appear in the Places in Nautilus. Clicking on it then mounts it, and I can get back to work without CLI mounting. Still curious how to put it back the way it was though.

---

### Post by lamps06 on 2008-08-04
Has anyone discovered a solution for the automount issue in Hardy Heron?  It is extremely frustrating.  I am STILL unable to get my USB drive to automount.  I can mount it manually but then I am stuck with read only access which limits what I can do with the drive.

It is disappointing to see that there has not been a fix for this issue yet.  I have seen many different posts regarding the same issue and yet there is no definitive solution.  I have tried multiple different "quick fixes" that seem to work for some people but none of these have worked for me.  I seriously hope the Ubuntu teams resolves this issue in 8.10.  I love Ubuntu, but if it lacks proper USB support it is almost worthless.

Is anyone else able to offer any insight into what might be causing this problem or what I can do to fix it?  This only started happening after I installed some updates back in May/June.  Thanks.

---

### Post by beanhead on 2008-08-04
Some times it depends on the usb drive like cruiser micro has known issues and I have kinkston drive witch read and write with no problems at all. what kind of drive are you using? also is it to hard to use sudo umount /dev/sda1, little more time the comand line makes life soo good.

---

### Post by prshah on 2008-08-04
> **lamps06 said:**
> I can mount it manually but then I am stuck with read only access which limits what I can do with the drive.


> **beanhead said:**
>  also is it to hard to use sudo umount /dev/sda1, 

While I've never faced this problem, here's an easier way to mount without worrying about fstab, permissions, etc:

```

sudo apt-get install pmount
#now, no need for sudo!
#replace /dev/sdd1 with your actual device name for the usb pen drive- 
#see dmesg after plugging in the pen.
pmount /dev/sdd1

```

pmount will automatically detect the filesystem type and mount the device, create the relevant folder in /media/, set umask permissions, etc.

It is still a manual process to mount/unmount, but hopefully a little easier.

---

### Post by punong_bisyonaryo on 2008-08-05
I have a Kingston and used to have a Cruzer Micro. The main thing is it USED TO work. The problem is not that it's too hard to sudo umount, the problem is that it's broken. It doesn't matter how many workarounds we can find, heck I have one. The fact still remains...it's broken.

I agree that a little more time with the command line is good, but having to umount (or even pmount) every time I plug in a USB (and I plug in my CF card reader all the time) gets really tiring. I'm resigned to a fredsh install but I won't be able to reinstall Ubuntu until I can buy an external DVD drive (my Kohjinsha doesn't have one and I'm on overseas assignment). I wish we could find a solution for this.

---

### Post by prshah on 2008-08-05
> **punong_bisyonaryo said:**
> 
 It doesn't matter how many workarounds we can find, heck I have one. The fact still remains...it's broken.

I wish we could find a solution for this.

Is gnome-volume-manager running? That's what controls auto-mounting. Try this```
ps -e | grep volume
``` If it shows something, then try killing the process ```
sudo killall gnome-volume-manager
``` Now, try manually restarting it, from terminal```
gnome-volume-manager
``` Now plug in your USB device and see if it automounts; if it doesn't, post back error messages displayed. 

If automounting now works, it will again stop when you close the terminal; in this case, press Alt+F2 and give the same command again. You can also add it to your startup sessions if you like.

---

### Post by lamps06 on 2008-08-05
I am in agreement with punong_bisyonaryo.  My Transcend Jetflash TS2GJF110 2GB drive USED to work when I first upgraded to Hardy.  It also worked flawlessly in Gutsy.  It was only after I installed some update to Hardy (still not sure which one) that it ceased to function.  So obviously something changed that is causing a problem with my drive.

prshah, I appreciate your suggestion of using pmount but I am hoping someone with the Ubuntu team will acknowledge this problem and create a fix for it.  I will try checking if gnome-volume-manager is running when I get home tonight and report back.  Thanks everyone.

---

### Post by punong_bisyonaryo on 2008-08-05
prshah, thanks for all your support. Funny, I never would have imagined that the volume-manager controlled automounting.:) I will give this a try when I get home tonight. And I'll also look if this problem has already been reported in Launchpad, so we can post a bug report.

---

### Post by punong_bisyonaryo on 2008-08-06
I was able to do what you suggested, except I had to run gnome-volume-manager from /usr/lib/gnome-volume-manager/ but after that, still the same. And I was hoping for error messages but I got none. I'm thinking that either the gnome-volume-manager is whacked or HAL events aren't being created, but I woudln't know.

---

### Post by prshah on 2008-08-06
> **punong_bisyonaryo said:**
> I'm thinking that either the gnome-volume-manager is whacked or HAL events aren't being created

You can try to re-install gnome-volume-manager and pmount (these two are all that is responsible for drive automounting).```
sudo apt-get install --reinstall gnome-volume-manager pmount
``` It's a long shot, but it's worked in some cases; give it a try.

---

### Post by lamps06 on 2008-08-07
My experience is identical to that of punong_bisyonaryo.  My volume manager was running so I killed it and restarted.  My drive still did not mount and there were no error messages.  I tried reinstalling gnome volume manager but I still have the same experience.  I installed pmount and this did not help either.  What is going on?

---

### Post by lamps06 on 2008-08-07
I am not sure if this helps, but I have also had problems mounting discs in my DVDRW drive ever since I started having problems with my USB drives mounting.

---

### Post by prshah on 2008-08-07
> **lamps06 said:**
> My experience is identical to that of punong_bisyonaryo.  I installed pmount and this did not help either.  

Can both of you open a terminal, plug in the usb pen, and then give the following command, and post it's output?```
sleep 10 && dmesg | tail
``` This command will wait 10 seconds before executing, so don't think your computer is jammed!

---

### Post by Julianus on 2008-08-08
> **lamps06 said:**
> I am not sure if this helps, but I have also had problems mounting discs in my DVDRW drive ever since I started having problems with my USB drives mounting.

Same thing here: DVD/CDs are also not automounted anymore.

The USB, however, is detected by the system - fdisk -l shows me it's there (still have not tried with the DVD).

I also noticed the following: network-manager now takes much longer (say 20-30 secs) before asking me the password to connect to the WLAN after entering the KDesktop.

Sometimes, however, it still does it when expected to, a few seconds after entering KDesktop. When this happens, the USB and DVD are automounted without problem.

---

### Post by lamps06 on 2008-08-09
Here are the results of the command:

```

xxx@CPU:~$ sleep 10 && dmesg | tail
[ 6222.472036] sd 2:0:0:0: [sdd] Write Protect is off
[ 6222.472048] sd 2:0:0:0: [sdd] Mode Sense: 00 00 00 00
[ 6222.472052] sd 2:0:0:0: [sdd] Assuming drive cache: write through
[ 6222.473625] sd 2:0:0:0: [sdd] 4096000 512-byte hardware sectors (2097 MB)
[ 6222.474252] sd 2:0:0:0: [sdd] Write Protect is off
[ 6222.474258] sd 2:0:0:0: [sdd] Mode Sense: 00 00 00 00
[ 6222.474262] sd 2:0:0:0: [sdd] Assuming drive cache: write through
[ 6222.474275]  sdd: sdd1
[ 6222.550319] sd 2:0:0:0: [sdd] Attached SCSI removable disk
[ 6222.550387] sd 2:0:0:0: Attached scsi generic sg4 type 0

```

---

### Post by prshah on 2008-08-09
> **lamps06 said:**
> 
```

xxx@CPU:~$ sleep 10 && dmesg | tail
[ 6222.472036] sd 2:0:0:0: [sdd] Write Protect is off
[ 6222.472048] sd 2:0:0:0: [sdd] Mode Sense: 00 00 00 00
[ 6222.472052] sd 2:0:0:0: [sdd] Assuming drive cache: write through
[ 6222.473625] sd 2:0:0:0: [sdd] 4096000 512-byte hardware sectors (2097 MB)
[ 6222.474252] sd 2:0:0:0: [sdd] Write Protect is off
[ 6222.474258] sd 2:0:0:0: [sdd] Mode Sense: 00 00 00 00
[ 6222.474262] sd 2:0:0:0: [sdd] Assuming drive cache: write through
[ 6222.474275]  sdd: sdd1
[ 6222.550319] sd 2:0:0:0: [sdd] Attached SCSI removable disk
[ 6222.550387] sd 2:0:0:0: Attached scsi generic sg4 type 0

```

Why is everything repeated twice (as though you've plugged it in twice?)

OK everything looks fine here; other points to consider:

a) I assume that you are members of the group plugdev```
groups `whoami`

``` (or just "groups" it's all the same ;) )

b) Tried reinstalling hal? ```
sudo apt-get install --reinstall libhal1 libhal-storage1
```

c) Can you spot your pendrive entry in gconf-editor? Alt+F2, then ```
gconf-editor
``` press enter, then navigate to /system/storage; if you can find an entry for your pendrive, remove it. Otherwise, post the contents of /system/storage/default_options/vfat (or whichever file system you use) for a look-see.

---

### Post by lamps06 on 2008-08-09
> 
a) I assume that you are members of the group plugdev


Yes, I checked and I am a member of the plugdev group.

> 
b) Tried reinstalling hal?
Code:
```
sudo apt-get install --reinstall libhal1 libhal-storage1
```


I tried reinstalling both of those packages and this did not have any effect.

> 
c) Can you spot your pendrive entry in gconf-editor? Alt+F2, then
Code:

```
gconf-editor
```

press enter, then navigate to /system/storage; if you can find an entry for your pendrive, remove it. Otherwise, post the contents of /system/storage/default_options/vfat (or whichever file system you use) for a look-see.


My flash drive was not in gconf-editor.  I use vfat, and here are the contents of my /system/storage/default_options/vfat:

```

shortname=mixed
uid=
utf8
umask=077
exec
flush
usefree

```


Thanks a lot, prshah.  I really appreciate you taking the time to troubleshoot this with me.  No one else has been of much help.

---

### Post by punong_bisyonaryo on 2008-08-09
Output of dmesg | tail
```
[ 2783.629007] sd 5:0:0:0: [sdb] Write Protect is off
[ 2783.629021] sd 5:0:0:0: [sdb] Mode Sense: 23 00 00 00
[ 2783.629028] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 2783.631132] sd 5:0:0:0: [sdb] 312581808 512-byte hardware sectors (160042 MB)
[ 2783.632118] sd 5:0:0:0: [sdb] Write Protect is off
[ 2783.632131] sd 5:0:0:0: [sdb] Mode Sense: 23 00 00 00
[ 2783.632137] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 2783.632151]  sdb: sdb1 sdb4
[ 2783.659742] sd 5:0:0:0: [sdb] Attached SCSI disk
[ 2783.659923] sd 5:0:0:0: Attached scsi generic sg1 type 0
```

Same output before and after reinstall libhal

As for my gconf-editor, I have the following options. I noted I didn't have the usefree option.
```
shortname=mixed,uid=,utf8,umask=077,exec,flush
```

BTW, this happens even to my external ext3 drives, not just vfat.

Thanks for all your hard work! Even if we can't solve this, your valiant effort is already much appreciated!

---

### Post by prshah on 2008-08-10
> **lamps06 said:**
> 
...
```

...
usefree

```
...

This has been a known problem; however, it may/may not be your problem. From gconf-editor, try removing this, and then try your pendrive. AFAIK (ATNVF), a restart is not necessary, but just restart to be on the safer side.

[quote=punong_bisyonaryo]
I noted I didn't have the usefree option.
[/quote]

You've not confirmed that you're a member of group plugdev. Please check. And for you, try _adding_ the usefree option. (Though actually, usefree has been a bit of a problem in some cases, from what I have read).

In case the two of you have not yet caught on, I'm just trying (harmless) experiments in the hope of getting things to work. There are (too) many complaints about this issue, and since I don't have this problem, I cannot troubleshoot it myself; you two are my scapegoats ;)

I'm working on this so that I will know what to do/check if I run into the same issues. Your thanks are noted and appreciated, but unnecessary, and, actually, reciprocated.

---

### Post by rjwboys on 2008-08-10
Im haveing this problem also the flash drive appears in computer but i click on it and it does nothing, no error, nothing that can tell me whats going on

---

### Post by punong_bisyonaryo on 2008-08-11
I confirmed, I'm a member of plugdev. Tried putting usefree, but after I did that, clicking on the drive from Computer to mount it started reporting errors, like invalid mount option or someting. And it didn't solve the problem either. I tried a complete remove of hal (which also removed network-manager and power-manager among others) and reinstalled it. Still no go. Still searching for other experiments to figure this out.

---

### Post by lamps06 on 2008-08-12
> 
This has been a known problem; however, it may/may not be your problem. From gconf-editor, try removing this, and then try your pendrive. AFAIK (ATNVF), a restart is not necessary, but just restart to be on the safer side.


I removed the usefree option, restarted and still no luck...

---

### Post by punong_bisyonaryo on 2008-08-15
What the...it just worked! I'm pretty sure I didn't install any updates. In fact, it wasn't working just this morning and afternoon! Quick ask me some questions while I *try* to get some more info.

---

### Post by punong_bisyonaryo on 2008-08-15
Output of sleep 10 && dmesg | tail is still the same:
```
[32388.813550] sd 6:0:0:0: [sdb] Write Protect is off
[32388.813564] sd 6:0:0:0: [sdb] Mode Sense: 23 00 00 00
[32388.813571] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[32388.815114] sd 6:0:0:0: [sdb] 312581808 512-byte hardware sectors (160042 MB)
[32388.815987] sd 6:0:0:0: [sdb] Write Protect is off
[32388.815999] sd 6:0:0:0: [sdb] Mode Sense: 23 00 00 00
[32388.816005] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[32388.816018]  sdb: sdb1 sdb4
[32388.843839] sd 6:0:0:0: [sdb] Attached SCSI disk
[32388.843941] sd 6:0:0:0: Attached scsi generic sg1 type 0
```

Gconf-editor is also the same.

Although, I remember that I did play around with my advanced compiz settings today. And that's the only thing I changed. Weird.

I'm just grasping here, but could you turn off "Animations" under effects, enabling Minimize instead? Or rather, check if BOTH Animations and Minimize Effect are both checked. That's supposed to be impossible, but for some reason, I recall they were both checked before.

I'm also attaching my compiz profile just in case. Try loading it and see how it goes.

---

### Post by lamps06 on 2008-08-15
Wow, congrats!  I will give your suggestions a try this weekend and let you know what happens.  Fingers crossed...  Thank you!

---

### Post by neur0 on 2008-08-17
Had the exact same problem, and restart fixed it.
Hope it stays fixed, as the log says nothing about what happened - hard to diagnose.

---

### Post by lamps06 on 2008-08-18
Alas, I tried loading your compiz settings, punong_bisyonaryo, but it did not change anything for me. :(  I even restarted, but still nothing.

---

### Post by lamps06 on 2008-08-18
Also, I did have some success in getting my DVD drive to mount.  Another user pointed out that in my fstab I had not numbered it.  I used lshw -C disk and discovered that it needed a "0" at the end, ie /dev/scd0 instead of /dev/scd.  I made this one small change and now my DVD drive mounts perfectly.

Now if only it were that simple for my flash drive.

---

### Post by XPuntu on 2008-08-18
I had the same problems with my USB external drive. The only thing I could think of that had changed recently is that I installed virtualbox using this guide:

[http://www.ubuntugeek.com/howto-install-virtualbox-16-in-ubuntu-804hardy-heron-including-usb-support.html]("http://www.ubuntugeek.com/howto-install-virtualbox-16-in-ubuntu-804hardy-heron-including-usb-support.html")

There's a section about enabling USB support in mountdevsubfs.sh 

I reversed the changes, rebooted and now my USB drive is automounting. Does this help anyone?

---

### Post by lamps06 on 2008-08-19
XPuntu, I tried your suggestion but this did not help either.  Thanks, though!

---

### Post by lockettowl on 2008-08-19
OK, I've been having basically the same problems, but I'm much less tech-savvy than most, if not all, who have posted in this thread. I have tried to follow the advice posted so far, but have gotten no where.

I've had troubles with two USB devices - my flash drive and my digital camera. Here's my situation:
1. My flash drive worked just fine for the first month or two that I had Ubuntu (I have 8.04). Then, while it was plugged in, it would just disappear. Now, when I plug it in, it's usually not detected at all.
2. Likewise, my camera would work just fine when I first got it, even when my flash drive wasn't working correctly. Then, It stopped connecting as it should, but I could still import pictures using f-spot. Now, it isn't being detected at all.
3. Both devises work in other (non-Ubunut) computers.

---

### Post by cleopete on 2008-08-20
Hi,

Add me to the pile.  Pretty much the same story, I had working USB automount after I installed Hardy (in April), but some weeks ago I lost it.

I'm pretty new to Ubuntu, and as such I've been installing and uninstalling packages all over the place just to play, so I have no idea what particularly irresponsible thing I might have done to cause this, judging by the forums, it may not even be my fault.

Like many others in this boat, if I boot with the drive in it works, until I unplug it.  I've also noticed that Nautilus lists it as "USB Drive" instead of the custom label every other comp sees.

I've tried all of prshaws suggestions, here's the output:
```

david@TechieBoy2:~$ dmesg | tail
[  422.164610] sd 2:0:0:0: [sdb] Write Protect is off
[  422.164613] sd 2:0:0:0: [sdb] Mode Sense: 23 00 00 00
[  422.164616] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  422.165928] sd 2:0:0:0: [sdb] 7856128 512-byte hardware sectors (4022 MB)
[  422.166240] sd 2:0:0:0: [sdb] Write Protect is off
[  422.166245] sd 2:0:0:0: [sdb] Mode Sense: 23 00 00 00
[  422.166249] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  422.166256]  sdb: sdb1
[  422.223798] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[  422.223859] sd 2:0:0:0: Attached scsi generic sg1 type 0
david@TechieBoy2:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                    0  0  
# /dev/sda5
UUID=e672f7aa-18b1-4f59-a42e-e96388a50976  /              ext3         relatime,errors=remount-ro  0  1  
# /dev/sda6
UUID=435cf3c4-f81e-4884-9b4e-0b37331ed011  none           swap         sw                          0  0  
/dev/hda                                   /media/cdrom0  udf,iso9660  user,noauto,exec,utf8       0  0  

//netbiosname/sharename    
/techieboy/E$        cifs    credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
/dev/sdb1                                  /media/sdb1    vfat         users,user                  0  0  
david@TechieBoy2:~$ sudo fdisk -l
[sudo] password for david: 

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb553097a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1147     9213246   12  Compaq diagnostics
/dev/sda2   *        1148        7889    54155115    6  FAT16
/dev/sda3            7890       11248    26978072    7  HPFS/NTFS
/dev/sda4           11249       14593    26868712+   5  Extended
/dev/sda5           11249       14449    25712001   83  Linux
/dev/sda6           14450       14593     1156648+  82  Linux swap / Solaris

Disk /dev/sdb: 4022 MB, 4022337536 bytes
29 heads, 28 sectors/track, 9675 cylinders
Units = cylinders of 812 * 512 = 415744 bytes
Disk identifier: 0x04030201

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9676     3928060    b  W95 FAT32
david@TechieBoy2:~$ sleep 10 && dmesg | tail
[  926.577548] sd 3:0:0:0: [sdb] Write Protect is off
[  926.577552] sd 3:0:0:0: [sdb] Mode Sense: 23 00 00 00
[  926.577555] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[  926.578923] sd 3:0:0:0: [sdb] 7856128 512-byte hardware sectors (4022 MB)
[  926.579295] sd 3:0:0:0: [sdb] Write Protect is off
[  926.579299] sd 3:0:0:0: [sdb] Mode Sense: 23 00 00 00
[  926.579301] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[  926.579312]  sdb: sdb1
[  926.637104] sd 3:0:0:0: [sdb] Attached SCSI removable disk
[  926.637167] sd 3:0:0:0: Attached scsi generic sg1 type 0
david@TechieBoy2:~$ 
```


I don't have any issues with DVD drive mounting, I haven't tried an external HD.

When I tried to restart the gnome-volume-manager, it came back with "command unknown" when I tried to install it, it said it was already installed.

I didn't have usefree listed in in gconf-editor, and adding it didn't do squat.  Incidentally uid=1000, which I noticed was different from the others who had a big blank there.

I'm probably going to reinstall soon anyway (for other reasons) but it would be oh so cool to figure out why this is happening- for future reference.

Thanks

---

### Post by cleopete on 2008-08-22
> **XPuntu said:**
> I had the same problems with my USB external drive. The only thing I could think of that had changed recently is that I installed virtualbox using this guide:

[http://www.ubuntugeek.com/howto-install-virtualbox-16-in-ubuntu-804hardy-heron-including-usb-support.html]("http://www.ubuntugeek.com/howto-install-virtualbox-16-in-ubuntu-804hardy-heron-including-usb-support.html")

There's a section about enabling USB support in mountdevsubfs.sh 

I reversed the changes, rebooted and now my USB drive is automounting. Does this help anyone?

I have vbox installed on another Hardy machine.  No problems with that one.  You do necessarily lose the device on the host when usb passthrough is enabled, but you get it back when you close the vm.

---

### Post by prshah on 2008-08-22
In addition to my previous suggestions of [[pmount]]("http://ubuntuforums.org/showpost.php?p=5525706&postcount=13"), [[gnome-volume-manager]]("http://ubuntuforums.org/showpost.php?p=5528591&postcount=15"), [[reinstall gvm & pm]]("http://ubuntuforums.org/showpost.php?p=5535714&postcount=19") and [[plugdev/hal]]("http://ubuntuforums.org/showpost.php?p=5554694&postcount=25"), I'd suggest you also try:

a) Press Alt+F2,```
gconf-editor
```
b) navigate to /apps/nautilus/preferences
c) ensure the following are ticked (checked, enabled) "media_autmount", "media_automount_open"
d) ensure the the following are unticked (unchecked, disabled) "media_autorun_never"

---

### Post by lamps06 on 2008-08-23
> c) ensure the following are ticked (checked, enabled) "media_autmount", "media_automount_open"
d) ensure the the following are unticked (unchecked, disabled) "media_autorun_never" 

Alas, I tried this and still no luck.

---

### Post by BLTicklemonster on 2008-08-23
> **punong_bisyonaryo said:**
> Just found out something, which might be of a clue to some more experienced user to help us out: It seems that although my computre no longer auto-mounts, the drive that I plugged in will still appear in the Places in Nautilus. Clicking on it then mounts it, and I can get back to work without CLI mounting. Still curious how to put it back the way it was though.

I think it's an update issue. I used to could click on my drives in nautilus and it would create icons on my desktop, and I could plug in my digital camera or a usb stick and icons would be created on my desktop, but not now since I have done several updates. Also, my lan does not behave as it did before. I had it set to allow access to and from the XP boxes here without a password, but now they all ask for passwords regardless.

Also, I tried the gnome-volume-manager trick mentioned above, and here's what I got:

```
bill@bill-desktop:~$ ps -e | grep volume
```

It found nothing.
```

bill@bill-desktop:~$ gnome-volume-manager
bash: gnome-volume-manager: command not found
```

Okay, fine then:
```

bill@bill-desktop:~$ sudo aptitude install gnome-volume-manager
[sudo] password for bill: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
bill@bill-desktop:~$ 



```


Ooooookay. 

I guess I'll try a reboot and see what happens.

---

### Post by BLTicklemonster on 2008-08-23
Just restarted, and nope, nothing comes up. Also, when I dangerously turn off my camera without unmounting it in nautilus, I'm not spanked with a pop up telling me how dangerous my decision was to do that.

Looks to me like an update broke something, ya'll.

---

### Post by BLTicklemonster on 2008-08-23
I looked in system monitor, and saw no gnome-volume-manager, so I looked in sessions and it was under volume manager. So I decided to play around.

In sessions, volume manager, edit: 

the command was this:

/usr/lib/gnome-volume-manager/gnome-volume-manager --sm-disable

I removed --sm-disable and restarted.

In system monitor I now have a ton of gvfsd-* items duplicated, -daemon, -burn, -trash, -fuse-daemon, as well as 3 gvfsd entries, but no entry for gnome-volume-manager itself.

perhaps the edit in sessions would be --sm-enable or something?

Well, --sm-enable didn't do anything, so I put it back, and as it turns out, this had nothing to do with all the gvfsd entries at all.

I'm not rebooting when I do this, I'm just pressing ctrl+alt+f1 and entering sudo /etc/init.d/gdm stop then start. 

Anyway, what's up with gnome-volume-manager, it's there in synaptic as installed, and I even reinstalled it and rebooted before trying all of the above.

---

### Post by Jonie on 2008-08-23
Lots of posts, but perhaps a drive that wouldn't automount needs just a bit of dosfsck?

---

### Post by BLTicklemonster on 2008-08-23
Humor me, please? :)

*how does one do this marvelous thing?

Bah, install pysdm, set all drives, then install ubuntu tweak [http://ubuntu-tweak.com/](http://ubuntu-tweak.com/) then run it, navigate to desktop> desktop, show mounted volumes on desktop.

---

### Post by punong_bisyonaryo on 2008-08-23
> **Jonie said:**
> Lots of posts, but perhaps a drive that wouldn't automount needs just a bit of dosfsck?

I don't see how that would fix the problem. The drives are perfectly fine. The system just doesn't seem to want to automount. And we're still without a clue.

---

### Post by Jonie on 2008-08-24
Ok, it was just for the record. Windows is much more tolerant (or to be more specific ignorant) about errors. Once upon a time I even filed a bug on lauchpad regarding USB enclosure, finally it became evident that it's been the hardware which was unstable and slowly dying, but Windows mounted it quite happily and didn't complain. 

Anyway, chcecking if FAT isn't damaged is first to go is such a case. There was a bug in the early Hardy, too, such that /media mount points were not cleared upon unmounting and that brought some confusion into the use of removables. Check if /media is not populated with garbage, if so remove nonsense entries.

---

### Post by cleopete on 2008-08-25
> b) navigate to /apps/nautilus/preferences
c) ensure the following are ticked (checked, enabled) "media_autmount", "media_automount_open"
d) ensure the the following are unticked (unchecked, disabled) "media_autorun_never" 


> Check if /media is not populated with garbage, if so remove nonsense entries. 


My Nautilus prefs were right as rain and my /media folder is more sparse than Hwy. 50.

---

### Post by lamps06 on 2008-08-26
There is nothing in my /media folder that should not be there. 

I ran dosfsck /dev/sdd to check my flash drive and this is the output that was returned:

```
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
Currently, only 1 or 2 FATs are supported, not 191.
```

What does this mean?

---

### Post by punong_bisyonaryo on 2008-08-26
So were mine (and still are).

---

### Post by prshah on 2008-08-26
> **lamps06 said:**
> 
```
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
Currently, only 1 or 2 FATs are supported, not 191.
```


Means something is wrong. 191 FATs!?!!? Did you unmount /dev/sdd before running the fsck? (You must have, otherwise it would have given a warning...); maybe you should reformat the usb stick and check again.

---

### Post by Jonie on 2008-08-26
You tried to check the whole disk, not the proper partition. Launch sudo dosfsck /dev/sdd1, or whatever letter it has.

---

### Post by Jonie on 2008-08-26
BTW, pendrive can be either a superfloppy (no disklabel, filesystem directly on a device) or usb hard disk (partitioned as usual). Ones of the first type are now rare, unless you format it this way (f.ex. to boot with an old bios). In first case filesystem is on, say, /dev/sdd, in the other on /dev/sdd1. You can tell which one you got from fdisk -l /dev/sdd. Superfloppy will report loop disklabel, thus no disklabel.

---

### Post by mman426 on 2008-08-27
Hey, I have the same problem as most of you, and have tried just about everything suggested. The only thing of interest that I have noticed is that in my case, only sdb will not mount automatically (it shows up in computer as USB Drive, but won't mount). If I plug in a usb drive it does not mount, but if I plug in another usb drive, it registers as sdc and will automatically mount with a custom label. On a related note, none of my media (CD's and USB) will show up on my desktop when inserted. They used to show up and open a window, but now nothing shows up, not even for the USB drive sdc which automounts and shows up under computer.

---

### Post by mman426 on 2008-08-27
I just fixed my sdb problem by removing the entry in fstab for sdb that I had created earlier. Now sdb automatically mounts and shows up in computer; however, still none of my media automatically shows up on the desktop like it used to.

---

### Post by mman426 on 2008-08-27
nevermind that thing about fstab, that didn't fix the problem, I just figured out that if I plug in a USB as sdb it doesn't work, then I plug in a USB as sdc and it works, then I remove sdb and plug it back in and it works. This is a fix, but not at all what I would like.

---

### Post by lamps06 on 2008-08-27
Here is the ouput of my dosfsck:

```
mateo@Athlon:~$ sudo dosfsck /dev/sdd1
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
/dev/sdd1: 136 files, 103065/510989 clusters
```

---

### Post by punong_bisyonaryo on 2008-08-28
> **mman426 said:**
> nevermind that thing about fstab, that didn't fix the problem, I just figured out that if I plug in a USB as sdb it doesn't work, then I plug in a USB as sdc and it works, then I remove sdb and plug it back in and it works. This is a fix, but not at all what I would like.

Your case is interesting, and I think may lead to some clues if probed further. However, I think most people here have drives that don't work no matter what, so you may be the only one who can dig deeper on this. Anyway, be sure to share whatever you find out.

---

### Post by mman426 on 2008-08-28
Mine actually started working again last night. It suddenly worked after I used the trick I mentioned to make sdb work and then made a live usb on sdb. After that everything seemed to work fine, except my media still doesn't pop up on my desktop when inserted. I think all my problems originally stemmed from a live usb I was trying to create and the process was interrupted. I don't think I would be much help to everyone else anyway, I am still a n00b with linux.

---

### Post by maxonline on 2008-08-29
I have to say that I'm running in the same lamps06's status. 
The nice news is that this is true only in one of my two pc with different hardware but identical software configuration ( really identical !! ghosted ) :confused:

Of course, I've already tried more or less everything suggested ( here and more ) and the buggy one with different s.o. rel. ( like Gusty or M$ too ) work without problem.


p.s. with "gnome-mount -d" ( e.g. gnome-mount -d /dev/sde4 ) I can mount USB device without problem and after then, and only up to next umount, I see the right name in Place->Computer ( not the generic USB Drive ) and I can use it in nautilus as before.

max

---

### Post by prshah on 2008-08-30
> **prshah said:**
> In addition to my previous suggestions of [[pmount]]("http://ubuntuforums.org/showpost.php?p=5525706&postcount=13"), [[gnome-volume-manager]]("http://ubuntuforums.org/showpost.php?p=5528591&postcount=15"), [[reinstall gvm & pm]]("http://ubuntuforums.org/showpost.php?p=5535714&postcount=19") and [[plugdev/hal]]("http://ubuntuforums.org/showpost.php?p=5554694&postcount=25"), I'd suggest you also try:

a) Press Alt+F2,```
gconf-editor
```
b) navigate to /apps/nautilus/preferences
c) ensure the following are ticked (checked, enabled) "media_autmount", "media_automount_open"
d) ensure the the following are unticked (unchecked, disabled) "media_autorun_never"

One more new suggestion: check if the gnome-vfs-daemon is running; 
```
ps -e | grep -i vfs-da

```

---

### Post by maxonline on 2008-08-30
FYI in my two pc I didn't find gnome-vfs-daemon running.

max

---

### Post by MentalNotes on 2008-08-30
Regarding finding the automounting options, they've been moved to the Nautilus preferences. You can find them by opening nautilus, going to Edit -> Preferences and clicking on the Media tab. It had me a lost for a bit when I upgraded to Hardy too.

---

### Post by lamps06 on 2008-09-01
Here is the response I receive when I check for gnome-vfs-daemon:

```

mateo@Athlon:~$ ps -e | grep -i vfs-da
 5624 ?        00:00:00 gnome-vfs-daemo

```

---

### Post by neur0 on 2008-09-01
Just to report that it happened to me again, and, again the restart fixed it.
Manual mount (from the console) is fine, but no way to automount or mount via click on the panel icon and "Mount"
When I try the click-on-the-panel-and-mount option I get an empty error box.

---

### Post by computer_freak_8 on 2008-09-20
> **MentalNotes said:**
> Regarding finding the automounting options, they've been moved to the Nautilus preferences. You can find them by opening nautilus, going to Edit -> Preferences and clicking on the Media tab. It had me a lost for a bit when I upgraded to Hardy too.

This does not cover automatically mounting - it just covers whether or they will be opened after they are inserted (and mounted). It is possible for it to be mounted automatically without being opened automatically, and that is exactly what (to my understanding) this option does.

I would have to say that the quote in the most recent post by "prshah" worked for me - except I opened a terminal instead of hitting [Alt]+[F2].
(Now, I've even added a shortcut to the System -> Preferences menu.)

---

### Post by lamps06 on 2008-10-02
So it has been several weeks since I looked at this thread and it appears to have died.  In light of Ubuntu 8.10 beta being released today I wanted to resurrect the thread.

Does anyone know if the USB drive mounting issues have been addressed in this new release?  I am downloading the beta Live DVD ISO right now so I can test but I am curious if the community as a whole is aware of the trouble people have been having.

---

### Post by computer_freak_8 on 2008-10-02
> **lamps06 said:**
> So it has been several weeks since I looked at this thread and it appears to have died.

I'm still here!

Okay, try this:
1. Open "gnome-conf"
2. Click the down arrow next to "apps"
3. Click the down arrow next to "nautilus"
4. Click folder icon for "preferences"
5. Post a reply that says what you have in the "Value" column for the following items in the "Name" column

media_automount
media_automount_open
media_autorun_never
media_autorun_x_content_ask
media_autorun_x_content_ignore
media_autorun_x_content_open_folder

****Edit: Wrong command given! See post [http://ubuntuforums.org/showpost.php?p=5931731&postcount=85]("http://ubuntuforums.org/showpost.php?p=5931731&postcount=85") for the correction.****

---

### Post by Avionix on 2008-10-04
Hi I am also experiencing problems with auto mounting USB drives, I have tried most of the proposed solutions in this thread to no avail, I can see the USB drive in the 'places' dropdown but it will not mount. I run dmesg | tail as suggested and get the following ;

steve@DEERYHOME:~$ dmesg | tail
[17368862.492000] SCSI device sda: 2015231 512-byte hdwr sectors (1032 MB)
[17368862.492000] sda: Write Protect is off
[17368862.492000] sda: Mode Sense: 00 00 00 00
[17368862.492000] sda: assuming drive cache: write through
[17368862.492000]  sda: sda1
[17368862.600000] sd 7:0:0:0: Attached scsi removable disk sda
[17368862.600000] sd 7:0:0:0: Attached scsi generic sg0 type 0
[17368862.600000] usb-storage: device scan complete
[17368863.520000] FAT: Unrecognized mount option "flush" or missing value
[17369601.720000] FAT: Unrecognized mount option "flush" or missing value
steve@DEERYHOME:~$ 

Anyone got any idea what this is trying to tell me? I get the same error for all my USB drives and also my handycam.

Thanks in Advance.

---

### Post by computer_freak_8 on 2008-10-05
Okay, I'm still a newbie, but by the looks of 
> **Avionix said:**
> 
[17368863.520000] FAT: Unrecognized mount option "flush" or missing value
[17369601.720000] FAT: Unrecognized mount option "flush" or missing value

it looks like it is not recognizing a mount option ("flush"). 


Here's what I'd like you to do:

1. Post you "/etc/fstab" file.
2. Describe what exactly happens when you:
   A. Plug in your flash drive
   B. Try to mount it.
3. Describe your method for trying to mount it.
4. Post what the instructions tell you to in [this post here (Click me!)]("http://ubuntuforums.org/showpost.php?p=5896619&postcount=72").

Note: The order in which you do the above is not really important; I just numbered them for clarity, and so that you won't have to quote/end-quote so much.


Thanks for posting,
computer_freak_8

---

### Post by Avionix on 2008-10-06
Thanks for the reply, here's the contents of /etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1 -- converted during upgrade to edgy
UUID=55e8b327-b1ae-40a0-b4df-9fd3cc60a78a / ext3 defaults,errors=remount-ro 0 1
# /dev/hda5 -- converted during upgrade to edgy
UUID=21026bd9-3d0a-4f27-84b3-6b4afe4daa68 none swap sw 0 0
/dev/cdrom        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda        /media/usb0     auto    rw,user,noauto  0       0

When I plug in a USB device I get the following
mount: wrong fs type, bad option, bad superblock on /dev/sda1, missing codepage or helper program, or other error

I am then advised to check the output of dmesg | tail or so which is what I posted previously.

I appreciate your help.

---

### Post by computer_freak_8 on 2008-10-06
First off, what is your response to the other steps?
> **computer_freak_8]Here's what I'd like you to do:

1. Post you "/etc/fstab" file.
2. Describe what exactly happens when you:
A. Plug in your flash drive
B. Try to mount it.
3. Describe your method for trying to mount it.
4. Post what the instructions tell you to in [this post here (Click me!).]("http://ubuntuforums.org/showpost.php?p=5896619&postcount=72")[/quote]

Second, I noticed this line in your fstab file:
[QUOTE=Avionix said:**
> /dev/sda        /media/usb0     auto    rw,user,noauto  0       0

I'd like you to comment it out. That is, add the # character in front of it, so it looks like this:```
#/dev/sda        /media/usb0     auto    rw,user,noauto  0       0
```
Note: You will have to edit it as root - don't forget to save it! To edit it as root, open it with:```
sudo gedit /etc/fstab
```

After that, make sure the flash drive is unplugged, and then reboot. Then do the above steps. (I'm talking about the ones where I quoted myself!)

I need all the steps posted here for me to be able to help you the most. (This means 1 (which you already did, (Thanks!) I don't need that again,) 2-A, 2-B, 3, and 4.)

Hope to hear soon!
computer_freak_8

---

### Post by zanlation on 2008-10-07
I have been following this thread with hope as I have the same problem.  Once I commented out the following in fstab the USB flash drive loaded fine automatically. :)

# /dev/sdb1  /media/cdrom0 udf,iso9660, user, noauto, exec, utf8 0 0

I don't have a cdrom drive, so this wasn't an issue.

---

### Post by Avionix on 2008-10-08
Hello again computer_freak_8,
I have made the changes to the fsab file as you suggested saved and rebooted
2A When I plug in the usb stick I get a text box which says "unable to mount the volume xxxx" The details are
mount: wrong fs type, bad option,bad superblock on / dev/sda1, missing codepage or helper program or other error in some cases useful information is found in syslog - try dmesg | tail or so
2B and 3 I try to manually mount the USB stick as follows borrowing from a previous step in this thread,
steve@DEERYHOME:~$ sudo mount -t vfat/dev/sdd /media/USB0
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
or by label, using  -L label  or by uuid, using  -U uuid

4 I have posted this as requested, did I use the correct manual mounting option?

Thanks for your help.

---

### Post by Avionix on 2008-10-08
Hello again, just tried to mount it as follows using info from another forum on manually mounting Flashdrives, still no joy.

steve@DEERYHOME:~$ cd Desktop
steve@DEERYHOME:~/Desktop$ mkdir flash
steve@DEERYHOME:~/Desktop$ dmesg | grep -i "SCSI device"
[17218073.200000] SCSI device sda: 507904 512-byte hdwr sectors (260 MB)
[17218073.208000] SCSI device sda: 507904 512-byte hdwr sectors (260 MB)
[17219601.076000] SCSI device sda: 507904 512-byte hdwr sectors (260 MB)
[17219601.084000] SCSI device sda: 507904 512-byte hdwr sectors (260 MB)
steve@DEERYHOME:~/Desktop$ pwd
/home/steve/Desktop
steve@DEERYHOME:~/Desktop$ sudo  mount -t vfat -o uid=steve,gid=users /dev/sda /home/steve/Desktop/flash
mount: wrong fs type, bad option, bad superblock on /dev/sda,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
Same error as when I try to get it to automount hmmm.

---

### Post by computer_freak_8 on 2008-10-08
> **Avionix said:**
> ... did I use the correct manual mounting option

Well, this question depends on how your flash drive is formatted. 
What is the output of:
> sudo fdisk -l

Also, do you have data on the flash drive you need to keep?
Does the flash drive work in other operating systems? If so, what operating systems does it seem to work on?

Now, not sure if this will help, but it's worth a try:
[quote=computer_freak_8]Okay, try this:
1. Open "gnome-conf"
2. Click the down arrow next to "apps"
3. Click the down arrow next to "nautilus"
4. Click folder icon for "preferences"
5. Post a reply that says what you have in the "Value" column for the following items in the "Name" column

media_automount
media_automount_open
media_autorun_never
media_autorun_x_content_ask
media_autorun_x_content_ignore
media_autorun_x_content_open_folder[/quote]


****Edit: Wrong command given! See post [http://ubuntuforums.org/showpost.php?p=5931731&postcount=85]("http://ubuntuforums.org/showpost.php?p=5931731&postcount=85") for the correction.****

---

### Post by Avionix on 2008-10-08
Hi sudo fdisk -i reveals the following:



Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00017d9f

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       14263   114567516   83  Linux
/dev/hda2           14264       14593     2650725    5  Extended
/dev/hda5           14264       14593     2650693+  82  Linux swap / Solaris

Disk /dev/sda: 260 MB, 260046848 bytes
1 heads, 32 sectors/track, 15872 cylinders
Units = cylinders of 32 * 512 = 16384 bytes
Disk identifier: 0xe4a8cf36

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           2       15872      253936    6  F


The flash drive works fine on windoze XP and on my laptop which is running Hardy flawlessly.
Where would I find gnome-conf I cannot find it using the search tool or in /etc ???

---

### Post by computer_freak_8 on 2008-10-08
> **Avionix said:**
> Where would I find gnome-conf I cannot find it using the search tool or in /etc ???

1. Go to terminal
2. Type:```
gnome-conf
```
3. Press enter

This should bring it up. (It's a GUI application.)

****Edit: Wrong command given! See post [http://ubuntuforums.org/showpost.php?p=5931731&postcount=85]("http://ubuntuforums.org/showpost.php?p=5931731&postcount=85") for the correction.****

---

### Post by computer_freak_8 on 2008-10-08
Was the flash drive plugged in when you ran "sudo fdisk -l"? 

If not, please plug it in, wait about 30 seconds, run "sudo fdisk -l" again, and re-post with its output. If it was plugged in when you ran it, mention that instead.

Thanks.
computer_freak_8

---

### Post by Avionix on 2008-10-08
I tried the gnome-conf in the terminal, made sure the flashdrive was connected, results below;

steve@DEERYHOME:~$ gnome-conf
bash: gnome-conf: command not found
steve@DEERYHOME:~$ sudo fdisk -l
[sudo] password for steve: 

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00017d9f

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       14263   114567516   83  Linux
/dev/hda2           14264       14593     2650725    5  Extended
/dev/hda5           14264       14593     2650693+  82  Linux swap / Solaris

Disk /dev/sda: 260 MB, 260046848 bytes
1 heads, 32 sectors/track, 15872 cylinders
Units = cylinders of 32 * 512 = 16384 bytes
Disk identifier: 0xe4a8cf36

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           2       15872      253936    6  FAT16


I copied and pasted the commands to make sure I got them right.

---

### Post by computer_freak_8 on 2008-10-08
> **Avionix said:**
> steve@DEERYHOME:~$ gnome-conf
bash: gnome-conf: command not found
...
I copied and pasted the commands to make sure I got them right.

I am so sorry: I gave you the wrong command!

Okay, try *this*:
1. Open "gconf-editor" <-- From terminal
2. Click the down arrow next to "apps"
3. Click the down arrow next to "nautilus"
4. Click folder icon for "preferences"
5. Post a reply that says what you have in the "Value" column for the following items in the "Name" column

media_automount
media_automount_open
media_autorun_never
media_autorun_x_content_ask
media_autorun_x_content_ignore
media_autorun_x_content_open_folder


As for the "fdisk -l", it sees your flash drive, so I will have to do some thinking on this one...
Can you plug your flash drive into the (working) Ubuntu computer, make sure it's mounted, and then post the results of "fdisk -l", please?

Note 1: I previously (and mistakenly) told you "gnome-conf". This time, I mention "gconf-editor". 

Note 2: Don't use quotes when entering it

Note 3: *I* copied and pasted this time; I hope it will work!

---

### Post by Avionix on 2008-10-09
Hi computer_freak_8, I really appreciate your help on this the values are as follows;
                                                Value
media_automount                                   Ticked box
media_automount_open                              Ticked box
media_autorun_never                             Unticked box
media_autorun_x_content_ask                             []
media_autorun_x_content_ignore                          [] 
media_autorun_x_content_open_folder                     []


I hope this tells you something.

Thanks,

Avionix

---

### Post by Avionix on 2008-10-09
sorry didn't read your full reply, plugged the same flashdrive into the laptop, it mounted with no problem fdisk -l reveals the following


steve@steve-laptop:~$ sudo fdisk -l 
[sudo] password for steve: 

Disk /dev/sda: 40.0 GB, 40007761920 bytes 
255 heads, 63 sectors/track, 4864 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Disk identifier: 0x41ab2316 

   Device Boot      Start         End      Blocks   Id  System 
/dev/sda1               1          10       80293+  de  Dell Utility 
/dev/sda2   *          11        1285    10241437+   7  HPFS/NTFS 
/dev/sda3            1286        4803    28258335   83  Linux 
/dev/sda4            4804        4864      489982+   5  Extended 
/dev/sda5            4804        4864      489951   82  Linux swap / Solaris 

Disk /dev/sdb: 260 MB, 260046848 bytes 
1 heads, 32 sectors/track, 15872 cylinders 
Units = cylinders of 32 * 512 = 16384 bytes 
Disk identifier: 0xe4a8cf36 

   Device Boot      Start         End      Blocks   Id  System 
/dev/sdb1   *           2       15872      253936    6  FAT16 

Cheers,

---

### Post by computer_freak_8 on 2008-10-09
Okay, I just found another thread with a similar problem.


Try this:

1. Make sure flash drive is **_not_** plugged in; if it is, _**un**_plug it
2. Open "gconf-editor"
3. Click the arrow next to "system", "storage", and finally "default_options"
4. Click on the "vfat" folder
5. Double-click the "mount_options" item (on the right side)
6. Click on the word "flush""
7. Click the "Remove" button
8. Click the "OK" button
9. Close the Configuration Editor
10. Plug in your flash drive
11. Post what happened

****Edit: I noticed that I should probably clarify step two in case someone finds this post but hasn't read the whole thread. 
1. Click the "Applications" menu
2. Move the mouse to "Accessories"
3. Click "Terminal"
4. Type the following into the terminal:
```
gconf-editor
```
5. Press the [Enter] key on your keyboard
6. Continue with step #3 ***above*** the start of the edit****

---

### Post by Avionix on 2008-10-10
It mounts, yahooo!!!!, thanks a million.

I have no idea what flush means or how it got to be the default option, my video camera now mounts also, excellent.

Thanks again.

---

### Post by computer_freak_8 on 2008-10-10
Good. Glad to hear it. 

Now, here's your job: Try to help others with the same problem.
(You don't *have* to, but others would appreciate it, I'm sure.)

---

### Post by Avionix on 2008-10-10
I'll be glad to.

---

### Post by lamps06 on 2008-10-13
Sorry, computer_freak_8, but this did not solve my issue either.  My flash drive still just shows up as "USB Drive" within Nautilus but when I double click it says "Unable to mount location, can't mount file."  

On a side note I am running Ubuntu 8.10 beta within a virtual machine at work and I can mount the same USB drive fine.

---

### Post by boscorama on 2008-10-13
One thing to try is to type the following two commands into a shell:

$ sudo modprobe -r usb_storage
(Check dmesg to make sure it unloads)
(wait 10 seconds)
$ sudo modprobe usb_storage
(Check dmesg again)

It worked for me on kubuntu 8.04.1

HTH.

---

### Post by computer_freak_8 on 2008-10-13
After a little bit of digging, I came across I good thought:

1. Create a new (temporary) user
2. Give them all the same permissions that you have
3. Log in as them
4. See if the problem is there
5A. If you can mount it just fine, you know it is something messed-up with your account
5B. If you have the same problem(s), you know that it is something messed-up system-wide

Post back to let me know if it was 5A or 5B.

---

### Post by lamps06 on 2008-10-14
boscorama:  I tried what you suggested first, but I was still unable to mount my flash drive.  When I run dmesg when the drive is first attached I get this:

```
[ 2586.674152] usb 3-2.4: new high speed USB device using ehci_hcd and address 7
[ 2586.759809] usb 3-2.4: configuration #1 chosen from 1 choice
[ 2586.802844] scsi8 : SCSI emulation for USB Mass Storage devices
[ 2586.807127] usb-storage: device found at 7
[ 2586.807516] usb-storage: waiting for device to settle before scanning
[ 2591.810505] usb-storage: device scan complete
[ 2591.811856] scsi 8:0:0:0: Direct-Access     JetFlash TS2GJF110        0.00 PQ: 0 ANSI: 2
[ 2591.814319] sd 8:0:0:0: [sdd] 4096000 512-byte hardware sectors (2097 MB)
[ 2591.814934] sd 8:0:0:0: [sdd] Write Protect is off
[ 2591.814941] sd 8:0:0:0: [sdd] Mode Sense: 00 00 00 00
[ 2591.814944] sd 8:0:0:0: [sdd] Assuming drive cache: write through
[ 2591.816685] sd 8:0:0:0: [sdd] 4096000 512-byte hardware sectors (2097 MB)
[ 2591.817301] sd 8:0:0:0: [sdd] Write Protect is off
[ 2591.817307] sd 8:0:0:0: [sdd] Mode Sense: 00 00 00 00
[ 2591.817311] sd 8:0:0:0: [sdd] Assuming drive cache: write through
[ 2591.817323]  sdd: sdd1
[ 2591.893690] sd 8:0:0:0: [sdd] Attached SCSI removable disk
[ 2591.893765] sd 8:0:0:0: Attached scsi generic sg4 type 0

```

It looks like the flash drive is being seen as a SCSI drive...  After running ```
sudo modprobe -r usb_storage
``` I get this:

```
[ 2741.708498] usbcore: deregistering interface driver usb-storage
[ 2741.721689] usbcore: deregistering interface driver libusual

```

Then I run ```
sudo modprobe usb_storage
``` and after that the output of dmesg is:

```
[ 2825.439246] Initializing USB Mass Storage driver...
[ 2825.448555] scsi9 : SCSI emulation for USB Mass Storage devices
[ 2825.455423] usbcore: registered new interface driver usb-storage
[ 2825.455907] USB Mass Storage support registered.
[ 2825.457500] usb-storage: device found at 7
[ 2825.457943] usb-storage: waiting for device to settle before scanning
[ 2830.455219] usb-storage: device scan complete
[ 2836.021197] usb 3-2.4: reset high speed USB device using ehci_hcd and address 7
[ 2836.107963] scsi 9:0:0:0: Direct-Access     JetFlash TS2GJF110        0.00 PQ: 0 ANSI: 2
[ 2836.110571] sd 9:0:0:0: [sdd] 4096000 512-byte hardware sectors (2097 MB)
[ 2836.111200] sd 9:0:0:0: [sdd] Write Protect is off
[ 2836.111207] sd 9:0:0:0: [sdd] Mode Sense: 00 00 00 00
[ 2836.111211] sd 9:0:0:0: [sdd] Assuming drive cache: write through
[ 2836.112814] sd 9:0:0:0: [sdd] 4096000 512-byte hardware sectors (2097 MB)
[ 2836.113434] sd 9:0:0:0: [sdd] Write Protect is off
[ 2836.113440] sd 9:0:0:0: [sdd] Mode Sense: 00 00 00 00
[ 2836.113443] sd 9:0:0:0: [sdd] Assuming drive cache: write through
[ 2836.113450]  sdd: sdd1
[ 2836.114467] sd 9:0:0:0: [sdd] Attached SCSI removable disk
[ 2836.114536] sd 9:0:0:0: Attached scsi generic sg4 type 0

```

---

### Post by lamps06 on 2008-10-14
computer_freak_8:  I did what you suggested as well.  I created a new user, gave the user the same permissions as my other user, logged in as the new user and had the same results when attempting to mount the USB flash drive.

---

### Post by computer_freak_8 on 2008-10-14
> **lamps06 said:**
> I created a new user, gave the user the same permissions as my other user, logged in as the new user and had the same results when attempting to mount the USB flash drive.

So, it is system wide... interesting. I'm continuing to look for information, and I will soon be trying different things on my installation (specifically made to be okay to mess up) to see if I can get my flash drive to give me the same error. If I am able to accomplish this, knowing which setting I changed last, I will (hopefully) be able to resolve your problem by having you change the problematic setting.

Note: I am **not** implying that you changed a setting by mistake and can't remember what it was. I think that something happened that made it change, from anything like a power drop/hardware hiccup to a cookie stored at the same time you left-clicked the mouse. (No, I do not know *how* any of these things could have changed it, but it's a computer - stranger things have happened...)

---

### Post by lamps06 on 2008-10-14
Thanks a lot for taking the time to investigate the issue.  I feel like my case is sort of unique and most other people have had their problems resolved by any one of the other numerous solutions offered up in this and other threads.

Do you think the problems I am having are in any way related to the references to SCSI being made by dmesg in regards to my USB drive?  This seems like a red flag to me but maybe I am wrong.

---

### Post by computer_freak_8 on 2008-10-14
> **lamps06 said:**
> Do you think the problems I am having are in any way related to the references to SCSI being made by dmesg in regards to my USB drive?  This seems like a red flag to me but maybe I am wrong.

I don't think so. Usually that's what I think they're detected as. As far as I know, (which could easily be wrong,) Linux uses "hd_" for things it thinks are hard drives, and "sd_" for anything that it thinks is Small Computer System Interface (SCSI). Not sure though, I thought it was supposed to see Integrated Drive Electronics (IDE) hard drives as "hd_", but I've always had them show up as "sd_"

I have an idea... hold on.

---

### Post by computer_freak_8 on 2008-10-14
No, it's not the SCSI part that's causing the problem...

Plugged in flash drive, which automounted and autoopened, then:
```
dmesg
```
```

[45780.636268] usb 2-9.2: new high speed USB device using ehci_hcd and address 8
[45780.749752] usb 2-9.2: configuration #1 chosen from 1 choice
[45780.750244] scsi12 : SCSI emulation for USB Mass Storage devices
[45780.750423] usb-storage: device found at 8
[45780.750432] usb-storage: waiting for device to settle before scanning
[45785.749012] usb-storage: device scan complete
[45785.750124] scsi 12:0:0:0: Direct-Access     TOSHIBA  TransMemory      5.00 PQ: 0 ANSI: 0 CCS
[45786.353975] sd 12:0:0:0: [sdd] 8058880 512-byte hardware sectors (4126 MB)
[45786.356848] sd 12:0:0:0: [sdd] Write Protect is off
[45786.356853] sd 12:0:0:0: [sdd] Mode Sense: 23 00 00 00
[45786.356856] sd 12:0:0:0: [sdd] Assuming drive cache: write through
[45786.366978] sd 12:0:0:0: [sdd] 8058880 512-byte hardware sectors (4126 MB)
[45786.369849] sd 12:0:0:0: [sdd] Write Protect is off
[45786.369853] sd 12:0:0:0: [sdd] Mode Sense: 23 00 00 00
[45786.369856] sd 12:0:0:0: [sdd] Assuming drive cache: write through
[45786.369860]  sdd: sdd1
[45786.372300] sd 12:0:0:0: [sdd] Attached SCSI removable disk
[45786.372343] sd 12:0:0:0: Attached scsi generic sg6 type 0
[45916.367889] usb 2-9.2: USB disconnect, address 8
[45918.115253] usb 2-9.2: new high speed USB device using ehci_hcd and address 9
[45918.228611] usb 2-9.2: configuration #1 chosen from 1 choice
[45918.229096] scsi13 : SCSI emulation for USB Mass Storage devices
[45918.229255] usb-storage: device found at 9
[45918.229260] usb-storage: waiting for device to settle before scanning
[45923.227776] usb-storage: device scan complete
[45923.228857] scsi 13:0:0:0: Direct-Access     TOSHIBA  TransMemory      5.00 PQ: 0 ANSI: 0 CCS
[45924.203706] sd 13:0:0:0: [sdd] 8058880 512-byte hardware sectors (4126 MB)
[45924.206578] sd 13:0:0:0: [sdd] Write Protect is off
[45924.206583] sd 13:0:0:0: [sdd] Mode Sense: 23 00 00 00
[45924.206585] sd 13:0:0:0: [sdd] Assuming drive cache: write through
[45924.216704] sd 13:0:0:0: [sdd] 8058880 512-byte hardware sectors (4126 MB)
[45924.219580] sd 13:0:0:0: [sdd] Write Protect is off
[45924.219584] sd 13:0:0:0: [sdd] Mode Sense: 23 00 00 00
[45924.219586] sd 13:0:0:0: [sdd] Assuming drive cache: write through
[45924.219591]  sdd: sdd1
[45924.222026] sd 13:0:0:0: [sdd] Attached SCSI removable disk
[45924.222072] sd 13:0:0:0: Attached scsi generic sg6 type 0

```
Okay, so:
```
sudo modprobe -r usb_storage
```
```
FATAL: Module usb_storage is in use.
```
Oh, right, I probably have to unmount it. Okay, that's done; try again:
```
sudo modprobe -r usb_storage
FATAL: Module usb_storage is in use.
sudo modprobe -r usb_storage
FATAL: Module usb_storage is in use.
sudo modprobe -r usb_storage
FATAL: Module usb_storage is in use.
sudo modprobe -r usb_storage
FATAL: Module usb_storage is in use.

```
Now, *why* won't it--     oh. That's why... Well, I can't unplug my USB hard drive; I'm using it, so:
```
sudo modprobe usb_storage
dmesg
[45780.636268] usb 2-9.2: new high speed USB device using ehci_hcd and address 8
[45780.749752] usb 2-9.2: configuration #1 chosen from 1 choice
[45780.750244] scsi12 : SCSI emulation for USB Mass Storage devices
[45780.750423] usb-storage: device found at 8
[45780.750432] usb-storage: waiting for device to settle before scanning
[45785.749012] usb-storage: device scan complete
[45785.750124] scsi 12:0:0:0: Direct-Access     TOSHIBA  TransMemory      5.00 PQ: 0 ANSI: 0 CCS
[45786.353975] sd 12:0:0:0: [sdd] 8058880 512-byte hardware sectors (4126 MB)
[45786.356848] sd 12:0:0:0: [sdd] Write Protect is off
[45786.356853] sd 12:0:0:0: [sdd] Mode Sense: 23 00 00 00
[45786.356856] sd 12:0:0:0: [sdd] Assuming drive cache: write through
[45786.366978] sd 12:0:0:0: [sdd] 8058880 512-byte hardware sectors (4126 MB)
[45786.369849] sd 12:0:0:0: [sdd] Write Protect is off
[45786.369853] sd 12:0:0:0: [sdd] Mode Sense: 23 00 00 00
[45786.369856] sd 12:0:0:0: [sdd] Assuming drive cache: write through
[45786.369860]  sdd: sdd1
[45786.372300] sd 12:0:0:0: [sdd] Attached SCSI removable disk
[45786.372343] sd 12:0:0:0: Attached scsi generic sg6 type 0
[45916.367889] usb 2-9.2: USB disconnect, address 8
[45918.115253] usb 2-9.2: new high speed USB device using ehci_hcd and address 9
[45918.228611] usb 2-9.2: configuration #1 chosen from 1 choice
[45918.229096] scsi13 : SCSI emulation for USB Mass Storage devices
[45918.229255] usb-storage: device found at 9
[45918.229260] usb-storage: waiting for device to settle before scanning
[45923.227776] usb-storage: device scan complete
[45923.228857] scsi 13:0:0:0: Direct-Access     TOSHIBA  TransMemory      5.00 PQ: 0 ANSI: 0 CCS
[45924.203706] sd 13:0:0:0: [sdd] 8058880 512-byte hardware sectors (4126 MB)
[45924.206578] sd 13:0:0:0: [sdd] Write Protect is off
[45924.206583] sd 13:0:0:0: [sdd] Mode Sense: 23 00 00 00
[45924.206585] sd 13:0:0:0: [sdd] Assuming drive cache: write through
[45924.216704] sd 13:0:0:0: [sdd] 8058880 512-byte hardware sectors (4126 MB)
[45924.219580] sd 13:0:0:0: [sdd] Write Protect is off
[45924.219584] sd 13:0:0:0: [sdd] Mode Sense: 23 00 00 00
[45924.219586] sd 13:0:0:0: [sdd] Assuming drive cache: write through
[45924.219591]  sdd: sdd1
[45924.222026] sd 13:0:0:0: [sdd] Attached SCSI removable disk
[45924.222072] sd 13:0:0:0: Attached scsi generic sg6 type 0
```

I'll keep looking...

---

### Post by computer_freak_8 on 2008-10-14
I'm now grasping at anything and everything I can.
Try these two commands:
```
sudo lshw -C disk -businfo
```
and
```
sudo lshw -C disk
```
and then post the output of both.

---

### Post by cleopete on 2008-10-14
I am so bummed to see this thread is still in play, but Lamps, you are the iron man.  I bailed and reinstalled some time ago (which turned out to be way...WAY more of a hassle than the first time), and I haven't had that problem since...on this machine.

Now it's happening to one of my desktops.  It only affects the first thumb drive, and I have a gazillion of those and plenty of usb drives, but it's not the most elegant soulution.

I've kinda given up, and ave been looking toward Intrepid's imminent release.  Do we know if this has been a problem in the alpha?

---

### Post by computer_freak_8 on 2008-10-15
> **cleopete said:**
> ... and ave been looking toward Intrepid's imminent release.  Do we know if this has been a problem in the alpha?

Well, according to "lamps06":
> **lamps06 said:**
> ... On a side note I am running Ubuntu 8.10 beta within a virtual machine at work and I can mount the same USB drive fine.

(I myself have not tested it, but I trust lamps06. Although, you mentioned "alpha" and he/she (which? dunno...) mentioned "beta". The beta version can be found [here]("http://www.ubuntu.com/testing/intrepid/beta").)

---

### Post by computer_freak_8 on 2008-10-15
I just thought I'd note that I find this problem very interesting. User lamps06, I'm sure finds it very, *very* irritating. (I would, too. Especially an LTS version - that's what gets me about it. I dunno, though...)

Any other Ubuntu gurus have any ideas? I may have given my last one, so if it doesn't work... *crossing fingers*

---

### Post by lamps06 on 2008-10-20
Sorry for the delayed response.  Here is the output of sudo lshw -C disk -businfo:

```

Bus info          Device       Class       Description
======================================================
scsi@2:0.0.0      /dev/sdd     disk        2097MB TS2GJF110
                  /dev/sdd     disk        2097MB 
scsi@0:0.0.0      /dev/sda     disk        80GB WDC WD800JB-00JJ
scsi@0:0.1.0      /dev/sdb     disk        100GB Maxtor 6L100P0
scsi@1:0.0.0      /dev/sdc     disk        30GB WDC WD307AA-00BA
scsi@1:0.1.0      /dev/cdrom1  disk        DVD_RW ND-3550A

```

And here is the output of sudo lshw -C disk:

```

  *-disk                  
       description: SCSI Disk
       product: TS2GJF110
       vendor: JetFlash
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/sdd
       version: 0.00
       size: 2000MiB (2097MB)
       capabilities: removable
       configuration: ansiversion=2
     *-medium
          physical id: 0
          logical name: /dev/sdd
          size: 2000MiB (2097MB)
          capabilities: partitioned partitioned:dos
          configuration: signature=91f72d24
  *-disk:0
       description: ATA Disk
       product: WDC WD800JB-00JJ
       vendor: Western Digital
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 05.0
       serial: WD-WCAM9U901415
       size: 74GiB (80GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=000884cf
  *-disk:1
       description: ATA Disk
       product: Maxtor 6L100P0
       vendor: Maxtor
       physical id: 1
       bus info: scsi@0:0.1.0
       logical name: /dev/sdb
       version: BAJ4
       serial: L21WEQAG
       size: 93GiB (100GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=004d212e
  *-disk:2
       description: ATA Disk
       product: WDC WD307AA-00BA
       vendor: Western Digital
       physical id: 2
       bus info: scsi@1:0.0.0
       logical name: /dev/sdc
       version: 10.0
       serial: WD-WMA2F2214588
       size: 28GiB (30GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=20202020
  *-cdrom
       description: DVD writer
       product: DVD_RW ND-3550A
       vendor: _NEC
       physical id: 3
       bus info: scsi@1:0.1.0
       logical name: /dev/cdrom1
       logical name: /dev/dvd1
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 1.05
       serial: [_NEC    DVD_RW ND-3550A 1.0505093000
       capabilities: removable audio cd-r cd-rw dvd dvd-r
       configuration: ansiversion=5 status=open


```

---

### Post by Stelakis1 on 2008-10-21
I have the same problem.

I tried everything that was said here but still nothing...

One thing is very funny though...

When I plug the usb stick nothing happens, but right after I run lsusb in a terminal the usb device pops up in nautilus...
I unmount the device and plugged it in again... nothing...
I run once again lsusb and again it pops up.

Not to forget that when I boot my PC and the usb device is plugged then it's fully recognizable...

---

### Post by Raithmir on 2008-10-22
> **Stelakis1 said:**
> I have the same problem.

I tried everything that was said here but still nothing...

One thing is very funny though...

When I plug the usb stick nothing happens, but right after I run lsusb in a terminal the usb device pops up in nautilus...
I unmount the device and plugged it in again... nothing...
I run once again lsusb and again it pops up.

Not to forget that when I boot my PC and the usb device is plugged then it's fully recognizable...

I have exactly the same issue. Annoying thing is this was working fine. It seemed to stop working after I rebooted following some updates, including a new kernel update.

Next time I reboot I'll try with the older kernel version again.

---

### Post by OpenKimono on 2008-10-22
I just upgraded from ubuntu 6.06 to 8.04 today.  I ran into several problems after rebooting, notably this one.  I found the Configuration Editor (gconf-editor) parameter that was the culprit.

system->storage->default_options->vfat

It was set to [shortname=mixed,uid=,utf8,umask=0777,exec,flush]

By removing "flush", I was able to automount my USB device again.:)

---

### Post by Modernity on 2008-10-22
OK, not to add any more users to the post and just to give you a , but I recently installed Xubuntu and after up-dates the USB flash drive won't mount. So, here is how it works, and maybe you can tell me how to fix it. When you start the system up with the drive plugged in, it automounts fine. When the system is started without the USB flash drive and you plug it in it gives the Unable to mount error. So, is it the FLUSH option causing this? I don't have gconf installed. I am using Xubuntu, so if you can tell me where the FLUSH option for the drive, maybe I can try that, unless you can think of something I am missing.

Thanks

---

### Post by Modernity on 2008-10-22
> **Modernity said:**
> OK, not to add any more users to the post and just to give you a , but I recently installed Xubuntu and after up-dates the USB flash drive won't mount. So, here is how it works, and maybe you can tell me how to fix it. When you start the system up with the drive plugged in, it automounts fine. When the system is started without the USB flash drive and you plug it in it gives the Unable to mount error. So, is it the FLUSH option causing this? I don't have gconf installed. I am using Xubuntu, so if you can tell me where the FLUSH option for the drive, maybe I can try that, unless you can think of something I am missing.

Thanks

OK, after scouring the net I fixed it. 2 things I did to fix it is Check the fstab under /etc/ and check the file for a mount for the CDROM. Then Comment it out (using #). then save the file, then turn volume management off in Thunar. Done. If any one else has problems with Xubuntu on an EeePC install, this is what you look for.

---

### Post by Stelakis1 on 2008-10-23
> **Raithmir said:**
> I have exactly the same issue. Annoying thing is this was working fine. It seemed to stop working after I rebooted following some updates, including a new kernel update.

Next time I reboot I'll try with the older kernel version again.

Yes this happened to me too after the latest kernel update. 
And if I remember well there was a hal update at the same time.

---

### Post by Raithmir on 2008-10-24
2.6.24-19-generic kernel : My USB memory stick works fine.
2.6.24-21-generic kernel : Plugging USB memory stick causes light to flash, then stay off. Running lsusb from a shell it immediately starts working and brings up the mount options box.

edit: I'm using Kubuntu 8.04.1 by the way.

---

### Post by computer_freak_8 on 2008-10-24
> **lamps06 said:**
> Sorry for the delayed response.Now, *I'm* sorry for *my* delayed response. Try what others have tried.

1. Reboot
2. Press the [Esc] key to enter the grub menu *This step may not be needed*
3. Choose the Ubuntu entry with the earliest kernel version (lowest number) **Not the "Recovery Mode" option!**
4. Try getting the USB drive to automount
5. Repeat steps 1-4, except #3 - instead, each time choose the next-oldest kernel
6. Post again to tell us what happened

---

### Post by lamps06 on 2008-10-29
Well, I tried booting up with the oldest kernel I had, kernel 2.6.24-16-rt, but my flash drive still does not mount with this kernel.  I thought I had several older kernels that were just not being displayed in this list so I checked menu.lst but there was nothing else there to uncomment and when I checked /boot/ there were no older kernels than the one I used to boot.

Grrrrrrrrr...

---

### Post by lamps06 on 2008-10-29
Also, I am using the real time kernel because I am running Ubuntu Studio.

---

### Post by The Pinny Parlour on 2008-10-31
Everything had been working fine until today.  I downloaded the latest Ibex today and transfered to my USB thumb drive.  I took it home to plug it in to my Ubuntu box and now my Ubuntu box decides not to recognise my USB thumb drive anymore.   It works perfectly in windows but I get get absolutely nothing in Ubuntu.  

I have tried it in all the USB ports the PC has.   I plugged in a USB printer and it works so I'm stumped.  

I was just about to upgrade and this happens.  Oh the upgrade curse has bitten me again, and in reality I hadn't even started the upgrade yet.


Any help please?

---

### Post by vinceTX on 2008-11-01
I don't have an answer but maybe I can add some more info. I have Ubuntu 8.04 (Gnome). I have not done any major upgrades. (I'm on dialup.) I have 3 flash drives, Adata, Patriot and Emprex. They all auto mount and work well.

I bought a new 16GB Corsair Flash Voyager (with FAT32). I took it to the local LUG on Ibex Day to load 8.10 on it. The person who was loading drives could not mount mine. He had an EEE PC with, I think, Ibex. He had a Mac machine nearby and it automounted the drive and Ibex was copied to it.

When I got home my machine would not mount the Corsair, nor could I mount it manually. Again, all of my older USB drives still work. I tend to think that the Corsair drive is good but Hardy (and probably Ibex) can't mount *it* for some reason.

> vince@vince-desktop:~$ lsusb
Bus 004 Device 007: ID 1b1c:0ab1  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

> vince@vince-desktop:~$ sudo lshw
         <snip>
*-scsi
     physical id: 14
     bus info: usb@4:3
     logical name: scsi11
     capabilities: emulated scsi-host
     configuration: driver=usb-storage
  *-disk
      description: SCSI Disk
      product: Flash Voyager
      vendor: Corsair
      physical id: 0.0.0
      bus info: scsi@11:0.0.0
      logical name: /dev/sdb
      version: 0.00
      size: 15GiB (16GB)
      capabilities: removable
      configuration: ansiversion=2
   *-medium
      physical id: 0
      logical name: /dev/sdb
      size: 15GiB (16GB)
      capabilities: partitioned partitioned:dos
      configuration: signature=04dd5721
    *-volume
        description: Windows FAT volume
        vendor: MSDOS5.0
        physical id: 1
        logical name: /dev/sdb1
        version: FAT32
        serial: 9403-e6c0
        size: 15GiB
        capacity: 15GiB
      capabilities: primary bootable fat initialized
        configuration: FATs=2 filesystem=fat


Thanks for everyone's help thus far,
Vince

---

### Post by lunarleo on 2008-11-07
I also had this problem (I use Ubuntu 8.04). I went into the package manager and found a package called usbmount and installed it. My flash drive showed up after a reboot.

---

### Post by Recipe Ferrum on 2008-11-13
Hello!

I just installed Linux for the first time ever 5 days ago, and i'm definitely enjoying it.......except for the USB problems. 

Not only will my thumbdrives not automount, but neither will my external CDROM or USB Mouse. They will work initially upon reboot, but after 5-10 minutes they disappear. However, this seems to be dependent on how active the user is (ie, clicking on a bunch of stuff). If I reboot, and let the computer sit there, I can come back 10 hours later and the mouse will work.....until I click on a bunch of stuff. Once the mouse drops off, so do the thumbdrives. 

I cannot get them to remount with lsusb either. 

Also I tried all the helpful suggestions earlier in the thread about commenting out lines, the gconf-editor, downloading usbmount through synaptic.......nada! 

by the way, i think it's also important to mention that i have no idea what i'm doing....all i know about linux i learned in the last two days from this forum. 

sorry for long post! sheeesh!  
):P

---

### Post by SteinbergerNate on 2008-11-13
Well, if this issue is anything like mine, it's a permissions issue. I was able to access my usb volumes 2 days ago and then yesterday it just stopped working. I'm using xfce with Thunar as my file manager. When I plug in a usb device is shows up but is not mounted until I click on it. 

When I click on it now, I get a message saying that I don't have permissions. So, I launched Thunar as root and when I click on it, it mounts fine. When I close the root Thunar with the device still mounted, and go in as a normal user, everything on that device is read only for normal users. Root is the only one with access to all of it.

I don't know what I changed in the past couple days to make it do this.

---

### Post by computer_freak_8 on 2008-11-16
Okay, I've read through most of this thread again to refresh my memory. I don't know whether I will be able to help anyone or not, but I'm willing to try.

So, for those of you still needing help, please respond to this post with the following information:

[LIST=1]
[*]All the ways that **do** work to access it (Disk mounter applet, Nautilus, manually mounting, et cetera)
[*]All the ways that **do not** work to access it (Disk mounter applet, Nautilus, manually mounting, et cetera)
[*]Does it make any difference in the ways you are able/unable to access it if you use a different kernel?
[*]Does it make any difference in the ways you are able/unable to access it if you use a different user account?
[*]Does it make any difference in the ways you are able/unable to access it if you do what is mentioned [here]("http://ubuntuforums.org/showpost.php?p=5528591&postcount=15")?
[*]Does it make any difference in the ways you are able/unable to access it if you do what is mentioned [here]("http://ubuntuforums.org/showpost.php?p=5931731&postcount=85")?
[*]Post the output of the following commands:
```
dmesg | tail
cat /etc/fstab
sudo fdisk -l
lsusb
sudo mount -l
```
[/LIST]

One more thing: Try [Ubuntu Tweak]("http://ubuntu-tweak.com/downloads"). 
Note: I have not played around with this program myself, (or even installed it - yet,) but I have heard from one post that it might work

---

### Post by agblat on 2008-11-17
> **lamps06 said:**
> For what it was worth I was able to create a /media/USB1 directory and manually mount the drive there using

```

sudo mount -t vfat /dev/sdd /media/USB1

```

But this is a pain.  Before Ubuntu would automount USB devices, I do not want to manually mount them...
Odd automount here as well, except it appears to be volume (as in size) dependent. Automount in Ubuntu 8.04 works for small USB flash almost to 1 gig, but beyond that, the mount behaves erratically. External USB hard drives won't mount at all - even with manual mount (correctly formatted).

---

### Post by computer_freak_8 on 2008-11-17
> **agblat said:**
> Odd automount here as well, except it appears to be volume (as in size) dependent. Automount in Ubuntu 8.04 works for small USB flash almost to 1 gig, but beyond that, the mount behaves erratically. External USB hard drives won't mount at all - even with manual mount (correctly formatted).

Okay, post back the results/answers of/to [this post]("http://ubuntuforums.org/showpost.php?p=6192914&postcount=121") so I can help you troubleshoot more efficiently.

---

### Post by DuGi on 2008-11-21
same problem here. its happened few weeks ago. pendrive or mp3player doesnt appear (no device in fdisk, lshw) until i use command lsusb. then its detected and works fine until disconnect. i dont know where is a problem... (tested on 2 kernels - kubuntu 8.04)

---

### Post by Jota37 on 2008-11-21
> **Jonie said:**
> Lots of posts, but perhaps a drive that wouldn't automount needs just a bit of dosfsck?

Nope. Happens here to several drives, both USB (ext3 OR fat formatted) and CD (all of which work fine in Windows, if they are FAT in the case of some USB).

---

### Post by Jota37 on 2008-11-21
It's indeed an interesting (and irritating) problem, as computer_freak_8 said above...

My SD cards from my cameras work fine on Kubuntu 8.10 (fresh install), but the USB drives don't.

My work computer (Ubuntu 8.04), similar problems. Things worked fine until some (undefined) recent update, then stopped. Addtionally, CDs are not mounting either. I have tried many of the things mentioned above (thanks!), but none worked... yet.

I'll try to dig further later and see if something else I have still to try will do the trick. But this is a HUGE problem and I hope the Ubuntu team is working on getting it fixed ASAP...

---

### Post by agblat on 2008-11-22
> **computer_freak_8 said:**
> Okay, post back the results/answers of/to [this post]("http://ubuntuforums.org/showpost.php?p=6192914&postcount=121") so I can help you troubleshoot more efficiently.
katu@katu-desktop:~$ \dmesg | tail

[ 1182.584523]  sdb: sdb1

[ 1182.585946] sd 14:0:0:0: [sdb] Attached SCSI removable disk

[ 1182.586028] sd 14:0:0:0: Attached scsi generic sg3 type 0

[ 1182.593261] sr2: scsi3-mmc drive: 48x/48x tray

[ 1182.593371] sr 14:0:0:1: Attached scsi CD-ROM sr2

[ 1182.593439] sr 14:0:0:1: Attached scsi generic sg4 type 5

[ 1190.580725] usb 4-5: USB disconnect, address 14

[ 1190.581210] Buffer I/O error on device sdb1, logical block 1

[ 1190.581216] lost page write due to I/O error on sdb1

[ 1190.621480] scsi 14:0:0:0: rejecting I/O to dead device


katu@katu-desktop:~$ cat /etc/fstab

# /etc/fstab: static file system information.

#

# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc            /proc           proc    defaults        0       0

# /dev/sda1

UUID=bd12e5fb-591c-4881-a81d-a47e22f3b78e /               ext3    relatime,errors=remount-ro 0       1

# /dev/sda5

UUID=86fa2446-91ee-4cb2-ab92-e64db7247bdc none            swap    sw              0       0

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0


katu@katu-desktop:~$ sudo fdisk -l



Disk /dev/sda: 61.4 GB, 61492838400 bytes

255 heads, 63 sectors/track, 7476 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes

Disk identifier: 0x24e624e5



   Device Boot      Start         End      Blocks   Id  System

/dev/sda1   *           1        7165    57552831   83  Linux

/dev/sda2            7166        7476     2498107+   5  Extended

/dev/sda5            7166        7476     2498076   82  Linux swap / Solaris


katu@katu-desktop:~$ lsusb

Bus 004 Device 001: ID 0000:0000  

Bus 003 Device 001: ID 0000:0000  

Bus 002 Device 001: ID 0000:0000  

Bus 001 Device 003: ID 045e:0039 Microsoft Corp. IntelliMouse Optical

Bus 001 Device 001: ID 0000:0000  

katu@katu-desktop:~$ sudo mount -l

/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro) []

proc on /proc type proc (rw,noexec,nosuid,nodev)

/sys on /sys type sysfs (rw,noexec,nosuid,nodev)

varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)

varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)

udev on /dev type tmpfs (rw,mode=0755)

devshm on /dev/shm type tmpfs (rw)

devpts on /dev/pts type devpts (rw,gid=5,mode=620)

lrm on /lib/modules/2.6.24-21-generic/volatile type tmpfs (rw)

securityfs on /sys/kernel/security type securityfs (rw)

gvfs-fuse-daemon on /home/katu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=katu)


Above are the results of the terminal inquiries. Best of luck - I appreciate your efforts.

---

### Post by agblat on 2008-11-22
> **computer_freak_8 said:**
> Okay, post back the results/answers of/to [this post]("http://ubuntuforums.org/showpost.php?p=6192914&postcount=121") so I can help you troubleshoot more efficiently.
Forgot to add that when a large volume USB flash is inserted, multiple instances of Home Folder continue popping up until the USB is removed. There is only a brief time to enter a terminal command before these instances make the system unresponsive.

---

### Post by DuGi on 2008-11-23
before **lsusb**

```
athlon% dmesg | tail
[   58.600441] Bluetooth: HCI socket layer initialized
[   58.621285] Bluetooth: L2CAP ver 2.9
[   58.621289] Bluetooth: L2CAP socket layer initialized
[   58.642925] Bluetooth: RFCOMM socket layer initialized
[   58.642936] Bluetooth: RFCOMM TTY layer initialized
[   58.642939] Bluetooth: RFCOMM ver 1.8
[   59.445061] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   59.577507] PPP generic driver version 2.4.2
[   64.147039] PPP BSD Compression module registered
[   64.212173] PPP Deflate Compression module registered


athlon% cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /                ext3    noatime,nodiratime,errors=remount-ro,data=writeback     0       1
/dev/sda3       /home            ext3    relatime        0       2
/dev/sda4       /media/share     ext3    relatime        0       2
/dev/sda2        none            swap    sw              0       0
/dev/scd0       /media/cdrom0    udf,iso9660 user,noauto,exec,utf8 0       0


athlon% sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00026291

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         914     7341673+  83  Linux
/dev/sda2             915        1045     1052257+  82  Linux swap / Solaris
/dev/sda3            1046        7572    52428127+  83  Linux
/dev/sda4            7573       38913   251746582+  83  Linux



athlon% sudo mount -l
/dev/sda1 on / type ext3 (rw,noatime,nodiratime,errors=remount-ro,data=writeback) []
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-21-generic/volatile type tmpfs (rw)
/dev/sda3 on /home type ext3 (rw,relatime) []
/dev/sda4 on /media/share type ext3 (rw,relatime) [share]
securityfs on /sys/kernel/security type securityfs (rw)
rpc_pipefs on /var/lib/nfs/rpc_pipefs type rpc_pipefs (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)



athlon% lsusb
Bus 002 Device 003: ID 1110:9021 Analog Devices Canada, Ltd (Allied Telesyn)
Bus 002 Device 002: ID 1532:0007
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 004: ID 0424:2504 Standard Microsystems Corp. USB 2.0 Hub
Bus 001 Device 001: ID 0000:0000
```

and after **lsusb**

```
athlon% dmesg | tail
[11123.918760] sd 6:0:0:0: [sdc] Write Protect is off
[11123.918762] sd 6:0:0:0: [sdc] Mode Sense: 03 00 00 00
[11123.918764] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[11123.922008] sd 6:0:0:0: [sdc] 1017856 512-byte hardware sectors (521 MB)
[11123.923212] sd 6:0:0:0: [sdc] Write Protect is off
[11123.923215] sd 6:0:0:0: [sdc] Mode Sense: 03 00 00 00
[11123.923216] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[11123.923220]  sdc: unknown partition table
[11123.931966] sd 6:0:0:0: [sdc] Attached SCSI removable disk
[11123.931998] sd 6:0:0:0: Attached scsi generic sg3 type 0



athlon% cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /                ext3    noatime,nodiratime,errors=remount-ro,data=writeback     0       1
/dev/sda3       /home            ext3    relatime        0       2
/dev/sda4       /media/share     ext3    relatime        0       2
/dev/sda2        none            swap    sw              0       0
/dev/scd0       /media/cdrom0    udf,iso9660 user,noauto,exec,utf8 0       0



athlon% sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00026291

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         914     7341673+  83  Linux
/dev/sda2             915        1045     1052257+  82  Linux swap / Solaris
/dev/sda3            1046        7572    52428127+  83  Linux
/dev/sda4            7573       38913   251746582+  83  Linux


Disk /dev/sdc: 521 MB, 521142272 bytes
17 heads, 59 sectors/track, 1014 cylinders
Units = cylinders of 1003 * 512 = 513536 bytes
Disk identifier: 0x6f20736b

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   ?      775809     1913904   570754815+  72  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(357, 116, 40) logical=(775808, 8, 13)
Partition 1 has different physical/logical endings:
     phys=(357, 32, 45) logical=(1913903, 14, 4)
Partition 1 does not end on cylinder boundary.
/dev/sdc2   ?      168185     2098423   968014120   65  Novell Netware 386
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(288, 115, 43) logical=(168184, 16, 27)
Partition 2 has different physical/logical endings:
     phys=(367, 114, 50) logical=(2098422, 8, 24)
Partition 2 does not end on cylinder boundary.
/dev/sdc3   ?     1864289     3794527   968014096   79  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(366, 32, 33) logical=(1864288, 10, 12)
Partition 3 has different physical/logical endings:
     phys=(357, 32, 43) logical=(3794526, 1, 20)
Partition 3 does not end on cylinder boundary.
/dev/sdc4   ?           1     3626348  1818613248    d  Unknown
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(372, 97, 50) logical=(0, 0, 1)
Partition 4 has different physical/logical endings:
     phys=(0, 10, 0) logical=(3626347, 7, 42)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order




athlon% sudo mount -l
/dev/sda1 on / type ext3 (rw,noatime,nodiratime,errors=remount-ro,data=writeback) []
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-21-generic/volatile type tmpfs (rw)
/dev/sda3 on /home type ext3 (rw,relatime) []
/dev/sda4 on /media/share type ext3 (rw,relatime) [share]
securityfs on /sys/kernel/security type securityfs (rw)
rpc_pipefs on /var/lib/nfs/rpc_pipefs type rpc_pipefs (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/sdc on /media/disk type vfat (rw,nosuid,nodev,noatime,uhelper=hal,flush,uid=1000,utf8,shortname=lower) []



athlon% lsusb
Bus 002 Device 003: ID 1110:9021 Analog Devices Canada, Ltd (Allied Telesyn)
Bus 002 Device 002: ID 1532:0007
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 007: ID 4102:1017 iRiver, Ltd.
Bus 001 Device 004: ID 0424:2504 Standard Microsystems Corp. USB 2.0 Hub
Bus 001 Device 001: ID 0000:0000

```

strange output from fdisk -l but it's ok (formatted from iriver menu). why ubuntu doesnt find usb device automatically?

---

### Post by computer_freak_8 on 2008-11-23
@agblat: Your flash drive was plugged in when you ran these commands, correct? If so, it looks like it may be a hardware issue. Judging by the areas I have bolded:

> **agblat said:**
> katu@katu-desktop:~$ \dmesg | tail

[ 1182.584523]  sdb: sdb1

[ 1182.585946] sd 14:0:0:0: [sdb] Attached SCSI removable disk

[ 1182.586028] sd 14:0:0:0: Attached scsi generic sg3 type 0

[ 1182.593261] sr2: scsi3-mmc drive: 48x/48x tray

[ 1182.593371] sr 14:0:0:1: Attached scsi CD-ROM sr2

[ 1182.593439] sr 14:0:0:1: Attached scsi generic sg4 type 5

[B][ 1190.580725] usb 4-5: USB disconnect, address 14

[ 1190.581210] Buffer I/O error on device sdb1, logical block 1

[ 1190.581216] lost page write due to I/O error on sdb1

[ 1190.621480] scsi 14:0:0:0: rejecting I/O to dead device[/B]



...it seems like the drive might be failing. I'm no expert, though; it's just one guess.

As for the multiple home folder windows appearing, I know that on my system, whenever a folder no longer exists, but it was opened in a Nautilus window, that window turns into a window of the home folder, since (I think) this is the default location for Nautilus. What is sounds like to me, is that maybe it is auto-mounting and auto-unmounting very rapidly for some reason. This is the only thing I can think of right now that would cause this.

I'll be doing some searching, and I'll let you know what turns up.

---

### Post by computer_freak_8 on 2008-11-23
> **DuGi said:**
> strange output from fdisk -l but it's ok (formatted from iriver menu). why ubuntu doesnt find usb device automatically?

Not sure, but it may have something to do with the firmware on the iRiver. I know that I have a U3 flash drive that has similar oddities with "sudo fdisk -l" - is the flash drive you were using a U3 drive? Does it have any special firmware? What is the output if you use that drive with the commands?

Also - now this is just a thought - do the USB storage devices work if you run "lsusb", and then plug them in? (Instead of the other way around.) If so, as a workaround, you could set the "lsusb" command to run when you start your computer. (I could help you do this, if needed.) But, if it doesn't work when doing it in that order, there would be no point in having it run at startup.

I'll be searching, and let you know what I find.

---

### Post by agblat on 2008-11-23
Went to the KAL bug page and noticed that this appears to be an ongoung issue with 8.04 and 8.10 - it also appears in other Linux branding according to the KAL bug threads. Looks like they're still working on it. As to when a fix may make it into the menu of updates, that's for Kreskin. Again, thanks for your help.

---

### Post by DuGi on 2008-11-23
> **computer_freak_8 said:**
> Not sure, but it may have something to do with the firmware on the iRiver. [...]
the same problem is with pendrive and mmc card reader.

> **computer_freak_8 said:**
> Also - now this is just a thought - do the USB storage devices work if you run "lsusb", and then plug them in? (Instead of the other way around.)
nope. it's only working with plugged device. it is not very big problem to me but i'm happy when my operating system works perfectly :)

---

### Post by agblat on 2008-11-23
I reran the commands with the USB plugged in - this time it did recognize the flash drive:

katu@katu-desktop:~$ dmesg | tail
[42088.963614] FAT: Directory bread(block 2000) failed
[42088.963623] FAT: Directory bread(block 2001) failed
[42088.963632] FAT: Directory bread(block 2002) failed
[42088.963641] FAT: Directory bread(block 2003) failed
[42088.963650] FAT: Directory bread(block 2004) failed
[42088.963659] FAT: Directory bread(block 2005) failed
[42088.963668] FAT: Directory bread(block 2006) failed
[42088.963677] FAT: Directory bread(block 2007) failed
[42088.963686] FAT: Directory bread(block 2008) failed
[42088.963695] FAT: Directory bread(block 2009) failed

katu@katu-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=bd12e5fb-591c-4881-a81d-a47e22f3b78e /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=86fa2446-91ee-4cb2-ab92-e64db7247bdc none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

katu@katu-desktop:~$ sudo fdisk -l
Disk /dev/sda: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x24e624e5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7165    57552831   83  Linux
/dev/sda2            7166        7476     2498107+   5  Extended
/dev/sda5            7166        7476     2498076   82  Linux swap / Solaris

Disk /dev/sdc: 4022 MB, 4022337024 bytes
255 heads, 63 sectors/track, 489 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1         488     3919841    b  W95 FAT32
katu@katu-desktop:~$ lsusb
Bus 004 Device 014: ID 0781:5406 SanDisk Corp. Cruzer Micro 4GB Flash Drive
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 045e:0039 Microsoft Corp. IntelliMouse Optical
Bus 001 Device 001: ID 0000:0000  

katu@katu-desktop:~$ sudo mount -l
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro) []
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-21-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/katu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=katu)
/dev/sdb1 on /media/disk type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
/dev/sdc1 on /media/disk-1 type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush) []

Odd thing, the drive light alternately brightens and dims, each time bringing up another instance of Home Folder. At least is isn't a blue screen.

---

### Post by prshah on 2008-11-24
> **agblat said:**
> 
katu@katu-desktop:~$ dmesg | tail
[42088.963614] FAT: Directory bread(block 2000) failed
<snip>[42088.963695] FAT: Directory bread(block 2009) failed


There is some (logical) damage to the filesystem. You can clear it up (as well as the repetitive mounting) and remount it with ```

sudo umount /dev/sdc1
sudo fsck -a /dev/sdc1
sudo gnome-mount /dev/sdc1

```

---

### Post by lamps06 on 2008-11-24
I thought I should chime in since I have been silent for a while.  I installed 8.10 this morning (standard install, not the studio version of 8.04 I was running previously) and now my flash drive mounts fine.

I do not know if upgrading to 8.10 is an option for everyone in this thread but if you get a chance try burning a copy to CD and running it live.  That is what I did first to check and see if my USB drive would mount.

Good luck to everyone else.  I know how frustrating this issue is.

---

### Post by agblat on 2008-11-24
katu@katu-desktop:~$ sudo fsck -a /dev/sdcl
fsck 1.40.8 (13-Mar-2008)
fsck.ext2: No such file or directory while trying to open /dev/sdcl
/dev/sdcl: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

Received this in reply, but the 8gig flash did mount, there are no multiple loads of "Home Folder", and the flash drive led is steady. Whatever the underlying issue is it has led to black screen and cold reboot about 4x since surfacing. 

Thanks for your valuable input.

---

### Post by prshah on 2008-11-25
> **agblat said:**
> katu@katu-desktop:~$ sudo fsck -a /dev/sdcl
fsck 1.40.8 (13-Mar-2008)
fsck.ext2: No such file or directory while trying to open /dev/sdcl
/dev/sdcl: 

That's /dev/sdc**[SIZE="7"]1[/SIZE]** as in ONE, not lowercase letter "L".

---

### Post by lamps06 on 2008-11-25
Well, I spoke too soon.  Immediately after installing 8.10 the first thing I did was plug in my USB flash drive and it automounted fine.  I could read and write.  Cool.

Then I proceeded to modify my fstab so that my two internal IDE, NTFS formatted hard drives would mount automatically.  I rebooted.  My IDE drives mounted fine but when I plugged in my USB flash drive it no longer automounted!  I unmounted my IDE drives and manually mounted the USB flash drive into one of the folders where I mount my IDE drives and then I had read access to my USB drive but no write access.  What is going on here?  I am pretty sure I edited my fstab properly.  I will post it once I get home.

Anyone know why this could be affecting the automounting of my USB flash drive?  Thanks!

---

### Post by yarek on 2008-11-26
I'm having exactly the same problems on my AMD64 (Linux phoenix 2.6.24-21-generic #1 SMP Tue Oct 21 23:09:30 UTC 2008 x86_64 GNU/Linux). I can mount my USB drives using command-line manually, but it's a pain.  I'd like my drives to automount.  This isn't a problem on my x86.  

Any help would be appreciated.

Yarek

---

### Post by DuGi on 2008-11-26
i installed kernel 2.6.27-7-generic from intrepid repository and now automount working fine. i think its a problem with 2.6.24-* kernel.

---

### Post by lamps06 on 2008-11-26
Here is my fstab:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=fc1869c6-0cad-4d4c-b71a-3b26f23b5ab1 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=c797da93-e0fb-45b1-b703-25c2dcc930ff none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

######THESE ARE THE TWO ENTRIES I MADE####

# /dev/sdb1
UUID=E8909F03909ED800
/dev/sdb1	/media/Media_Drive	ntfs	defaults 0 0

# /dev/sdc1
UUID=C830453E3045352A
/dev/sdc1	/media/WinXP	ntfs	defaults	0	0

```

And here is the output of lsusb:

```

mateo@athlon:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 0457:0151 Silicon Integrated Systems Corp. Super Flash 1GB / GXT  64MB Flash Drive
Bus 003 Device 002: ID 0424:2504 Standard Microsystems Corp. USB 2.0 Hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

Also, I am not sure if it matters, but I running an AMD Athlon XP 1800+.

---

### Post by lamps06 on 2008-11-26
In addition I thought I should mention that when the USB drive does automount it is creating its own folder within /media/ and mounting itself there.  I thought that when USB drives and other devices automounted they did not create folders in /media/?  Am I incorrect?

And finally, one other item:  when I add the lines to my fstab to mount my IDE drives upon startup, they do indeed mount fine and they show up on my desktop and in nautilus.  However, their names are always just "30 GB Media" or "100 GB Media".  I thought their names were supposed to mirror the folders in /media/ where I tell them to mount, ie "Media_Drive" and "WinXP".  Again, am I not thinking correctly?

---

### Post by mc4man on 2008-11-26
> I thought that when USB drives and other devices automounted they did not create folders in /media/?

When they automount it's to /media/<volume label>

I label everything, internal, external. thumb drives

For all your labeling needs (for usb and internal
[https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

---

### Post by prshah on 2008-11-26
> **lamps06 said:**
> Here is my fstab:

```

######THESE ARE THE TWO ENTRIES I MADE####
# /dev/sdb1
UUID=E8909F03909ED800
/dev/sdb1	/media/Media_Drive	ntfs	defaults 0 0
# /dev/sdc1
UUID=C830453E3045352A
/dev/sdc1	/media/WinXP	ntfs	defaults	0	0

```


I'm not sure you can automount a USB device in this fashion, but you need to add the following options; just "defaults" is not enough.

defaults,relatime,auto

Eg,```
# /dev/sdb1
UUID=E8909F03909ED800
/dev/sdb1	/media/Media_Drive	ntfs	defaults,relatime,auto 0 0
# /dev/sdc1
UUID=C830453E3045352A
/dev/sdc1	/media/WinXP	ntfs	defaults,relatime,auto	0	0

```

---

### Post by lamps06 on 2008-11-27
Thanks for the suggestion, prshah, but I think you may have misunderstood me.  The two entries I added to my fstab were for my internal IDE drives.  When I add those entries my two internal drives mount fine but I lose the ability to automount my USB flash drive.  If I remove those two entries then my USB flash drive will automount fine but I have to manually mount my IDE drives.

Even still, I tried added your suggestions to my fstab and then neither my internal IDE drives or my USB flash drive would mount.

---

### Post by prshah on 2008-11-27
> **lamps06 said:**
> but I think you may have misunderstood me.  The two entries I added to my fstab were for my internal IDE drives.

Apologies; then of course my post is irrelevant.

---

### Post by lamps06 on 2008-12-02
Can anyone offer any suggestion here?  I am now running 8.10 (not studio) and if I leave my fstab along then my USB drive mounts fine.  However, if I add the two lines to my fstab (posted above) then my two internal IDE drives mount fine on startup but I lose the ability to mount my USB drive!  It is very frustrating.  Anyone?

---

### Post by lamps06 on 2008-12-05
Just wanted to let everyone know that my problem is finally resolved.  Check out [_this_]("http://ubuntuforums.org/showthread.php?t=1002088") link to see how I was able to fix my problem.  It was a pretty specific solution to my problem (namely a badly written fstab) but hopefully it will help a few other people.

Good luck!

---

### Post by vinceTX on 2008-12-07
To recap: I bought a new Corsair 16GB Flash Voyager thumb drive to load Ibex on Oct 30. It was put into an Asus EEEPC running Ibex but would not automount. It was put into a Mac, automounted and accepted Ibex. Later, it would not mount in my Hardy machine at home. (Original, not updated. This machine will automount 4 other makes of thumb drives.) But the Corsair would work fine in XP. I loaded Ibex from a CD onto my other machine. The Corsair would not work in this machine either.

Two days ago I was at a friends' house and the Corsair worked fine on a different Mac. I just plugged it into my Hardy machine and now it automounts. It creates an icon in Nautilus, identifies itself and reads fine. All problems are gone and I have no reason why. That's all I can say. Thanks or your patience.

---

### Post by VMbuseck on 2009-01-21
Is there any reasonable solution to get the USB automounting working again in 8.04 LTS ? I have several problems with hardy after the upgrade from dapper (VMware, kpdf, bootsplash, firefox, ...) and dont want to get back to back to dapper.

---

### Post by computer_freak_8 on 2009-01-24
> **VMbuseck said:**
> Is there any reasonable solution to get the USB automounting working again in 8.04 LTS ?
That is a very good question.

Alright, everyone in this thread that is still having problems: Try running the following commands. It has been a while now, as well as another kernel release for Hardy Heron.
```
sudo apt-get update
sudo apt-get upgrade
```

Also, try starting the Gnome Volume Manager by issuing the command:
```
gnome-mount
```

Also, if all of this does not work, and you are one of the people that is still having problems, post your /etc/fstab file.

---

