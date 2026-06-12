---
title: "Setting up btrfs"
date: 2021-08-16
forum: General Help
---

### Post by monkeybrain20122 on 2021-08-16
I wonder what is the correct way to install Ubuntu with btrfs. It seems very simple, just clicking a few boxes during install. But does it work? I read tutorials on Debian and Kali-Linux they are all kind of complicated involving interrupting the installer and dropping into busybox, mounting and unmounting some volumes, creating directories and  editing /etc/fstab anb so on. It seems too easy in Ubuntu. Are there any extra steps?

Thanks

---

### Post by ActionParsnip on 2021-08-16
Just use the manual partitioning and set btrfs as you need
[https://www.addictivetips.com/ubuntu-linux-tips/ubuntu-btrfs/](https://www.addictivetips.com/ubuntu-linux-tips/ubuntu-btrfs/)

---

### Post by monkeybrain20122 on 2021-08-16
> **ActionParsnip said:**
> Just use the manual partitioning and set btrfs as you need
[https://www.addictivetips.com/ubuntu-linux-tips/ubuntu-btrfs/](https://www.addictivetips.com/ubuntu-linux-tips/ubuntu-btrfs/)

Yes, I know that. My question is whether there are extra steps involved since it seems very simple comparing to tutorials from other distros. For example, you can choose your file system the same way in Debian but that is not enough, you still have to drop into busybox and do a lot of other things to get it to work, see video[ here]("https://www.youtube.com/watch?v=uxHbV6pOytk").


Having read a lot of these how to tutorials online it is my experience that a lot of very simple ones appear to be cut and paste where the writers haven't even tried them out themselves.

---

### Post by The Cog on 2021-08-16
Yes it's that simple. Except that when I did it, I didn't delete all the other partitions because there were things I wanted to keep. Just select the partition you want to install on, set the type as btrfs and mount point as /. It will automatically make separate subvolumes for / and /home, called @ and @home, so no need to set up a separate home partition.

---

### Post by monkeybrain20122 on 2021-08-17
> **The Cog said:**
> Yes it's that simple. Except that when I did it, I didn't delete all the other partitions because there were things I wanted to keep. Just select the partition you want to install on, set the type as btrfs and mount point as /. It will automatically make separate subvolumes for / and /home, called @ and @home, so no need to set up a separate home partition.

Hey indeed it is that simple in Ubuntu! Just tried to make and restore some snapshots and it work!. Wow! It is quite a lot of work to set it up in Debian (see the video I linked to) and I tried it it didn't even work (something has changed so Debian 11 doesn't look exactly like debian 10 as in the video and I improvised at some point and screwed it up. :))  Archwiki is even more complicated! I will learn the details when I have the time but right now I just want to see it works to see if it is worth spending time on it, and Ubuntu give me an easy way to test it out!

---

### Post by ActionParsnip on 2021-08-17
Why would it not be that simple?

---

### Post by guiverc on 2021-08-17
I really know little about BTRFS (*I've used opensuse for years as it's default, but I really only  learnt some things to avoid*) however can happily install Lubuntu using XFS & BTRFS using nothing more than selecting them as the *file-system* on the installer (`calamares` so a different install to most other Ubuntu and *flavors*).

I did a QA-test install with XFS today; but will likely do the BTRFS tomorrow (it's now the oldest on our [*focal.3* checklist]("https://phab.lubuntu.me/w/release-team/testing-checklist/"))

It depends to an extent on what features you want to use.  Yes I've had installs that have failed, or subsequent failures (eg. *install alongside* after a BTRFS install) where BTRFS or XFS are involved (*as complications do exist in a number of ways*), but simple BTRFS installs are actually easy.  Subsequent taking advantage of the *additional* features can be more involved...

FYI: Next day update:  BTRFS install easily done, manual partitioning, select the "/" partition that was XFS, switch to 'format' then select BTRFS, select "/home" but no format & install.. The issue with *subsequent* installs is `update-grub` doesn't easily follow the BTRFS path and the install doesn't appear in `grub` (which means the QA-test install needs to be failed; as it needs a manual fix). My next install (*after the current one*) will be a full-disk install over the BTRFS so I don't forget about the *unusual* formatting on that testbox.

---

