---
title: "Delete &quot;RECYCLER&quot; &amp; &quot;System Volume Information&quot; on NTFS partition"
date: 2013-10-03
forum: General Help
---

### Post by geohei on 2013-10-03
Hi.

I have an NTFS formatted HDD containing 1 data partition only (no Windows system on HDD - only data!), which I'd like to use with Ubuntu 12.04 server.

I have some questions.

1.
I mounted the NTFS HDD manually "mount -t ntfs /dev/sdb5 /mnt/ntfs-0". I found the folders "RECYCLER" and "System Volume Information". Can I safely remove these 2 folders without creating filesystem inconsistencies/problems to the NTFS filesystem?

Google showed several hits. This forum as well. But none treated the question if this folder can be safely deleted if (a.) it's not an NTFS system partition and (b.) if it's a pure NTFS data partition.

2.
Can I safely write into this NTFS partition without any risk of data corruption? I remember that Ubuntu NTFS support used to be read-only in the past. How is it now?

Thanks,

---

### Post by GwL3eNC on 2013-10-03
Hello,

i've deleted the RECYCLER folder many times. i would say it's useless if you are shure your trash is trash. If you disable the windows system 
recovery i think the folder System Volume Information is useless but i have never delete it. I wrote often data into nfts partitions,
to me never happens something strange. My automounted ntfs partitions in kubuntu dolphin are writeable without i have to do something.

Greets

---

### Post by geohei on 2013-10-03
Thanks for your reply.

Could you please post the auto mount entry of your NTFS partition you use in fstab?

Since this NTFS partition will never see any Windows system anymore, I believe that "System Volume Information" folder can also be deleted. What do you think?

Thanks,

---

### Post by GwL3eNC on 2013-10-03
Hi,

sorry i don't think about it. Here is it

UUID=2094678F946765EE /media/System ntfs defaults 0 0
UUID=668749435CB12ADA /media/Speicher ntfs defaults 0 0

This are my two partitions. The folders /media/System and /media/Speicher must exist. The long number
you can find using

sudo blkid

I can't tell you to delte the sys vol info folder. You can wait a bit that another one tells something about or you
can try it on your own risk.

---

### Post by geohei on 2013-10-03
I found this here:
[http://ubuntuforums.org/showthread.php?t=839981]("http://ubuntuforums.org/showthread.php?t=839981")
I deleted both folders now. All seems fine so far :)

/etc/fstab is modified according to your suggestion and mounts the NTFS partitions fine now (using UUID i.s.o. devices). Great.

That should be it.

Many thanks!

---

### Post by coffeecat on 2013-10-03
> **geohei said:**
> 
Since this NTFS partition will never see any Windows system anymore

Do you mean that you are not using Windows at all on that system? If it's a data partition shared between Ubuntu server and Windows then NTFS would be a sensible choice of filesystem, but if that data partition is only accessed from an Ubuntu system, why would you use a Microsoft filesystem? Why not use a Linux filesystem? If you get filesystem corruption in NTFS, Linux NTFS tools can fix some problems but not all and there is no substitute for Windows' chkdsk.

---

