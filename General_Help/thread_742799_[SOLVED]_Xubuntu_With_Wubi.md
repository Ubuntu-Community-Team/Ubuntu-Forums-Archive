---
title: "[SOLVED] Xubuntu With Wubi"
date: 2008-04-02
forum: General Help
---

### Post by theravenproject on 2008-04-02
Okay I read the previous/other threads related to this topic and still feel that my situation warrants a new thread because I have a little variation here...I am running:

Dell Optiplex
Pentium IV
256 mb Ram
On board Video Card (Rage Ultra...128 mb)
20 gb Maxtor HD

Right now I have a 17 gb WIN XP partition on E:\ and a 2gb WIN 98 SE on C:\...The XP was an Upgrade disc so I had to leave the friggin win 98 on there although I can delete it now.

Now, I have the Kubuntu Live CD and The Ubuntu Live CD-Both are version 7.10...I ran a previous version of Ubuntu on this nag before and it ran slow-I was informed recently whilst inquiring about giving it another shot that 256 mb of ram isn't really enough for Ubuntu (They say 384 in the Documentation) but that I would be able to run Xubuntu just fine and that I should use the "Alternate Installer"!  Well, I have no way to burn the ISO right now and am really itching to get this show on the road!  What I want to do is to use my Ubuntu live Cd to resize my partitions as follows:
E:\ WIN XP: 10gb
Delete Win 98 SE
Swap Partition for Linux-FAT32 (**What size should I go with**)
Xubuntu get's the remainder of the HD som 9.5 gb **I would really like somebody who knows there stuff to help me map out my partition scheme so that I get this right!!!**

Lastly,  I want to install Xubuntu in Windows as a file like I have heard you can do with this Wubi program...and then transfer it over to the EXT3 Linux partition-going back after all of that and deleting it from the Win XP partition and Deleting Wubi and finally getting on with my merry self...Please-Any and all input is appreciated-I want to make sure that I am not about to screw up and also that Xubuntu us the right Distro for this machine...I could care less what the desktop environment looks like-all I care is that I will still have all the benefits of my old Ubuntu back...

---

### Post by theravenproject on 2008-04-02
I'm not bumping but I just stumbled across [FONT="Comic Sans MS"]**UNETBOOTIN**[/FONT]  and Wonder if this program is applicable to my prob?  Sorry I am such a helpless dummy-I jsut want to make sure I do this right!!!!!!!

---

### Post by theravenproject on 2008-04-02
Can anyone HELP::::::::::????????

---

### Post by ago on 2008-04-03
Yes you can use Unetbootin since that uses the alternate installer. If you already have a CD there is no much point in using Unetbootin. 300-500MB of swap will do. Allocate 8-10GB as /, do not create other separate mountpoints.

---

