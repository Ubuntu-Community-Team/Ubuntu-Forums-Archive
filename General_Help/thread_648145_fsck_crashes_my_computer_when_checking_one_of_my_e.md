---
title: "fsck crashes my computer when checking one of my ext3 partitions"
date: 2007-12-23
forum: General Help
---

### Post by delfick on 2007-12-23
hello

I have my partions setup so I have an extra one formatted as ext3 for storing files and such.

Using this driver [http://www.fs-driver.org/](http://www.fs-driver.org/) I'm able to access it when I'm in windows

earlier today I was transferring some stuff to it and it comes up with this error (which I didn't really read that well, cause I keep having issues with another drive of mine, but that's a different story), anyway i think it was about a cyclic error or something.....

so when I pressed OK it stopped copying and made my computer very slow (the explorer shell crashed) and when i tried to restart the computer it just sat there and did nothing (and left it for an hour or two) so I hard reset it.

Then when I boot into linux I believe it tries to check it and freezes, cause all I see is the boot screen stop and then I can't go into any other console, or do anything. So I booted into my Livecd and ran "sudo fsck /dev/sda6 -C" and it gets to 2.4% before It completely freezes. Nothing works, not even the sys req thingo (which I've never got working anyways).....
(and yes, I'm sure it's /dev/sda6, after reading the sudo fdisk -l output, I can see that's the only partiton that size :D)

Anyone have any ideas how I could get around this crash ?? 

thnx :D

---

### Post by cmnorton on 2007-12-23
Two things: 

1) Is this drive mounted when you're issuing the fsck command? It shouldn't be.

2) I'd try to fsck this drive will booted from a live/rescue cd

---

### Post by delfick on 2007-12-23
> **cmnorton said:**
> Two things: 

1) Is this drive mounted when you're issuing the fsck command? It shouldn't be.

nope :D

> 2) I'd try to fsck this drive will booted from a live/rescue cd

??
"will booted" ?

:D

---

### Post by ~LoKe on 2007-12-23
Boot up a liveCD and fsck that way.   Fsck it all to hell!

---

### Post by delfick on 2007-12-23
that's what I did :D

my normal desktop wouldn't boot, as it would automatically check that partition (as it was in fstab) and so I booted into the livecd and fsck it there with "sudo fsck /dev/sda6 -C" and it crashes at 2.4%

So I booted the livecd and remove that entry from the /etc/fstab file on my root partition so I can boot into my normal system whilst I find a way to get around that crash....

......

---

### Post by cmnorton on 2007-12-24
> **delfick said:**
> nope :D



??
"will booted" ?

:D

Sorry. I meant to say use a live CD, and then fsck the drives in question. You should not crash in that instance.

---

### Post by pjkoczan on 2007-12-24
If the live CD fsck's don't work, then there's a decent chance that you have a bad disk.

---

### Post by delfick on 2007-12-24
crap.....

oh well, I think I have a copy of everything I had on that partition (only made it a few days ago)

so I should be able just reformat it....

I'll get to that eventually :D

Christmas first :D

thnx anyways people

---

