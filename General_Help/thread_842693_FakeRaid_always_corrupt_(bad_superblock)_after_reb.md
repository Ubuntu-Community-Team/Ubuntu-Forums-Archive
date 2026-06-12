---
title: "FakeRaid always corrupt (bad superblock) after reboot"
date: 2008-06-27
forum: General Help
---

### Post by timbellomo on 2008-06-27
I recently migrated from XP.  On XP, I had setup a Windows-managed software RAID0 (2x500GB).  I regularly backed up to a 1TB external hard drive.

When migrating to Ubuntu, I realized that I couldn't take my Windows RAID with me.  I hadn't used my mobo's "RAID" option - I made the software RAID in Windows alone.

So I set things up (what I thought was) the *right* way: Create RAID in BIOS, use dmraid to activate it in Ubuntu, format it, and copy all of the files onto it from my backup.

I've encountered a few problems:

1. I first formatted the partition with jfs.  I rsync'd the files (which took forever) over from the backup.  Everything looked fine.  Later that day after reboot, I couldn't mount the RAID.
```
mount: wrong fs type, bad option, bad superblock on /dev/mapper/via_dfchbchadh,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```
I tried fsck.jfs, but it said both superblocks were bad and "CANNOT CONTINUE."  After reading a few posts, I chalked it up as a loss and reformatted the RAID.

2.  I formatted the drives with xfs, figuring that maybe jfs was the issue.  This time, I copied the files with "sudo cp -Rv."  This went much faster (but still took a half a day or so.)  Upon reboot, I couldn't mount the RAID again -- same error.  I ran "xfs_repair" and it found the secondary superblock.  I was able to mount the RAID, and everything looked fine... until I rebooted.  Now I'm getting the "mount: wrong fs type..." error again.

2b. (of secondary importance) Although the cp was faster - it didn't preserve modified dates.  Can it?  Can I somehow set the proper modified dates with rsync or unison?

I'm not sure which direction to move in at this point.  

Should I abandon the mobo's fake raid and just build the software RAID completely in LVM (I think this is possible)?

Should I choose a different filesystem?  Could that be the problem?

As  always, any advice is appreciated.

Thanks,
Tim

---

### Post by fjgaude on 2008-06-28
I'm not sure I can help you with dmraid... don't use it anymore, use mdadm.

But I do know that rsync, grsync, and unison preserve the modification dates of files... these I use daily, for years.

What's wrong with using mdadm to create your two-disk array?

---

### Post by timbellomo on 2008-06-28
Thanks for the response.

In a previous install, I'd given mdadm a go, and had no issues with it.  I think the main driver in me using a fakeraid over a softraid was the possibility of Windows being able to use the RAID in a dual-boot scenario.  

I just found a post, though, that explains that a Windows softraid can be read in Linux (with proper config.)  Knowledge of that would have saved me all of this hassle.

In any event, I'll give mdadm a spin again - is there any advantage/disadvantage of mdadm/dmraid (or softraid/fakeraid).

Thanks,
Tim

---

### Post by fjgaude on 2008-06-28
Well, once you fully learn how mdadm works and its power you see that it is the Ubuntu and Linux way.

So many things can go work with dmraid and it doesn't work with raid5 arrays.

Anything that works is good if you know all the details of the program. Fakeraid and dmraid go together and their speed is likely just the same as mdadm, but without the features of mdadm.

Windows software raid made in XP, Vista is something I don't think many have used in Ubuntu. Many use BIOS/fakeraid and dmraid with a two-drive array. I'm into raid5 so I can't comment too much about other ways, except mdadm.

---

