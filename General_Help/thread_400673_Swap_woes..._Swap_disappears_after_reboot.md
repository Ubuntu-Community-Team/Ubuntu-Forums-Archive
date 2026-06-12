---
title: "Swap woes... Swap disappears after reboot"
date: 2007-04-03
forum: General Help
---

### Post by jakev383 on 2007-04-03
I resized my partitions - I shrunk my ext3 partition for Ubuntu by 900M (sda6) and then grew my swap partition to use the available space (sda7). 
But every time I reboot my swap goes away:
root@jake-lapbox:~# free -m
             total       used       free     shared    buffers     cached
Mem:          2018        430       1588          0          6        108
-/+ buffers/cache:        314       1704
Swap:            0          0          0

I did run mkswap to format the space to all be swap, and recorded the new UUID and added that to my fstab:

root@jake-lapbox:~# cat /etc/fstab
# /etc/fstab: static file system information.
#
<snip>
# /dev/sda7
# Before I changed partition size....
#UUID=5b9c8177-5d02-438e-9bb4-fe8f6fe05e46 none            swap    sw              0       0
UUID=2a74abff-b7af-4a0d-86cf-b85d7e95ff42 none swap sw 0 0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

Here's my layout:

root@jake-lapbox:~# fdisk -l

Disk /dev/sda: 118.5 GB, 118526284800 bytes
255 heads, 63 sectors/track, 14410 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2   *           6        2011    16113195    7  HPFS/NTFS
/dev/sda3           13804       14409     4867695   db  CP/M / CTOS / ...
/dev/sda4            2012       13803    94719240    5  Extended
/dev/sda5            3593       13803    82019826    b  W95 FAT32
/dev/sda6            2162        3592    11494476   83  Linux
/dev/sda7            2012        2161     1204812   82  Linux swap / Solaris

Partition table entries are not in disk order

Not having swap space makes it a little difficult to hibernate my laptop.... Does anyone have any ideas?
Thanks in advance!

---

