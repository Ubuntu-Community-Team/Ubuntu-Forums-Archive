---
title: "Recover Data on Samba"
date: 2007-07-02
forum: General Help
---

### Post by Forgott3n on 2007-07-02
Hello,

I have had a serious issue which involved the corruption of the registry in Windows XP SP2 Pro. I quickly booted into my Ubuntu 7.04 Feisty partition and recovered the data via the mounted NTFS partition (Windows). I then backed up the data via Samba to smb://main/SpencerMain/BACKUP/Justin/JUSTIN-LAPTOP/06-27-07/

It took around 3 hours to transfer all data to the folder. Afterwards I shutdown the computer and reformatted Windows XP SP2 Pro. Later when I go to restore the data I get an error saying something like "Cyclic Redundancy Error" and I cannot open the 06-27-07 folder. I tried opening the folder over samba in Windows, Ubuntu, opening the folder on the host computer, everything. I cannot get it to open.

Is there any form of recovery tools I can use to try to get some of the data back? Also, since I reformatted my Windows partition, it overwrote GRUB.. How do I restore it?

And finally, when I tried again today, I got a different error message:

[img]http://img337.imageshack.us/img337/449/issueti0.gif[/img]

---

### Post by dannyboy79 on 2007-07-02
what physical disk holds the data? In other words, what disk was moutned to smb://main/SpencerMain/BACKUP/Justin/JUSTIN-LAPTOP/06-27-07/ when you performed the transferring of the data? all you should do is mount the drive locally in either ubuntu or windows xp and access the data there instead of trying to access it thru samba. If you are trying to access the data and this is what's occurring, then you should first see if the partition table is ok and if there's any formatted filesystem's on the disk in question. if so, then you might be able to retrieve your data possibly using TestDisk to rebuild any missing partitions etc etc. It doesn't sound good. 

You haven't really explained everything very well. Are you dual booting, are you writing to a NTFS disk from within ubuntu and that ntfs is the same disk that had your windows xp install on it, registry and all? What filesystem is the share that was mounted over samba?

---

