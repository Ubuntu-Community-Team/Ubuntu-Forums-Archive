---
title: "How to correctly use TimeShift + copy snapshots to external drive"
date: 2018-11-28
forum: General Help
---

### Post by aramchekian on 2018-11-28
I'm trying to backup my progress so that I don't have to start over with a clean installation every time I mess something up. I am not sure if I'm doing this correctly. These are the steps I've taken so far...

sudo add-apt-repository ppa:teejee2008/ppa

sudo apt update

sudo apt install timeshift

*Change all folders from excluded to included.

*Create a snapshot and save it on the main disk drive.

Then...

*Format an external drive as ext4.

sudo cp -a /timeshift/snapshots/2018-11-28_19-47-10/ /media/teresja/TimeShift

*Change backup location to external drive.

It seems like I can restore from a snapshot saved to my main disk drive successfully, but I am not 100% certain. Furthermore, when I try to use the snapshot I copied to the external drive in TimeShift, no snapshot appears in the list to restore from. I'm guessing this is because I need to copy it back over to the main disk drive and restore it from there before it can be used? I made sure to switch the backup location from the main disk drive to the external drive, which I formatted to match (ext4).

---

### Post by Richard-S on 2018-11-28
I use Timeshift to back up to an external drive. If I start Timeshift when the external drive is not mounted, it shows no backup exists. Perhaps having backups in two different locations is confusing to Timeshift.

Why would you want to back up to your main disk drive if you are backing up to an external drive?

Richard

---

### Post by aramchekian on 2018-11-28
I want to have a backup on the main disk drive that I will update periodically, but I also want to have a copy of the original backup in a safe place, such as a flash drive, so that I can restore from there in case something happens to the original.

---

### Post by aramchekian on 2018-11-29
So, I tried...

```
sudo cp -a /media/teresja/TimeShift/2018-11-28_19-47-10/ /timeshift/snapshots
```

...and now I am able to use this copy of the snapshot to restore from.

My question now is, if I were to completely remove and reinstall ubuntu (for whatever reason), would I still be able to use this snapshot to recover from? Or does it rely on files in the system which would have been deleted upon re-installation?

Also (and perhaps a better question), is there a better method for doing what I am trying to do?

---