### Post by taurus on 2007-04-03
Edit /etc/fstab

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/fstab
```
and replace this line
```
UUID=2a74abff-b7af-4a0d-86cf-b85d7e95ff42 none swap sw 0 0
```
with this one.

```
/dev/sda7   none   swap   sw   0   0
```
Save it and then reboot.  Now, what happens when you run this command from a terminal again?

```
free
```

---

### Post by jakev383 on 2007-04-04
Here's what I got:

root@jake-lapbox:~# free
             total       used       free     shared    buffers     cached
Mem:       2066716     443384    1623332          0      12520     213240
-/+ buffers/cache:     217624    1849092
Swap:            0          0          0

And when I try swapon -a:

root@jake-lapbox:~# swapon -a
swapon: /dev/sda7: Invalid argument

So I try mkswap again:

root@jake-lapbox:~# mkswap /dev/sda7
Setting up swapspace version 1, size = 1233723 kB
no label, UUID=ff4a2197-e0ad-4eb5-92b2-b92c52725e22
root@jake-lapbox:~# swapon -a
root@jake-lapbox:~# free
             total       used       free     shared    buffers     cached
Mem:       2066716     508088    1558628          0      13168     275220
-/+ buffers/cache:     219700    1847016
Swap:      1204804          0    1204804

Now in my fstab all my mounts are by UUID, not dev name. Would that make a difference?

Thank for the help

---

### Post by taurus on 2007-04-04
> **jakev383 said:**
> 
So I try mkswap again:

root@jake-lapbox:~# mkswap /dev/sda7
Setting up swapspace version 1, size = 1233723 kB
no label, UUID=ff4a2197-e0ad-4eb5-92b2-b92c52725e22
root@jake-lapbox:~# swapon -a
root@jake-lapbox:~# free
             total       used       free     shared    buffers     cached
Mem:       2066716     508088    1558628          0      13168     275220
-/+ buffers/cache:     219700    1847016
Swap:      1204804          0    1204804

Now in my fstab all my mounts are by UUID, not dev name. Would that make a difference?

Thank for the help

Well, your swap partition is activated now and no, it doesn't matter if you use UUID or the actual partition name in /etc/fstab.

---

### Post by shotgunefx on 2007-04-04
Is this a laptop? I had a [similar problem ](http://ubuntuforums.org/showthread.php?t=394649) when I installed suspend2 and didn't configure initrd correctly.

---

### Post by jakev383 on 2007-04-04
> **shotgunefx said:**
> Is this a laptop? I had a [similar problem ](http://ubuntuforums.org/showthread.php?t=394649) when I installed suspend2 and didn't configure initrd correctly.
Yes it is a laptop, but everything worked fine before I resized the partitions - that's what kills me.

I did try and hibernate it and as soon as I booted it back up, it did not resume the session (started new) and lost my swap again:

root@jake-lapbox:~# free
             total       used       free     shared    buffers     cached
Mem:       2066716     483696    1583020          0      62800     184312
-/+ buffers/cache:     236584    1830132
Swap:            0          0          0

doing a swapon -a gives me an error that /dev/sda7 is an invalid argument; I ran mkswap /dev/sda7 and then swapon -a and all was well again. I'm going to try shutting the thing down and see if it's only the hibernate that does it....

---

### Post by shotgunefx on 2007-04-04
> **jakev383 said:**
> Yes it is a laptop, but everything worked fine before I resized the partitions - that's what kills me.

I did try and hibernate it and as soon as I booted it back up, it did not resume the session (started new) and lost my swap again:

root@jake-lapbox:~# free
             total       used       free     shared    buffers     cached
Mem:       2066716     483696    1583020          0      62800     184312
-/+ buffers/cache:     236584    1830132
Swap:            0          0          0

doing a swapon -a gives me an error that /dev/sda7 is an invalid argument; I ran mkswap /dev/sda7 and then swapon -a and all was well again. I'm going to try shutting the thing down and see if it's only the hibernate that does it....

Strange, I hit it after doing a custom kernel upgrade. Anything in dmesg?

---

### Post by jakev383 on 2007-04-04
Booting from a full shutdown seems to work okay, so maybe it's only when I hibernate the thing. I'll check your link out later about the initrd. I'm assuming I probably need to modify something in there since the UUID changed for the swap partition....
Thanks.

---

### Post by shotgunefx on 2007-04-04
> **jakev383 said:**
> Booting from a full shutdown seems to work okay, so maybe it's only when I hibernate the thing. I'll check your link out later about the initrd. I'm assuming I probably need to modify something in there since the UUID changed for the swap partition....
Thanks.

Are you using suspend2 or software supend? I know suspend2 usually references it by name swap:/dev/hdxy, so as long as you have it all set in fstab by uuid or name, don't think you'll have to do anything as far as suspend config as long as the partition name doesn't change.

But if you haven't installed a new kernel, I don't know why it would be doing that (screwing initrd). Did you try and resume after the resize? Meaning, have you booted clean, fixed the swap, then tried suspending?

---

### Post by jakev383 on 2007-04-04
> **shotgunefx said:**
> Are you using suspend2 or software supend? I know suspend2 usually references it by name swap:/dev/hdxy, so as long as you have it all set in fstab by uuid or name, don't think you'll have to do anything as far as suspend config as long as the partition name doesn't change.

But if you haven't installed a new kernel, I don't know why it would be doing that (screwing initrd). Did you try and resume after the resize? Meaning, have you booted clean, fixed the swap, then tried suspending?

I'm using kernel 2.6.17-11-generic and whatever suspend package came with Ubuntu.... It always worked before, so I didn't fix it (okay, it worked 75% of the time) And I just booted into it for the second time from a cold start and my swap is fine. If I try and hibernate it loses the swap (upon reboot) and boots up like it was never hibernated. And that is AFTER the resize... Do you know what file it would reference the partition so I can make sure it's okay?
Thanks again.

---

### Post by jakev383 on 2007-04-04
I checked around a little and found this in my /etc/acpi/hibernate.sh file:
if [ -x /sbin/s2disk ]; then
    DEVICE="/dev/disk/by-uuid/`awk -F= '{print $3}' </etc/initramfs-tools/conf.d/resume`"
    if [ -f /etc/usplash.conf ]; then
        . /etc/usplash.conf
        /sbin/s2disk -x "$xres" -y "$yres" $DEVICE
    else
        /sbin/s2disk $DEVICE
    fi

It looks like it's referencing it by UUID. I'll try and modify this script this evening and look at the resume script as well.

---

### Post by shotgunefx on 2007-04-04
> **jakev383 said:**
> I checked around a little and found this in my /etc/acpi/hibernate.sh file:
if [ -x /sbin/s2disk ]; then
    DEVICE="/dev/disk/by-uuid/`awk -F= '{print $3}' </etc/initramfs-tools/conf.d/resume`"
    if [ -f /etc/usplash.conf ]; then
        . /etc/usplash.conf
        /sbin/s2disk -x "$xres" -y "$yres" $DEVICE
    else
        /sbin/s2disk $DEVICE
    fi

It looks like it's referencing it by UUID. I'll try and modify this script this evening and look at the resume script as well.

Well, had the right idea anyway. :) Strange that my scripts don't do that. I was running edgy, then built 2.6.20 and hacked all hell out of the acpid support stuff.

---

### Post by jakev383 on 2007-04-04
Agreed - on the right track. I see that in /etc/initramfs-tools/conf.d I had a file called "resume" that had:
RESUME=UUID=5b9c8177-5d02-438e-9bb4-fe8f6fe05e46
Which was the old UUID before I grew the swap size. I changed this file to read:
RESUME=/dev/sda7
I also edited the hibernate.sh script in /etc/acpi to read:
#    DEVICE="/dev/disk/by-uuid/`awk -F= '{print $3}' </etc/initramfs-tools/conf.d/resume`"
        DEVICE=/dev/sda7

In the hopes that it would use /dev/sda7 instead of the UUID. I also created symlinks in the /dev/disk/by-uuid dir for the various UUID's to point to ../../sda7 like the rest of the links in there.
Now when I try and hibernate, I get something about not being able to find the swap space and it comes back up into Gnome (locked screen, like I just returned from the screensaver) and my swap is missing again.... I had to mkswap /dev/sda7 and then swapon -a to get it activated again.
Is there a way to dpkg-reconfigure the whole thing so it works right again? I'd rather not reformat my system to get everything back to normal, since I've only stopped dual booting for the last 2 weeks, and am not comfortable losing my Win partition just yet.... I also don't want to lose all the customizations I've done in Ubuntu.....
Any suggestions are appreciated! And thanks for the help so far!

---

### Post by shotgunefx on 2007-04-04
> **jakev383 said:**
> Agreed - on the right track. I see that in /etc/initramfs-tools/conf.d I had a file called "resume" that had:
RESUME=UUID=5b9c8177-5d02-438e-9bb4-fe8f6fe05e46
Which was the old UUID before I grew the swap size. I changed this file to read:
RESUME=/dev/sda7
I also edited the hibernate.sh script in /etc/acpi to read:
#    DEVICE="/dev/disk/by-uuid/`awk -F= '{print $3}' </etc/initramfs-tools/conf.d/resume`"
        DEVICE=/dev/sda7

In the hopes that it would use /dev/sda7 instead of the UUID. I also created symlinks in the /dev/disk/by-uuid dir for the various UUID's to point to ../../sda7 like the rest of the links in there.
Now when I try and hibernate, I get something about not being able to find the swap space and it comes back up into Gnome (locked screen, like I just returned from the screensaver) and my swap is missing again.... I had to mkswap /dev/sda7 and then swapon -a to get it activated again.
Is there a way to dpkg-reconfigure the whole thing so it works right again? I'd rather not reformat my system to get everything back to normal, since I've only stopped dual booting for the last 2 weeks, and am not comfortable losing my Win partition just yet.... I also don't want to lose all the customizations I've done in Ubuntu.....
Any suggestions are appreciated! And thanks for the help so far!

Not sure on reconfiguring as I did a kernel patch and a manual install.

I'd create the swap, change the resume file to point to the correct UUID and then shutdown (instead of hibernating) then when you come up again, see if it hibernate/resume correctly.

Hope that helps.

---

### Post by shotgunefx on 2007-04-04
Do'h. Not thinking.

Don't you have to reinstall the kernel image to get it to rebuild initrd? That's probably the problem.

---

### Post by jakev383 on 2007-04-05
> **shotgunefx said:**
> Do'h. Not thinking.

Don't you have to reinstall the kernel image to get it to rebuild initrd? That's probably the problem.

Not sure. I went trolling through the forum searching for "hibernate.sh" and see a lot of threads with people that are having the exact same problem as me. Most of them think it's tied to the new kernel. I tried the .10 kernel but that one didn't solve anything. I couldn't go any further back since I cleaned up a little and deleted the older versions :( 
Oh well. Suspend works great for me. I can use that I guess. I get 4-5 hours out of a battery now in full-use mode, so suspend should work instead of hibernating until this gets fixed - or I move to Fiesty......

---

### Post by shotgunefx on 2007-04-05
> **jakev383 said:**
> Not sure. I went trolling through the forum searching for "hibernate.sh" and see a lot of threads with people that are having the exact same problem as me. Most of them think it's tied to the new kernel. I tried the .10 kernel but that one didn't solve anything. I couldn't go any further back since I cleaned up a little and deleted the older versions :( 
Oh well. Suspend works great for me. I can use that I guess. I get 4-5 hours out of a battery now in full-use mode, so suspend should work instead of hibernating until this gets fixed - or I move to Fiesty......

Well, I think if you modify the script to use the /dev/hdxy syntax, or put the right uuid in the resume file, then just reinstall the current kernel image, it will fix it.

---

### Post by jakev383 on 2007-04-05
> **shotgunefx said:**
> Well, I think if you modify the script to use the /dev/hdxy syntax, or put the right uuid in the resume file, then just reinstall the current kernel image, it will fix it.

I think it has the right UUID now. Would it just be dpkg-reconfigure linux-image-$(uname -r) ?

---

### Post by shotgunefx on 2007-04-05
> **jakev383 said:**
> I think it has the right UUID now. Would it just be dpkg-reconfigure linux-image-$(uname -r) ?

I *think* that would do it.

 I'm not extremely familar with how installing a kernel works to be honest. I've groked enough to fix my problems, but I don't know if reconfigure would rebuild initrd or not. I think so. Have to ask someone who knows more :)

---

### Post by shotgunefx on 2007-04-13
Ever get that straightened out?

---

### Post by jakev383 on 2007-04-13
Sort of -  I just quit using hibernate. It only takes a couple seconds longer for me to boot from a cold machine anyway (2G RAM). For those times that I know I'll need to keep what's open open for the next couple hours I'll just suspend it. Suspend works, but my screen savers don't work after a suspend. Screen still blanks, and it's not enough for me to worry about right now.
Thanks!

---

### Post by sudo_nym on 2007-04-19
> **jakev383 said:**
> I checked around a little and found this in my /etc/acpi/hibernate.sh file:
if [ -x /sbin/s2disk ]; then
    DEVICE="/dev/disk/by-uuid/`awk -F= '{print $3}' </etc/initramfs-tools/conf.d/resume`"
    if [ -f /etc/usplash.conf ]; then
        . /etc/usplash.conf
        /sbin/s2disk -x "$xres" -y "$yres" $DEVICE
    else
        /sbin/s2disk $DEVICE
    fi

It looks like it's referencing it by UUID. I'll try and modify this script this evening and look at the resume script as well.

Thanks, this helped.

I've had no trouble resuming from hibernation, and can't address that.  But more often than not, the standard `Hibernate' option just doesn't do anything.  I push the button, wait, and the desktop just sits there like nothing happened.  Like you, I also lose swap after every reboot.  Don't know why.

