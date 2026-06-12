---
title: "Trouble Growing RAID0 Array"
date: 2013-02-15
forum: General Help
---

### Post by coerulea on 2013-02-15
When trying to grow a RAID0 array, the array converts to RAID4 and then is supposed to switch back to RAID0, but it never does this last step.  This array is an extra "storage" array and no system files are stored on it.  I'm also doing this on a virtualized server (not sure if that matters, but adding that note for completeness), and it's 12.04LTS.  Here are the steps that I've taken:

- created the array with two 100GB drives
mdadm --create /dev/md0 --level=0 --raid-devices=2 /dev/xvdb1 /dev/xvdd1

- add a third drive to the array  (tried a lot of steps for this but i think this is the right cmd)
mdadm --grow /dev/md0 --raid-devices=3 --add /dev/xvde1

From here the array gets reshaped to RAID4.  This step took a long time to do and I'm assuming it's because it was creating the parity drive.  Once it finished, the output of 'mdadm -D /dev/md0' shows that it is still RAID4 and the array's size is not any larger.  Again, I think this is because it just added the new drive in as a parity drive.  The state is marked as 'clean' and I don't notice anything odd or non-functioning.

So I then try to manually convert it back to RAID0 with:
mdadm --grow /dev/md0 --level=0

This command also took a very long time to run/reshape but never converts it to RAID0.  Found a post where it said I needed to specify a backup file, like:
mdadm /dev/md0 --grow --level=0 --backup-file=/root/backupfile

but this also takes a long time and never converts.  I've even tried adding a 4th drive, thinking maybe it would trigger something that would actually make it convert back, but that didn't work either.

I've found multiple posts where it says it is not possible to grow a RAID0 array, but I found this snippet from the 'mdadm' man page:

"From  2.6.35,  the  Linux Kernel is able to convert a RAID0 in to a RAID4 or RAID5.  mdadm uses this functionality and the ability to add devices to a RAID4 to allow devices to be added to a RAID0.
When requested to do this, mdadm will convert the RAID0 to a RAID4, add the necessary disks and make the reshape happen, and then convert the RAID4 back to RAID0."

Could someone help me figure out how to get this array to convert back to RAID0?

Thanks!

---

### Post by Nullexe on 2013-04-09
I had a similar issue and was able to resolve it by un-mounting the volume checking the partition and then resizing

e2fsck -f /dev/mdX

and then

resize2f /dev/mdX

---

