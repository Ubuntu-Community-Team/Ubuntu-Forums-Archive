---
title: "Several Problems With Ubuntu - Who Can Solve Them All?  =]"
date: 2008-03-04
forum: General Help
---

### Post by benf101 on 2008-03-04
I have several problems that are preventing me from having the perfect Ubuntu experience.  Here we go:

[LIST=1]

[*]Vista Will Not Boot
     I loaded Vista first and Ubuntu next.  The Vista/Longhorn option comes up but after I select it, Windows tells me to choose "Safe Mode", etc... 
     I have tried the repair option on the Vista installation cd with no success.  I don't think it's the MBR because I during the repair, I ran the DOS prompt and entered "bootrec /fixmbr" and "bootrec /fixboot".  The start up then ignored the fact that Ubuntu existed and attempted to boot Vista, but never got past the initial start-up screen.  (The one where the green block scrolls across the bar.)
     So, I used the Ubuntu CD and fixed grub and now Ubuntu starts again, but Vista won't.  That's where I am at.
:confused:
[*]I cannot find where to identify what kind of video card I have so I can update my video driver
     KDenLive runs like garbage while previewing sections of video where effects have been applied.  Basically, the video drags while the audio keeps the right pace, causing them to be out of sync.  I *think* that may be because of my video card driver since Microsoft Video Maker has no problem handling this.
:confused:
[*]Some partitions need to be merged or expanded
     My swap partition is quite dinky, at about 878mb, where I have been told it should be double my RAM size, or 2 gigs.  I have many gigs that are partitioned but unformatted (and therefore unused) due to my failed attempts at Ubuntu installation.  GParted is incapable of merging partitions.  How can I expand my SWAP file and merge unused partitions into usable partitions?
:confused:
[*]DVD Styler has been installed but doesn't start.  After clicking it in the start menu, the taskbar says "Starting DVD Styler" but then it disappears and never starts.  I'm not sure where to go from there.  I've already tried reinstalling, but no dice.
[/LIST]

If it helps, here's what I'm dealing with:
- Dell with overseas support
- 3.2 ghz intel pentium 4 (hyperthread, if it matters)
- 1 gig RAM
- 160 gig hard drive
- 3 kids screaming while I'm trying to concentrate on this

I have tried looking it up on this forum already and couldn't find answers.  Please don't be one of those dweebs who yell at people because someone else already asked the question.

Thanks for any help you can offer. :)

==========================
Added information:
[http://infreedomscause.com/files/dell_screenshot.png](http://infreedomscause.com/files/dell_screenshot.png) to see packing slip with hardware specifics
========================

---

### Post by logos34 on 2008-03-04
1. Did you leave space for ubuntu when you installed vista, or did you use the whole disk then shrink it down with gparted during ubuntu install?  If the latter that, that could be the problem, which means you need to reinstall vista.  (If you have to resize vista, use it's own disk management tool). 

2. (in a terminal):
[B]
lspci[/B]

3. Actually the rule of thumb is twice you ram **up to ~1 gb max** (over that 1x is enough, with the exception of power usage like video editing or graphics design, etc.).  So it's fine the way it is (although hibernating may be a prob). 

You might want to post a screenshot of gparted, or the output of **sudo fdisk -l**. You are correct--you can't merge partitions but you could just do swapoff, delete it, shrink an adjacent partition and create a new slightly larger swap.

---

### Post by benf101 on 2008-03-05
Here's a screenshot of my partitions:

[IMG]http://infreedomscause.com/files/partitions_screenshot.png[/IMG]

---

### Post by benf101 on 2008-03-05
And just for good measure, here's the gparted version:

[IMG]http://infreedomscause.com/files/Screenshot--dev-sda - GParted.png[/IMG]

If I use part of that 8gig partition for my swap, how do I tell Ubuntu to begin using *that* drive as swap and not the other?

No matter how I slice it, it seems that my drive is a bit sloppy now.  I'd love to clean it up without reinstalling everything, if that's possible.

---

### Post by logos34 on 2008-03-05
It's hard to know what happened with vista.  I don't have any experience using it, so not sure what to suggest beyond what you've already tried, except maybe to run the vista-equivalent of **chkdsk**.

As far as the swap is concerned, the more pressing issue is that you seem to be running out of room for root, and could use the space occupied by swap.  So I'd definitely delete it (along with the extended partition sda3 that contains it), and make a slightly larger one (**primary** linux-swap) at the head of the disk.  Then unmount vista partition and grow it to the left to take up leftover space.  Edit /etc/fstab so the swap line matches the new location. Ge tthe new UUID with

**blkid**

or just use the format

> /dev/sda3 none swap sw 0 0

Since root cannot be mounted when resizing you'll have to use gparted on the ubuntu live cd to grow sda1 to the right.

---