But here's why I found your post so helpful: Even when `Hibernate' has no effect, a direct; ```
sudo /etc/acpi/hibernate.sh
``` from the terminal works just fine.  Again, I have no idea why.

So now I have a custom `Launcher' button on the menubar, and the command it executes is; ```
gksu /etc/acpi/hibernate.sh
```

Seems to work, but I *don't* know if it's the Right Thing.  Actually, I would appreciate some advice on this, just in case it's the Wrong Thing...  :-\

And here's a simple-minded, four-line boot script [not counting comments] for my swap problem.  Again, I don't know if this is a good idea, and would appreciate some advice on it.

Actually, it's two scripts.  The first is /etc/init.d/swapple ;
```
#!/bin/sh

echo "Fixing swap..."

/usr/local/bin/swapple2 &
```

And here's why there's two.  Note the trailing `&' on that last line.  This means it will launch the secondary script, without waiting for it to finish.

Here's /usr/local/bin/swapple2 ;

```
#!/bin/sh

sleep 22
#
##  Wait 22 seconds, just in case another boot script is making
##  a mistake when *it* tries to activate swap.  You should see your
##  desktop before `swapple2' actually finishes.

##  Just in case the system [mistakenly] thinks there is an active
##  swap partition...
#
swapoff -a

##  Please CHANGE the following to reflect your setup, and
##  please don't make swap on the wrong partition, especially
##  if it contains anything you want to keep.
#
mkswap /dev/hda6
swapon /dev/hda6

