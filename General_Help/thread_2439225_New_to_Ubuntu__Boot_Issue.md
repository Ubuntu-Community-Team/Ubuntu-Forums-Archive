---
title: "New to Ubuntu / Boot Issue"
date: 2020-03-24
forum: General Help
---

### Post by mistadan on 2020-03-24
I'm an experienced network tech, but have little experience with Ubuntu beyond setting it up for use as a workstation. I was handed a machine that updated, now has zero space, and won't boot. Unfortunately, I can't boot into any of the old kernels either. Here's what I'm seeing:


[LIST=1]
[*]When I boot the box, I get a GRUB (ver 2.02) message that allows me to select Ubuntu or Advanced options. If I pick the Ubuntu option it pops an error "failure reading sector ox111e9e8 from 'hd0'". That error will automatically roll to what looks like an attempt to boot that ends in "end Kernel panic - not syncing: VFS: unable to mount root fs on unknown-block(0,0)".
[*]If I boot the box and select "Advanced options for Ubuntu" I get what I think is a list of kernels, each with a recovery mode option. There is 4.15.0-55 and 4.15.0-54. Selecting any of these leads to a loading screen that attempts to load linux, throws error "failure reading sector 0x12046b80 from 'hd0'" and attempts to load initial ramdisk and errors with "you need to load the kernel first. Pressing any key to continue takes me back to the end Kernel panic unable to mount root error mentioned above.
[*]If I boot to GRUB using the esc. key and use ls, I get "(hd0) (hd0,gpt2) (hd0,gpt1)"
[/LIST]
At this point I've exhausted my bag of tricks, I'm in a little over my head and I'm hoping somebody here can lend a hand.

Thanks!

---

### Post by Bashing-om on 2020-03-24
mistadan; Hello -

The advisory "failure reading sector 0x12046b80 from 'hd0' " makes me think what we have here is either software corruption and/or hardware failure.

In this situation, first up is to see what a file system check reveals.

Let's prepare to run fsck; hd0 is grub speak for the 1st hard drive, sda.
From a live environment - the desktop installer, run:
```

sudo parted -l

```
post that output back here in the thread - so we know what the target(s) are to point the file system check to.
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

After the file system check we see where we go from here.

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by andysharpie on 2020-04-10
I had the "kernel panic" occur on a machine recently. During that process, I stopped by this thread, but then had trouble finding a live environment which supported "sudo," or "parted" as commands, as Grub certainly did not. How do you get to this environment?

---

### Post by Bashing-om on 2020-04-10
andysharpie; Hello -

> 
How do you get to this environment?


Boot the live desktop installer in "try ubuntu" mode.
Once the desktop is loaded key combo ctl+alt+t will activate a terminal interface.

[INDENT]my bit to try and help
[/INDENT]

---

