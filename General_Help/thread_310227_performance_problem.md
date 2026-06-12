---
title: "performance problem"
date: 2006-11-30
forum: General Help
---

### Post by tlinuxnub on 2006-11-30
I just downloaded the latest version of kubuntu. I allowed it to update, install all the new drivers and such.  But I am having a pretty bad performance issue.  Everything seems laggy, doesnt open right away, and holding my cursor over the konqueror icon takes the pc a while to load up that small bubble to tell me its konqueror.  I think this is caused by my video drivers either being outdated or incorrect, and or its not operating my cpu correctly.

I have a sony vaio vgn-s460.  With an Nvidia Geforce 6 series, pci-x, with 128 mb dedicated memory to the video.  the cpu is the intel centrino, the pc has 512 mb ram.  Ive had linux on this laptop before and it was much smoother.  Anyone have any tips or some instructions how to fix this?  please keep in mind im very new to linux.  so some step by step may help:-D 
I did try downloading the newest nvidia driver from their site, but im not sure if I got the right ones.  please help!
Thanks everyone

---

### Post by hardyn on 2006-11-30
what is your idle CPU usage?

it that a P-M or duo-core machine?

---

### Post by tlinuxnub on 2006-12-01
how do i find that out? and no its not duo core.
and now my display colors are all messed up

---

### Post by hardyn on 2006-12-01
under the tool bar on the top, either prefereces, or system, there is something called "system monitor" (i think, im not on my linux box this morning).

start it, and it will bring up a window and display time line diagrams with memory and CPU useage.

you idle cpu useage should be somewhere between 2-5%... if its more like 20-30 please reply to this post, i think there is a problem with ubuntu and sonly/asus notebook, and i would like some ammo to get this fixed.

thanks.

---

### Post by tlinuxnub on 2006-12-01
yeah its idling more at 40% i have no idea why.  the only thing i have running is my browser and the system monitor.  any ideas?

---

### Post by bobosity on 2006-12-01
open a terminal and run 'dmesg' 

anything look strange?

---

### Post by bobosity on 2006-12-01
oh yeah...

open another terminal and run 'top'

that will tell you what's eating resources.

---

### Post by hardyn on 2006-12-01
its a bug in the ubuntu kernel...

it makes pentium M based Asus and Sony notebooks do this, they have repaired the kernel for most other makes of single and dual core notebooks, but the problem exists with these two.  (asus is a big OEM, the sonys may be built by asus)

you can search around there are 2 solutions....
roll back to the i386 kernel... or edit one of the start up files.  search for "maxcstate".

Please Please Please report it as a bug here:
[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/73275](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/73275)
so we can get this fixed.

---

### Post by tlinuxnub on 2006-12-01
For the resources part of your response.  Xorg keeps rising to the top, but its not from cpu usage. the cpu usage is always at 0.3% the memory will move around a little more, ranging from about 3.0 to 8.1.  but at random times, as im typing this, i just saw the xorg go to 4% cpu usage, so this is just more confusing to me.

I also ran the 'dmesg' command and found a few errors.  

[17192392.592000] hda: tray open
[17192392.592000] end_request: I/O error, dev hda, sector 64
[17192392.592000] Buffer I/O error on device hda, logical block 8

Now this error continues a few times, the secotr being 68, and logical block being 16 and 17.  
[17240507.632000] ISO 9660 Extensions: Microsoft Joliet Level 3
This is what comes up before the errors pop up, and afterwards.  any ideas?
Thanks

---

### Post by hardyn on 2006-12-01
sounds like the hard disk may be going bad.

there are several hard disk scanning utils, just about every hard disk manuf. has one; and most are not specific to the brand of hard disk.

---

### Post by tlinuxnub on 2006-12-01
I highly doubt the hard disk is going bad.  I did recently have the machine up and running on windows. with absolutely no problems what so ever.  But I did reply on the post you linked as you asked.  But am now going to try with the maxcstate and see how that helps.  How exactly do I go about finding the maxcstate in the start up files?

---