echo "Done, I hope..."
```

To enable the boot script, I needed sysvconfig from the Debian software channels.  I honestly have no idea what files it modified, but it seemed to make all the right changes, in all the right places.  Don't know if it conflicts with any of the primary Ubuntu fare, but Synaptic didn't complain about installing it.


Good luck,

Patrick.

---

### Post by jakev383 on 2007-04-20
Hmm. And that works? The swap thing, even with using your hibernate work around?

---

### Post by sudo_nym on 2007-04-21
> **jakev383 said:**
> Hmm. And that works? The swap thing, even with using your hibernate work around?

Seems to.  I mean, it's exactly the same as you typing those commands into the terminal, after every boot.

But right after posting that [always seems to happen right *after* I say something...], I found out there's a much simpler way to do it; edit /etc/fstab and drop the `UUID=...' stuff for regular old `/dev/hdaN' entries.

[http://ubuntuforums.org/showthread.php?t=287096&page=3]("http://ubuntuforums.org/showthread.php?t=287096&page=3")
[Page 3 of 3, but you might want to have a look at the whole thread.]

So now my fstab looks like this;

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
/dev/hda1 /               ext2    defaults,errors=remount-ro 0       1
# /dev/hda5
/dev/hda5 /home           ext2    defaults        0       2
# /dev/hda6
/dev/hda6 none            swap    sw              0       0
/dev/hdb        /media/cdrom0   auto user     0       0
/dev/fd0           /media/floppy0  auto    rw,user,noauto  0       0
```

I've kept the `swapple' script around, but disabled, and haven't needed it since.  The standard `Hibernate' still doesn't work most of the time, so I'm still using the launcher button for that.

As said, I haven't had the same trouble resuming from hibernation, so I don't know if either approach would help you.  Hope it does though.

And just in case it doesn't, do backup of your fstab before trying that [if you try it, that is], and do make sure you've got a CD or something to boot from, just in case you need to go back and fix it.


Good luck,

Patrick.

---

