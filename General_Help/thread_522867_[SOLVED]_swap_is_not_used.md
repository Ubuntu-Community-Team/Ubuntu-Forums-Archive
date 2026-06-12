---
title: "[SOLVED] swap is not used"
date: 2007-08-11
forum: General Help
---

### Post by kaurman on 2007-08-11
Hi!

I'm using Feisty and as you can probably guess by now, I'm having problems with swap.

At first it was twice as big as the swap partition and was not used. I fixed that by geting rid of the swap partition's UUID in fstab and replacing that with /dev/sda5 (which is my swap partition).

For a while everything worked fine, but now I am unable to hibernate/suspend and swapspace is always 0% used even when ram (1016 MB) is 50% full.  The size of the swap is still correct though.

To sum it all up: how can I get the computer to use swap again?

Thanks in Advance,

Kaur

---

### Post by HermanAB on 2007-08-11
The commands are 'swapon' and 'swapoff'.

Swap space is used during an 'emergency' to keep Linux running when it is heavily loaded, instead of grinding to a halt due to a lack of memory.  It is also used to store the machine state during suspend as you found out.

Cheers,

Herman

---

### Post by mikewhatever on 2007-08-11
With 2 GB of RAM, you'll hardly ever need to swap, except when hibernating. What is the size of the swap partition now?

---

### Post by kaurman on 2007-08-11
My swap partition is about 1,52 GB and the total amount of RAM is 1016 MB. I know that my computer can work just fine without the swap, but because it's a laptop, hibernation/suspend are important- 

When things used to work right usually about 1-2% of swap was used.

Kaur

---

### Post by Midahed on 2007-08-11
What do you get if you run the free command in a terminal session?

Mike

---

### Post by kaurman on 2007-08-11
Hello again,

free gives:

```

             total       used       free     shared    buffers     cached
Mem:       1027412     838192     189220          0     177404     349136
-/+ buffers/cache:     311652     715760
Swap:      1598428          0    1598428

```

Kaur

---

### Post by Midahed on 2007-08-11
That looks OK.  If it didn't see it as swap space, I would expect to see 0 0 0 as the total, used and free swap entries.

I don't know the answer, but maybe there another reference to the swap partition that still uses the old UUID, and that's what's screwing things up when you try to hibernate?

Does swapon -a make any difference?

Have you tried using free -s 5 to see if it ever actually swaps under normal use?

Mike

---

### Post by kaurman on 2007-08-11
Hi!

Thanks for taking the time to look into my problem.

> That looks OK. If it didn't see it as swap space, I would expect to see 0 0 0 as the total, used and free swap entries.

It seems that swap is seen (by 'free' or gnome-system-monitor). The problem is that the use of it is always 0%. I would expect about 1-2% usage as earlier.


> Have you tried using free -s 5 to see if it ever actually swaps under normal use?
 
The "swap" line stays the same all the time:
```

             total       used       free     shared    buffers     cached
Mem:       1027412     762204     265208          0      15460     352796
-/+ buffers/cache:     393948     633464
Swap:      1598428          0    1598428

             total       used       free     shared    buffers     cached
Mem:       1027412     763204     264208          0      15468     352796
-/+ buffers/cache:     394940     632472
Swap:      1598428          0    1598428

             total       used       free     shared    buffers     cached
Mem:       1027412     763336     264076          0      15476     352796
-/+ buffers/cache:     395064     632348
Swap:      1598428          0    1598428

             total       used       free     shared    buffers     cached
Mem:       1027412     763336     264076          0      15484     352796
-/+ buffers/cache:     395056     632356
Swap:      1598428          0    1598428

```

'swapon -a' didn't seem to make a difference

So it looks like my laptop just refuses to use swap.

Any help would be great.

With Best Wishes,

Kaur

---

### Post by Midahed on 2007-08-12
What does your /etc/fstab look like?

Mike

---

### Post by kaurman on 2007-08-12
Hello,

Here' s my fstab:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1 -- converted during upgrade to edgy
UUID=1843e5cf-c985-41cc-b638-2497c08d955d / ext3 defaults,errors=remount-ro 0 1
# /dev/hda5 -- converted during upgrade to edgy
/dev/sda5 none swap sw 0 0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
```

PS

After a bios ubdate /dev/hda5 is seen as /dev/sda5, but the trouble started before all that. I just changed the fstab after the update.

'Top' shows some cached swap and the number is even changing... Don't know what that means though :)

Kaur

---

### Post by Midahed on 2007-08-12
Are you absolutely sure you really have a problem?

I've just tried to make my system swap and it's quite difficult to achieve.  

If you have a 'decent' amount of memory by today's standard, you have to load the system quite heavily to get it to swap. I had several goes at loading a dozen applications or so, and it never swapped - even with 90% of memory used.  Eventually I started a search of the entire root filesystem for a file containing a long string (is was a UUID as it happens).  That really slowed it down and it did start to swap very heavily - to the point where it was slow to respond to mouse clicks, keyboard characters weren't echoed in a terminal session for 5-15 seconds, mouse pointer movements got very jerky, etc.

Try doing that.  You may find that it will then start to swap.

Mike

---

### Post by kaurman on 2007-08-12
I checked, and it really does use swap... Even when only 40% of RAM is used... As you can see from my previous posts there used to be no swap usage even when 50% of ram was full.
Strange.

The good news is that swap seems to work. The bad one is that I'll now have to trace the hibernation/suspend problem from somewhere else :)

Many thanks for your help.

Kaur

---

### Post by Midahed on 2007-08-13
> **kaurman said:**
> ....The bad one is that I'll now have to trace the hibernation/suspend problem from somewhere else :)
They're fairly old bugs, but there is some interesting stuff here in relation to UUIDs and hibernation problems.

[https://bugs.launchpad.net/ubuntu/+source/udev/+bug/105490](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/105490)
[https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/66637](https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/66637)

There's a fair bit to read through, but it seems that there is another place that the swap partition UUID is recorded.  This might be your problem.

*- Edit resume with correct non-UUID information: $ sudo gedit /etc/initramfs-tools/conf.d/resume*

The general recommendation seems to be that UUIDs should be replaced by /dev/sdax, etc, wherever they arise.

Hope this helps.

Mike

---

### Post by kaurman on 2007-08-13
Thanks for the links. 

I've always had trouble with hibernation. The thing that depresses me the most is the fact that the whole hibernation/suspend system is so unpredictable. Even if I've managed to fix suspend/hibernation once I still can't be sure that it keeps working.

But I guess that's Linux... It was my own choice to use the latest stable release while some of the previous ones may well be a bit more stable.


Kaur

---

### Post by flamacue on 2007-11-22
I'm running 7.04 (Feisty) on my Dell Inspiron 700m laptop.  Hibernate stopped working after I remade my swap partition.

The UUID of the swap partition changed when I recreated it, and hibernate no longer worked.  Also, the device mappings changed (swap changed from /dev/sda5 to /dev/sda7, and / changed from /dev/sda6 to /dev/sda5).  The system still booted fine, though, since /etc/fstab uses UUID's.  The swap was mounted and activated (swapon), as evidenced by "free".  However, when I tried to hibernate, it said it couldn't find the swap device, and to try swapon -a.  (Tried it, made no difference.)

Editing /etc/initramfs-tools/conf.d/resume to use the new UUID did not solve the issue.  Editing it to use the new block device ("RESUME=/dev/sda7") did the trick.  (I think I also ran "sudo update-initramfs -u", but I'm not sure if that was necessary or not.)

---

