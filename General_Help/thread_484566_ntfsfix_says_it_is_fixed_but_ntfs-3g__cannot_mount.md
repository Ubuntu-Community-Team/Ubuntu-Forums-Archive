---
title: "ntfsfix says it is fixed but ntfs-3g  cannot mount!"
date: 2007-06-25
forum: General Help
---

### Post by Buendia on 2007-06-25
Hi,

I have a sata hard drive with some partitions in (bloody) ntfs and a lot of data on them and I need to read/write to this drive. So I used ntfs-3g to mount, here is the result:

[FONT="Courier New"]Volume is scheduled for check. Please boot into Windows TWICE, or
use the 'force' mount option. For example type on the command line:

    mount -t ntfs-3g /dev/disk/by-uuid/01C4DB73D2161100 /media/sdb7 -o force

Or add the option to the relevant row in the /etc/fstab file:

    /dev/disk/by-uuid/01C4DB73D2161100 /media/sdb7 ntfs-3g defaults,force 0 0

Volume is scheduled for check. Please boot into Windows TWICE, or
use the 'force' mount option. For example type on the command line:

    mount -t ntfs-3g /dev/disk/by-uuid/01C4DB73D311D620 /media/sdb8 -o force

Or add the option to the relevant row in the /etc/fstab file:

    /dev/disk/by-uuid/01C4DB73D311D620 /media/sdb8 ntfs-3g defaults,force 0 0[/FONT]

(1) I only have vista in the windows side and (bloody god-damn) vista does not support the promise sata drivers ( actually, the bloody god-damn promise company has not created the drivers for vista). So this option of going to windows and shutting down is impossible for me.

(2) I have tried ntfsfix, and it says:

[FONT="Courier New"]
Mounting volume... FAILED
Attempting to correct errors... 
Processing $MFT and $MFTMirr...
Reading $MFT... OK
Reading $MFTMirr... OK
Comparing $MFTMirr to $MFT... OK
Processing of $MFT and $MFTMirr completed successfully.
Setting required flags on partition... OK
Going to empty the journal ($LogFile)... OK
NTFS volume version is 3.1.
NTFS partition /dev/sdb5 was processed successfully.[/FONT]

However, when trying to mount again, I get the same errors. So, ntfsfix reports a useless success.

How is it possible to fix this?

---

### Post by merlinus on 2007-06-26
Did you try these:

[FONT=Courier New]     mount -t ntfs-3g /dev/disk/by-uuid/01C4DB73D2161100 /media/sdb7 -o force

Or add the option to the relevant row in the /etc/fstab file:

    /dev/disk/by-uuid/01C4DB73D2161100 /media/sdb7 ntfs-3g defaults,force 0 0

If you add the option to /etc/fstab, then run this command in a terminal afterwards:

```

sudo umount -a && sudo mount -a

```

-merlin
[/FONT]

---

### Post by Buendia on 2007-06-26
Thanks Merlin, that did the job.

(1) If I disable and enable ntfs-3g, would it roll-back fstab to what it was?

(2) How can I fix this 'dirty' volume thing without going to windows?

---

### Post by Buendia on 2007-06-26
By the way, I cannot do anything with that dirty disk by qtparted, when I select the disk, qtparted quits, here is what it says in the terminal:


gksu qtparted
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 157
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
No Implementation: Support for opening ntfs file systems is not implemented yet.
No Implementation: Support for opening ntfs file systems is not implemented yet.
No Implementation: Support for opening ntfs file systems is not implemented yet.

---

