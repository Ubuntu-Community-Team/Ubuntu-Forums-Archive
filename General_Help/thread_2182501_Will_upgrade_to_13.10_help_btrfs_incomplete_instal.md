---
title: "Will upgrade to 13.10 help btrfs incomplete install?"
date: 2013-10-21
forum: General Help
---

### Post by Mark_in_Hollywood on 2013-10-21
I'm using v. 12.04 (Precise Pangolin). In June 2013, I re-formatted the drive: btrfs. This filesystem, has placed my /home (on /dev/sda6) in my / - this is due to restoring a backup of /home, I believe, but am not 100% sure of.

Now I have btrfs routinely filling / with snapshots, I cannot find a way to control it to make it not take snapshots. The btrfs may be very good with somethings, but it was a mistake to use it. No data has been lost, but it's taking too much time from doing more useful work. For those who understand btrfs, what is on the drive is both @ and @home with "home" being in @. Fixing this, while possible is nightmarish. I cannot get a concise response as to how to fix it. Some responses have even been erroneous. Not maliciously, but due to incomplete communication.

Will the most recent 13.10 understand this? Repair it?

---

### Post by grahammechanical on 2013-10-21
A couple of us experimented with btrfs while Saucy Salamander was under development. I have read that as btrfs is being improved all the time then we should use the latest Linux kernel.

I do not understand why you have a problem. With btrfs we have to run a few commands to take a snapshot. It is not done automatically. We can install something called apt-btrfs-snapshot and that will automatically take a snapshot of @ (or / ) every time that we install software or run an update. In this case we do get a collection of apt-snapshots. Especially if we run daily updates which we do when running the development branch. You should be able to uninstall apt-btrfs-snapshot.

Every install of Ubuntu has a /home folder in / even those who had /home on a separate /home partition. You may find that on btrfs that @home in @ is just an empty folder. There should be another @home that is your @home partition. It will have a folder with your user name and inside that all the usual stuff.

The main issue I had, which in my opinion prevents it from becoming the default file system for Ubuntu, is the absence of a GUI snapshot management utility. I did notice that if we go into Recovery mode and put the file system into read/write mode such as by running Network we get an "apt-snapshot - revert to old snapshot and reboot" option in the recovery menu. I cannot remember if we get options to delete snapshots there.

I think it must be possible to use apt-snapshot revert to also delete because I was able to modify the apt-snapshot script to create my own snapshot management utility. And I did not really know what I was doing. I used existing code from the script and created additional scripts to create and delete snapshots.

Regards.

---

### Post by philinux on 2013-10-21
I see that snapper is in development. [http://lizards.opensuse.org/2011/04/01/introducing-snapper/](http://lizards.opensuse.org/2011/04/01/introducing-snapper/)

And a search for btrfs gui has a few hits.

---

### Post by The Cog on 2013-10-21
As far as I can see, an install on btrfs creates a @ subvolume and a @home subvolumes. They are not just folders, they are subvolumes, which are an entity known to the filesystem. The intention is that you should mount the @ subvolume as your root, and the @home as your /home. If you can see these subvolumes then you are mounting it wrong. Rather than mount the main partition, mount the two subvolumes, with entries like this in fstab:
```
UUID=blah /     btrfs subvol=@     0 1
UUID=blah /home btrfs subvol=@home 0 2
```

Other snapshots create more subvolumes in the partition root, so they should not be visible in your mounted subvolumes.
I created a mount point /mnt/btrfs where I could mount the main volume and manipulate the subvolumes (e.g. creating renaming, deleting snapshots).

Update-grub doesn't find linux installation tucked inside subvolumes though, so multi-boot gets difficult.

---

### Post by Mark_in_Hollywood on 2013-10-24
Please direct your attention to post #16 (HaraldWeber)

[http://ubuntuforums.org/showthread.php?t=2179497&page=2](http://ubuntuforums.org/showthread.php?t=2179497&page=2)

I had my OS blow up in May. In June I used Deja-Dup to backup /home. Then I reformatted the drive as: btrfs. All went well until 2 things. One, I used Deja-Dup to restore the /home. and Two: I tried to re-install [profile-sync-daemon]("http://ubuntuforums.org/showthread.php?t=2175269"). On each cold boot, btrfs would create a snapshot. After a while my nearly 20 gig / filled up. Each cold boot I received a "disk full message" about having less than 1 gig of free space.

The solution is pretty scary looking to me. Despite my (bad) choice of btrfs, I'm not a sophisticated computer geek. If I have to use a LiveUSB session to fix the problem, per the HaraldWeber, above, I want to know that his directions are spot-on. I chose btrfs to work with MythBuntu. I could never get it setup correctly. 

Just a final FYI, on cold boot each morning, after GRUB but before the password entry screen, Ubuntu says that / and /home aren't mounted and do I want to Skip, Ignore or Mount Manually. I select Ignore and the OS loads fine.

I'm not looking to get the profile-sync-daemon working again until the btrfs problem of it having the @home in @. Originally the / and /home are separate partitions /dev/sda1 and /dev/sda6. Now, it appears that btrfs thinks that @home in a part of @.

---

