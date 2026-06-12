---
title: "Using pyschocats tutorial"
date: 2007-02-14
forum: General Help
---

### Post by Sbarton on 2007-02-14
Sorry about the title. I have used this method to create a separate home partition, and I have a few questions.Firstly many thanks for the tutorial.I had already booted into the pc and popped in the 'Live' CD then rebooted. After the live cd loaded I followed the tutorial to the point where I applied the changes, there were 2 actions.1 action succeeded and then I was asked to reboot as another was already mounted.(?) I did reboot and just followed through to the end. I have the extra partion (ext3) and it seems to have moved all files etc over to the new partition. However,when I rebooted I did not have my own login splash nor wallpaper I originally had nor web browser and had to reset these and their respective settings.Is this a normal affect of this type of operation? The other point is that in the tutorial I notice that the graphic showing the file type has above it a 'logical' selection,  I could only choose 'Primary'. Whether that was because the selected partition to resize was previously logical (in the tutorial) I do not know. It would be nice to know if I have missed some point or went wrong?
I have included a fstab and the partion resized was hda1 and created hda3.
Regards

---

### Post by firebush on 2007-12-07
Hi Sbarton,

I recognize that this is months after this post, but perhaps someone else will see this and find it helpful:

> However,when I rebooted I did not have my own login splash nor wallpaper I
> originally had nor web browser and had to reset these and their respective
> settings.Is this a normal affect of this type of operation?

No, this shouldn't have happened this way.  I encountered this problem as well.  As helpful as the psychocats site is (I wouldn't have attempted the separate home partition endeavor without it), it did seemly have one typo in the commands they gave:

find . -depth -print0 | sudo cpio --null --sparse -pvd /new/

That command needs a sudo in front of it, so that it reads:

sudo find . -depth -print0 | sudo cpio --null --sparse -pvd /new/

(I assume this is a typo...perhaps someone else can correct me if it isn't, but certain files just won't get copied without the sudo because of permissions issues.)

> The other point is that in the tutorial I notice that the graphic showing the file 
> type has above it a 'logical' selection, I could only choose 'Primary'.

I saw this too.  Primary is fine - after four partitions, you have to start using logical partitions.  I'm not clear on the distinction, but primary worked well for me.

---

