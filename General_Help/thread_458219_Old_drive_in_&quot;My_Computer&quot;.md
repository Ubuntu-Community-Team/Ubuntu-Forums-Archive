---
title: "Old drive in &quot;My Computer&quot;"
date: 2007-05-29
forum: General Help
---

### Post by Legace on 2007-05-29
I recently used a very old USB flash-disk on Ubuntu 7.04. After using it, a _CD 1_ link appeared in the computer:/// -folder. After removing the disk and after rebooting, the "CD 1" is still there..

[_*Look at this picture >>_*]("http://img255.imageshack.us/img255/5613/compla9.png")

If I click on the CD 1, then it says: *mount: special device /dev/scd0 does not exist*
**In windows xp, the disk doesn't go into the "Removable media" group, but in the "Harddisks" group. This is probably the problem here too :)**

Can I get that CD 1 away? It is really annoying..

---

### Post by dexter on 2007-05-29
sudo umount /dev/scd0 ?

---

### Post by Legace on 2007-05-30
> **dexter said:**
> sudo umount /dev/scd0 ?

When I put the code:
> biru@biru-ubuntu:~$ sudo umount /dev/scd0
Password:
umount: /dev/scd0: ei löydy
biru@biru-ubuntu:~$

But the CD 1 is still in the My computer place..

---

### Post by kentbrew on 2007-05-31
I've got something like that going on myself.  I've just installed Ubuntu (Feisty 7.04)  on two older laptops; they both read my external HD (USB, brand new, 500 gigs) just fine. 

But when I tried a USB stick, the external HD's icon and filesystem went away from Places:Computer, and left me with a ghost icon for the USB stick that says it's unable to mount media (there's probably no media in the drive) when I double-click it, and won't let me move it to the trash (Cannot move file to trash, do you want to delete immediately?). The USB stick (a 2-gig Patriot Memory model, labeled "USB Disk Pro") never mounted. If I try to delete the ghost icon, I get this: Error "Operation not permitted" while deleting "computer://USB%20Disk%20Pro.drive". 

More: when I try attaching the external HD, it is no longer recognized. Same thing happened on both newly-installed laptops ... both the USB stick and external HD work fine on my Windows machinery.

I'm missing a key piece of information: where does the contents of "Computer - File Browser" come from, please? I was able to create a dummy icon in here by mucking about with fstab, but it didn't want to hook up to either the USB stick or the external HD, and I got too nervous to mess with it without knowing what I was doing.

[More info:  okay,hang on, I found the USB Disk Pro in the Device Manager, under UHCI Host Controller. It's acting like the stick is still there, only it's not ... is there an easy way to remove it through Device Manager that I'm missing?]

Thanks very much for your help,

--Kent

---

### Post by cascader on 2007-05-31
It appears that I may have the same problem. After trying out my new **[COLOR=Red]LG 2GB USB Stick[/COLOR]** I am left with a **ghost icon** on my screen. Check image::


[[IMG]http://lh6.google.com/image/pruger/Rl5aeWmGbtI/AAAAAAAABJ4/m1hTKssZB-Y/s144/WeirdMount.jpg[/IMG]]("http://ubuntuforums.org/%3Ca%20href=")

This icon does in fact link to my **[COLOR=Blue]WinXP[/COLOR]** installation, hda1, and its apparent corruption seems to have happened at the same time as I tested my new USB Drive. Whether the two events are related is anybodies guess. Hopefully this post will lead to a solution. Maybe I will find it.

This drive/partition also appears that in the **[COLOR=DarkGreen]/dev/disk/by-label[/COLOR]** directory as ;
**[COLOR=DarkGreen]___________[/COLOR]**  , that's right, as a string of underscores.

**[COLOR=Green]What is going on ?[/COLOR]**

---

### Post by kentbrew on 2007-06-02
My ghosts all went away when I did a restart. I still can't get the USB stick to work, even after reformatting it with NTFS, but the HD is now fine on the Evo and quasi-fine--when I unmount it, I get an error that says I don't have permission to remove the directory from /media--on the M700.  I'm going to try a different memory stick next. (Unless somebody can point me at instructions for reformatting the 2-gig stick and removing that silly 25-meg partition with the proprietary Windows crap on it.)

Seriously, though: this is about the only major hitch--besides dealing with some very old Windows wireless card drivers--that I've run into. I'm about ready to start shopping for a brand-new laptop for Ubuntu.

---

