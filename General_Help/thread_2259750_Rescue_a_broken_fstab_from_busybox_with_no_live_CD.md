---
title: "Rescue a broken fstab from busybox with no live CD?"
date: 2015-01-06
forum: General Help
---

### Post by mrule on 2015-01-06
Hi all, 

I had a drive mounted from fstab that failed. It's not an important drive, but the system drops into busybox anyway when it notices that it's missing. I can mount the root drive, but ubuntu's busybox version doesn't seem to contain a text editor, so I can't comment out the dead drive from fstab. I don't have a live CD and I don't have means to create one.

I feel like this should be quite solvable. All the system needs to do is skip mounting the missing drive and everything will be fine. I just can't for the life of me find information about how to accomplish this from busybox.

---

### Post by mrule on 2015-01-10
Ok, so here is the update. It may well be that the version of busybox built for ubuntu simply isn't set up for making repairs -- because most people are expected to use the liveCD? Anyway I went out and got a USB stick and used that to fix things up. 
In the future, as I understand it, I should specify "nobootwait" option in fstab for non-essential drives.

---

