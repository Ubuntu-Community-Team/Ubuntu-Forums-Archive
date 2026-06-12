---
title: "Possible samba related problem - Help needed!"
date: 2016-11-30
forum: General Help
---

### Post by ian49 on 2016-11-30
I'm running Ubuntu 14.04 and have a small SSD for the op sys and a 2GB drive which I had split into 2 shares of roughly equal size. Everything has worked fine since day 1 but today I had an error which suggested I needed to update Samba. I did this via synaptic package manager and then rebooted. Now I'm unable to access either of the shares on the 2GB which is nothing short of a disaster. If I try to view them they both report 0 items. If I run the Disks utility on the 2GB disk it says "Disk is OK, one bad sector". It shows the 2 partitions for the shared drives and reports that they are 64% full and 9.4% full which is what I'd expect based on what was stored on them. My question is has I lost all my data or is it something else, perhaps to do with permissions. I'm really desperate so any help would be appreciated.

---

### Post by ian49 on 2016-11-30
I'm now wondering if the samba upgrade might be a red herring. I unmounted the 2 shares and ran ntfsfix which gave the following:

sudo ntfsfix /dev/sdb1
Mounting volume... Error reading bootsector: Input/output error
Failed to sync device /dev/sdb1: Input/output error
FAILED
Attempting to correct errors... Error reading bootsector: Input/output error
Failed to sync device /dev/sdb1: Input/output error
FAILED
Failed to startup volume: Input/output error
Error reading bootsector: Input/output error
Volume is corrupt. You should run chkdsk.

I'm assuming this point everything has been lost unless anyone knows of a way I can recover the actual data. I'm guessing the file table is corrupted?

---

