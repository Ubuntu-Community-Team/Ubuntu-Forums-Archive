---
title: "Software RAID1"
date: 2007-01-08
forum: General Help
---

### Post by jdavis on 2007-01-08
Hello,

I am currently on the verge of purchasing 2x400GB drives for my main ubuntu box which I would like to mirror with RAID1 (I currently have 2x200GB which are full, and in different boxes so are very rarely backed up). The drives are FAT32 and store data only, which is setup via Samba to be accessed by M$ boxes and my [GeeXboX]("http://www.geexbox.org") media center. The goal is to have a single box with a 400GB fileshare that will resist a drive dying, and without any huge slowdown.

I have an 80GB SATA drive which currently stores my OS, along with some non-important files and temp stuff. This will not be Raided. This drive will be formatted anyway during the new drive install, as i'm going to take the opportunity to create a seperate partition for my /home.

The 2x400GB drives will be SATA, the box is of quite a high spec (3GHZ CPU, 2GB RAM) and so shouldn't experience any speed issues with RAID.

What I would like to know is, during the install can I simply install to the 80GB drive as I would normally (that way I will avoid the GRUB problems that I have seen when the ubuntu boot partition is Raided) and then set the 2x400GB drives as raid using a HowTo such as [this]("http://users.piuha.net/martti/comp/ubuntu/raid.html").

I would also like to know what happens during a reinstall of Ubuntu on the 80GB drive, can the two Raided drives just be left as they are, or would they need to be setup for RAID again and reformatted?

Also, how easy it it to replace a drive if it fails, and is there an easy way to sync the drives again?

Any help or general advice would be appreciated as I haven't done anything with Raid before!

thanks, Jonathan

---

### Post by jdavis on 2007-01-08
I hate to do this but...

Bump... :rolleyes:

---

### Post by RandomJoe on 2007-01-08
I've not set up a RAID after the fact on Ubuntu, but yes you can set it up after you get installed to the 80GB.  No problems there.  I am also currently running on a 2x300GB RAID1 - that boots off the RAID1 as well - I had no problems at all, not sure what the Grub issues are.

I had a drive die on my RAID5 array once, just replace the dead drive with a new one of same or larger size, partition and re-add to the array.  (It's been so long ago I'd have to dig out a Howto myself to remember just what to do!)  It takes quite a while to rebuild the array, of course, during which time performance is degraded but other than that it was pretty simple.

When reinstalling, the RAID will work just fine so long as the new OS knows the filesystem.  I originally set up my RAID5 with ReiserFS on Slackware, installed Ubuntu to the OS drive and the RAID was just picked up no problem, then back to a newer version of Slack.

---

