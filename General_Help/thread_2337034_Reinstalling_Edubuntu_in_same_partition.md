---
title: "Reinstalling Edubuntu in same partition"
date: 2016-09-13
forum: General Help
---

### Post by archp2009 on 2016-09-13
Hello,

I collect OS's as a hobby.  I presently have 15 Linux distros and a half dozen Windows operating systems with the linux on one hard drive and the Windows on two other separate hard drives.  I use Daniel Richter's Grub Customizer on one of the Linux Distros to make my boot menu easier to read.  In trying to make extra space for an upgrade on my Edubuntu partition today,  I deleted some kernels that evidently were still needed.  Now the mouse won'work when I boot into Edubuntu. I plan to reinstall the latest Edubuntu release on top of the troublesome version that is on that partition now. It's been a couple of years, so I am a tad nervous.   I have a ver 14.045 Edubuntu DVD burned.  Could someone please walk me through the "something else" procedure to do this.  I understand that I could lose the Windows loader in my boot menu if the MBR is overwritten.If this is inevitalbe, it would be nice to know beforehand.  Thanks in advance for any suggestions to lessen the chances of disaster.

---

### Post by &amp;KyT$0P# on 2016-09-13
Can you boot some *buntu live media, chroot into the broken system (as root) and just apt-get install the removed kernel packages?

And, be sure to run [FONT=Courier New]apt-get update[/FONT] in the chroot before installing anything

---

