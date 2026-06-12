---
title: "NTFS-3G &amp; CPU Utilization"
date: 2007-01-12
forum: General Help
---

### Post by jimbo99 on 2007-01-12
I've been monitoring this driver for some time and have noticed that when I copy files onto an ntfs partition, after a while (not right away), the cpu utilization will skyrocket to near 100% all the time.  The files to be copied are rather sizeable.

In order to test you might have to copy something that would take 10 minutes or more to complete.

I have this running on 6.10.  The main drive is a 320gig standard linux.  The drive I'm copying it to is another 320gig.  Both are mounted under linux.  Both drives are SATA.

I use one for WinXP, though I rarely boot to it.  And I use the other as my primary workstation.  I copy these files to the ntfs partition on the other drive so that when I boot into XP I will have access to those files.

I don't know that I am looking for an answer, rather maybe just looking to make you guys aware that this program is somewhat defective in that no driver should capitalize the cpu like that.

---

### Post by hikaricore on 2007-01-12
This is why ntfs write drivers are still considered unsuitable for most users.  Everytime I've written to ntfs I've had the same issue.  Remember this driver is a hack, reverse engineering on the file system that MS won't open source.  Proceed at your own risk and expect difficulties.

---

