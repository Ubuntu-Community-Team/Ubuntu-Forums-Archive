---
title: "XP bluescreen after interrupted 804 install"
date: 2008-06-16
forum: General Help
---

### Post by e13 on 2008-06-16
Hello,

I was installing Ubuntu 804 release to T41 with XP SP2 currently installed/working.

I had somewhere near the end of install, when installer started polling time from timeserver, thru wifi card while there is no public networks. Even adding ethernet cable after 15 min of waiting did not change anything. After nearly an hour long wait, I tried to stop install, closing this little status-bar-window. With success but with no reaction... Then I just killed the machine. 

New try. Installer did not recognise windows partition, offered to split the one he just created for itself on previous run... I had to specify manually, where is root and where is swap. Holding ethernet cable pluged in, this time installer finished successfully.

But after rebooting and trying to boot xp, I ran into bluescreen with message starting "Stop 0x0000007B". Boot from XP cd and choosing recovery console option ended with C:> prompt preceeded with warning that path or filename was incorrect. Map command shows only CDROM, no HDD. Therefor no fixmbr or fixboot or chkdsk...

Ubuntu 804 in the other hand boots just fine, can mount forementioned ntfs partition and all... I installed testdisk, ran it with attempt to rebuild bootsector, which testdisk reported bad at first. Rebuild was successful. Reboot ended again with bluescreen...

Again back to ubuntu, testdisk. This time Repair MFT option - segfault.

Now also gparted reports that "Cluster accounting failed @ xxxx: extra cluster in $Bitmap", which he did not previously say.

fsck responds with Error 2 while executing fsck.ntfs for...

Any ideas?

---

