---
title: "gparted 0.3.3 help please"
date: 2007-05-04
forum: General Help
---

### Post by dryder on 2007-05-04
Hi,

I've installed gparted 0.3.3 (after reading the posts about the distro version being buggy).

It is in the menu Applications>System Tools

But when I try to run it it does not come up with an Admin login box - but says I need to log in as root to run it.

How exactly do I log in as root and then be able to use the menu system? I don't undestand why it simply doesn't pop-up the admin login box as the distro gparted does.

Would appreciate any help - thanks.

David

---

### Post by Sef on 2007-05-04
You can't partition a hard drive that is mounted.   Instead get [GParted]("http://gparted.sourceforge.net") from its site.

---

### Post by zmike1 on 2007-05-04
I'm using the live CD version of GPARTED but it doesn't seem to allow me the option to make an extended partition?  I have 62.4 G of unallocated that don't want to make  Primary...
... any advice?
Might this be  buggy too?

---

### Post by dryder on 2007-05-04
Hi,

> You can't partition a hard drive that is mounted. Instead get GParted from its site.

I think I may not have been explicit enough - apologies.

I did download gparted 0.3.3 from its site, ./configure, make and sudo checkinstall -D successfully.

The drive I am trying to partition is not mounted and is separate from the drive containg ubuntu.

David

---

### Post by zmike1 on 2007-05-04
sorry, I might add that I'm using v. 0.3.4-6 of gparted...

---

### Post by dryder on 2007-05-04
> I'm using v. 0.3.4-6 of gparted

As a point of interest, where did you get that from? Its not on their site, the latest is 0.3.3 I believe ...

---

### Post by zmike1 on 2007-05-04
My apologies if I'm wrong. I am a noob and a half.  
I think I downloaded it from sourceforge?  I did it yesterday at work.  Now that I check the "ABOUT" screen it says GParted 0.3.4

---

### Post by zmike1 on 2007-05-04
More apologies coming:  The .iso file says it's 0.3.4-6. the running version says 0.3.4

I am sorry that I'm going to have to stop this for right now.  Something urgent (wife related) has come up.

I'll be back.

---

### Post by dryder on 2007-05-04
There seems to be some confusion re my original post.

I an _not_ running Live CD - simply the updated version of gparted (0.3.3).

All I am asking is how to run it, just like running the distro gparted, as it does not give me a box asking me to confirm admin rights - it says I need to _log in_ as root.

I can't find a way to do that and run Applications>System Tools>GParted which is the home of the new version.

Thanks - David

---

### Post by mannheim on 2007-05-04
David -- You need to open a Terminal window, and type "gksudo gparted". You will be prompted for your password in a dialog box; then gparted will launch with admin privileges. (The menu entries in the default install take care of this.)

---

### Post by confused57 on 2007-05-04
> **zmike1 said:**
> I'm using the live CD version of GPARTED but it doesn't seem to allow me the option to make an extended partition?  I have 62.4 G of unallocated that don't want to make  Primary...
... any advice?
Might this be  buggy too?
If you already have an extended partition, probably with swap if you did a default install, just select the extended partition & resize...then you should be able to create logical partitions within the extended partition.

---

### Post by dryder on 2007-05-04
Thanks mannheim,

I'll give it a go ...
David

---

### Post by zmike1 on 2007-05-04
Thanks, Confused57.

I have not yet done the Ubuntu Install step.  (well actually, I did last week but I'm trying to fix the mistakes I made then so I've started over)

Anyway, 
On a new windows laptop, I *had* 3 primary partitions (FAT16, NTFS, FAT32) for Media direct, Windows XP, and a Recovery Partition (in order).  I used gparted to shrink the NTFS to 10G which left the 62 G mentioned earlier.  I've tried to make an extended part for the Ubuntu installation.

I don't want to use the default install because it overwrites the MBR and destroys the "Media Direct" functionality of the laptop.  Since I share the computer, I'm trying to keep this relatively benign feature.  I still don't seem to be given the option to choose either "extended" or "logical" from the screen in gparted.
Any ideas??

---

### Post by zmike1 on 2007-05-04
PS: Right now the space is "unallocated".   XP still works.  Trouble seems to be with gparted?  Also, parted wouldn't let me create an extended partition either.

---

### Post by confused57 on 2007-05-05
> **zmike1 said:**
> PS: Right now the space is "unallocated".   XP still works.  Trouble seems to be with gparted?  Also, parted wouldn't let me create an extended partition either.

Here's some screenshots that may help:
[http://gparted.sourceforge.net/larry/generalities/gparted.htm](http://gparted.sourceforge.net/larry/generalities/gparted.htm)

---

### Post by zmike1 on 2007-05-05
Thanks for the screenshots...  I looked at that and, in particular Figure 16, which shows where I'm stuck.  In gparted, when trying to set the partition as "extended" the only option that is selectable is "primary"  
Both "logical" and "extended" are dimmed and they won't select.

When I try using parted from the command line, I get essentially the same effect. (It) comes back with a message saying it is unable to complete the desired operation.  
... still searching

---

