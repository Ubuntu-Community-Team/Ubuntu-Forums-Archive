---
title: "Ubuntu 14.04.1 - Unable to safely remove external hdd"
date: 2014-09-04
forum: General Help
---

### Post by sffvba[e0rt on 2014-09-04
o/  all...

My current install of Ubuntu 14.04.1 64-bit has developed an interesting idiosyncrasy... When I try and "safely remove" my Western Digital external HDD it simply remounts itself as if I plugged it in again before I get a chance to remove it.  Even using the disk tool if I specify to power it down it does and after 2 seconds it powers back-up and mounts.  Normal thumb drives eject successfully.

Any thoughts on way this might be happening and how to remedy it?

---

### Post by Cliff_Simonds on 2014-09-07
Is your ext. Hdd partitioned? in Disks goto the drive pictogram at the bottom and click the double gear icon > Edit Mount Options > turn off Automatic Mount Options for each partition. I had this problem before too, and for a while, was just unmounting the partitions in Files, then pushing the drives off switch(not recommended if you just made a backup or copied files because of Write Caching).

---

### Post by mcduck on 2014-09-07
I'd say the blame is on the firmware of the drive itself.

I regularly use 4 different external drives connected through USB2, USB3 & eSATA), and all of them are just basic external drives without any fancy features. Obviously, they all work as you'd expect. Then I recently bought a new Transcend one, which has a button for quick backups (in Windows of course) and for quickly reconnecting the drive after it's been removed (in Windows, of course) plus some other fancy features that don't really work unless you happen to use Windows. This one does exactly the same you are seeing, ejecting the drive powers it off, but it will just automatically power up again after a few seconds and is then mounted again.

I haven't found any nice solution to it, apart from being quick and unplugging it in the two seconds after ejecting, before it decides to wake up again...

---

### Post by buzzingrobot on 2014-09-07
> **mcduck said:**
> ...ejecting the drive powers it off, but it will just automatically power up again after a few seconds and is then mounted again.



Very much suspect that is what's going on.  With external devices set to be mounted automatically on insertion, the drive appears to be, in effect, announcing its presence as soon as it's unmounted.  Perhaps this is useful in Windows.

The drive, if course, can be safely removed when the machine is powered down.

---

### Post by mcduck on 2014-09-07
Yeah, I pretty much interpret it as the drive being overly enthusiastic. :D

(And anyway there *is* a two-second gap where the drive is unmounted, and powered down, at which point it can be safely removed.)

---

### Post by sffvba[e0rt on 2014-09-07
Hmmm... thanks for the replies all... I typically just wait a few minutes after using it and then just remove it, I try and make sure no files are in use etc.  But it does seem I will have to try and use another for backup purposes and give this one to the wife (and Windows :p)

---

### Post by ErikMAkkerman on 2014-12-06
I've got the same problem, but I donot think it is de hdd drive.

I have two computers: a large DELL desktop and a small MSI netbook,
both running Ubuntu 14.04 LTS
I have two external hdds: an older 500 GB LaCie, and a brand new 1 TB Seagate.
Both the LaCie and Seagate function properly on the DELL.
On "Safely Remove Drive" they unmount and switch off.
On the MSI, however, they unmount, do NOT switch off, and mount again after
a short while.

Seems to me there is something with the hardware on the MSI that Ubuntu
does not manage properly.

---

### Post by HermanAB on 2014-12-06
You could unmount manually with: 'sync', then 'umount -l /dev/sdb', then unplug.

---

### Post by buzzingrobot on 2014-12-06
I've noticed on occasion that if a removable drive is highlighted in a file manager, whatever GUI is in use will complain if I try to eject/unmount it, no doubt assuming it's still in use. Clicking some other folder removes the highlight and allows the drive to be removed correctly.

---

### Post by ErikMAkkerman on 2014-12-27
Thank you, Herman. That seems to work!
Erik

---

