---
title: "Trying to clone an Ubuntu + XP with clonezilla; target HD doesn't boot after"
date: 2013-05-05
forum: General Help
---

### Post by diablo75 on 2013-05-05
I've been trying to help a friend who has XP and Ubuntu installed on his source hard drive that is about 300GB in size and he would like to clone it to a new 1TB hard drive.  He doesn't save much anything important in his Ubuntu partition so I decided to use gparted to remove all the ext4 and swap partitions and the extended partition containing all of them so that they only thing remaining on the source hard drive is Windows and a old recovery partition used for factory reset on his PC.  Doing this broke grub, so I used an Ubuntu install CD and [boot repair]("https://help.ubuntu.com/community/Boot-Repair") to get Windows on the source hard drive to boot up, and this works pretty nicely because grub recognizing Windows is the only OS on the disc now and so boots strait into it with no menu appearing after POST.

Anyway the next thing I tried to do was used Clonezilla in beginner mode to simply copy the source drive to the destination drive.  One of the questions it asked was if I wanted to copy the boot data (I can't remember the exact wording) and I told it yet.  After that I just had to say yes, yes, yes, yes and away it went.  I didn't see any errors along the way.

After that I powered off the system, unplugged the SATA cables from both drives and connected the SATA cable the old drive was using to the new drive.  When I tried to let the system boot it just sits there after POST with no output (the very last thing you see is the "Boot from CD" status that comes up to indicate it's checking the CD drive, but there's nothing in the drive so the normal behavior is to go to the next boot device which is the hard drive, but nothing happens).  It just sits there.  I decided to boot Ubuntu from CD and see if running boot repair again would fix things.  It didn't do any good at all and the new drive just doesn't want to boot.

So I'm thinking now that something that needs to happen during the cloning process isn't happening, perhaps because I did this in beginner mode and didn't check off something that needed to be checked off, or perhaps because I should be trying some other cloning software out.

Any ideas or suggestions would be greatly appreciated.  Thanks!

---

