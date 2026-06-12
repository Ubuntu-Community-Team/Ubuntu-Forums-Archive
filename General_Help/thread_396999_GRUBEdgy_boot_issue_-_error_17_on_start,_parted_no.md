---
title: "GRUB/Edgy boot issue - error 17 on start, parted not rec. partition"
date: 2007-03-30
forum: General Help
---

### Post by Scol-R-LEA on 2007-03-30
On one of my desktop systems, I have a dual boot configuration splitting a single Maxtor 300GiB drive between Ubuntu Linux (Edgy Eft with the latest updates as of March 26th) and Windows Vista RC1 (set up for preview testing, rarely used and now expired AFAIK). The Vista partition (NTFS) is in hda1 (C: drive in Windows nomenclature, 200GiB), the Linux root partition (ext3) in hda2 (95GiB), and the Linux swap in hda5 (5GiB). The system is running on an ASuS A7s333  motherboard, AMD Athalon 2200+ 1.5Ghz CPU, BIOS rev. 1006, with 1.5GiB RAM.

I had been running this set up since October with few hitches. However, I recently was converting a large number of MP3 files to OGG (for space savings primarily) using dirogg, which unfortunately crashed a number of times, locking the system (no mouse or keyboard response, could not restart Gnome) and requiring a hard reset. Had I been more attentive, I suppose this should have been a warning to stop right there, but I rather foolishly persisted; I found that if I stopped the program after about 20 minutes, removed the MP3s already converted (it was supposed to do this automatically, but didn't) and restarted it, it would run more or less stable. However, I got careless and let it run for a longer time, leading to another hard crash.

After this latest crash, the system failed to boot; I would get an 'error 17' from GRUB, and could not proceed past that. After some online investigation, I tried booting from the liveCD. Once running, I found that I could not mount hda2, and PartEd did not recognize the partition type for it; fdisk recognized it as a 'Linux' drive (not specifying the FS type). Trying to use 'find' in the GRUB shell accomplished nothing (not surprising, since it wasn't mounted). 

I suspect that the partition itself may be corrupted, not just the MBR, but I am hoping otherwise; while everything critical which was on this machine was duplicated on my main PC, and I was looking to re-install soon anyway to eliminate the Vista partition (and do a bit of experimenting with various things), there were some things I would have liked to have backed up before reinstalling. Furthermore, I would like to know of any solutions in case it should come up in the future. Any useful advice would be quite appreciated.

As an unrelated aside, I seem to have made a typo in creating my user account here tonight; I dropped the 'h' in 'Schol-R-LEA', giving the wrong user name. It's not a big deal, but if there is any way of getting the user name I'd wanted without creating a new account, I'd like to know.

---

### Post by 1/0 on 2007-03-30
Have you checked your root(x,y) settings in /boot/grub/menu.lst ? You could check the x and y by:
```
sudo fdisk -l
```

But this sounds like the MBR has taken a hit. In worst case you'll have to erase the MBR and reinstall GRUB.

---

### Post by Scol-R-LEA on 2007-03-30
Unfortunately, as I said earlier, I am unable to mount the drive to access /boot/grub/menu.lst, as I said earlier. Here is what fdisk was giving:

```
$ sudo fdisk -l

Disk /dev/hda: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1       25497   204803072    7  HPFS/NTFS
/dev/hda2   *       25498       36034    84638452+  83  Linux
/dev/hda3           36035       36483     3606592+   5  Extended
/dev/hda5           36035       36483     3606561   82  Linux swap / Solaris

```

Since then, I've tried running fdisk again, and this time, it accessed the partition, and found a slew of problems which it could not assure were reparable. I'm going to restart the system shortly and see if anything was actually fixed.

---

### Post by Scol-R-LEA on 2007-04-01
Update: I ran fsck, as I stated, and it immediately proceeded to remove the journaling and other features of ext3, effective converting the filesystem to  ext2. It supposedly also repaired several things, but subsequent fsck scans still found problems repeatedly. 

Now on booting I am getting an error 15 message instead of error 17, and GPartEd sees the partition as an ext2 boot partition. I can mount this partition to /mnt/root, and viewing the mounted FS shows only a single 'lost+found' directory. Listing the directory gives a long series of numbered files (I could view it with ls, but couldn't cd into it).

At this point, it is probably safe to say that the old FS is pooched; I'll probably simply repartition the whole drive tomorrow unless anyone can make any suggestions otherwise. As I said before, this should not present any catastrophic problems, but there were a few things I would have liked to back up first. So it goes.

---

### Post by 1/0 on 2007-04-01
NOOO! Did you forget to say its an ext3 fs? (fsck -t ext3)

As far as I know, you're right its formated and effectively toasted...

---

### Post by Scol-R-LEA on 2007-04-01
> **1/0 said:**
> NOOO! Did you forget to say its an ext3 fs? (fsck -t ext3)

As far as I know, you're right its formated and effectively toasted...

**headdesk** Yes, I think that is what I must have done... damn. Well, at this point I don't see much else that can be don,e but thank you for this clarification.

---

### Post by 1/0 on 2007-04-01
That makes me feel so bad. I know the feeling. Been there, done that. Now days I have an external ethernet drive that is a back up plus another server that's an extra backup. I also burn all photos I take on dvds.

---

