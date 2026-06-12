---
title: "Ubuntu Stalls During Bootup. Kernel Panic. Please Help!"
date: 2007-09-19
forum: General Help
---

### Post by ftblguy on 2007-09-19
Hi everyone,

I successfully installed Ubuntu back in July, and it had been running just fine until one day last week, I attempted to boot up in the morning, and it stalled during the Ubuntu splash screen (with the orange progress bar that scrolls from left to right). The progress bar goes about 10% of the way and then just stops
 forever. Upon pressing CTRL+ALT+F1, I can see this:

```
Starting up ...
Loading, please wait...
kinit: name_to_dev_t(/dev/disk/by-uuid/06f18f81-6248-48ed-aaa0-4412203d17e5) = sda5(8,5)
kinit: trying to resume from /dev/disk/by-uuid/06f18f81-6248-48ed-aaa0-4412203d17e5
kinit: No resume image, doing normal boot...
```

After another minute or so, it displays several more lines underneath the above:

```
[  139.341197] Out of memory: kill process 2721 (S10udev) score 58 or a child
[  139.341247] Killed process 2737 (udevmonitor)
[  139.367903] Out of memory: kill process 2721 (S10udev) score 42 or a child
[  139.367941] Killed process 2752 (udevsettle)
[  139.427883] Out of memory: kill process 2580 (rc) score 26 or a child
[  139.427922] Killed process 2580 (rc)
[  139.591850] Kernel panic - not syncing: Out of memory and no killable processes...
[  139.591894] <0>Kernel panic - not syncing: Out of memory and no killable processes...
[  139.591903]
[  139.591904]
```

But it never boots up all the way. I've tried (unsuccessfully) to boot up in safe mode, but still encounter the same problem. I am however able to boot successfully from the live CD. Does anyone have a clue as to what the problem here could be?

---

### Post by StewartM on 2007-09-19
> **ftblguy said:**
> Hi everyone,


```
Starting up ...
Loading, please wait...
kinit: name_to_dev_t(/dev/disk/by-uuid/06f18f81-6248-48ed-aaa0-4412203d17e5) = sda5(8,5)
kinit: trying to resume from /dev/disk/by-uuid/06f18f81-6248-48ed-aaa0-4412203d17e5
kinit: No resume image, doing normal boot...
```

After another minute or so, it displays several more lines underneath the above:

```
[  139.341197] Out of memory: kill process 2721 (S10udev) score 58 or a child
[  139.341247] Killed process 2737 (udevmonitor)
[  139.367903] Out of memory: kill process 2721 (S10udev) score 42 or a child
[  139.367941] Killed process 2752 (udevsettle)
[  139.427883] Out of memory: kill process 2580 (rc) score 26 or a child
[  139.427922] Killed process 2580 (rc)
[  139.591850] Kernel panic - not syncing: Out of memory and no killable processes...
[  139.591894] <0>Kernel panic - not syncing: Out of memory and no killable processes...
[  139.591903]
[  139.591904]
```

But it never boots up all the way. I've tried (unsuccessfully) to boot up in safe mode, but still encounter the same problem. I am however able to boot successfully from the live CD. Does anyone have a clue as to what the problem here could be?

I'm a complete newbie too so take my advice very guardedly.

But just a week ago, my new system hung on boot doing an fsck. Turned out it was due to errors on an externally connected (via USB port) hard drive. Simply turning that external HD "off" during boot meant that that error-filled drive was bypassed on bootup and things booted normally.

I note your first error involves "sda5". On my system, that's the filesystem partition the way that Dell configured it. Don't know what it means on yours. 

Two things I guess I would have tried:

a) from the live CD, see what partition sda5 refers to by browsing through Nautilus.

b) if it is something integral to your setup (i.e., not something that can be bypassed during boot)  maybe do a fsck of it?

If any real Linux gurus show up, help this guy out. If I'm telling you what you already know, please overlook that, I'm just trying to share what little I do know.

Stewart

---

### Post by ftblguy on 2007-09-19
From Device Manager, my Samsung 500GB SATA hard drive looks to be broken up into three volumes:
 -- Volume
 -- Volume (swap)
 -- Volume (ext)

sda5 refers to the "Volume (swap)". Should I try running a fsck on it?

---

### Post by nashjc on 2007-09-20
I'm having what I suspect is similar problem, but not on boot drive. Running Feisty 7.04

I installed a SATA 500GB recently. Then I started to get intermittent fsck failures on bootup. 

Noting that Knoppix has never given troubles -- of course after much playing with BIOS parameters etc -- I tried putting 2.6.20-15 at top of menu.lst in Grub. Also changed to nosplash from splash to see what is going on. Also commented out 'hiddenmenu'.  I can now see the fsck failure, but get intermittent fsck failures on the drive (always the 2nd partition, but the 1st partition isn't really there when I look on a failed bootup). I seem to get failures on both 2.6.20-16 and 15, but about 50% of the time. A solid, every-time failure would likely be easier to diagnose.

As far as I can tell, the bootup is failing to create /dev/sdc2 and is creating /dev/sdc1 wrongly. 

For info, when I get the single-user mode after failure, I can't even find dmesg, and get messages that apt-get is missing along with other annoyances.

Suggestions welcome. I suspect this is a perverse timing issue somewhere that a small change to a boot parameter will remove. But which parameter?

JN

---

### Post by StewartM on 2007-09-20
> **ftblguy said:**
> From Device Manager, my Samsung 500GB SATA hard drive looks to be broken up into three volumes:
 -- Volume
 -- Volume (swap)
 -- Volume (ext)

sda5 refers to the "Volume (swap)". Should I try running a fsck on it?

You could, or could just turn it "off" and try booting that way (if you have enough physical RAM).

Stewart

---

### Post by nashjc on 2007-09-20
Just to update -- I've now had one failure in Knoppix after getting locked out 3 times with Feisty kernels 2.6.20-15 and -16. Beginning to look a bit like hardware. Sigh.

JN

---

### Post by nashjc on 2007-10-06
Removed Promise Ultra 133 TX2 card and machine now fine. So problem seems to have been hardware or at least a hardware incompatibility.

Promise is working partially in another (test only) machine. However, it gave sufficient trouble with 4 devices on it that I removed 2 (on one IDE port). Could, however, have been a flakey drive on that port.  The test machine is a much slower box (2GHz Celeron vs 3GHz dual P4), and I believe is only running ATA100 (have not verified -- not of high importance just now).

---

