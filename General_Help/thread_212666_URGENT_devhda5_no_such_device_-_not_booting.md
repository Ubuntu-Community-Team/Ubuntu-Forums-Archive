---
title: "URGENT dev/hda5 no such device - not booting"
date: 2006-07-10
forum: General Help
---

### Post by skewer on 2006-07-10
Hi

I have been dual booting xp/dapper, not using XP more than 2 or 3 times in the last month. I went into XP today, made a new user, logged out, logged in as my new XP user, and rebooted, then after the GRUB menu (I chose Ubuntu as usual) I saw the boot screen, but...

after the 2nd item in the boot sequence (mounting root file system or whatever) had been there for a few seconds, I got a list of errors starting with something like
"failed to mount dev/hda5 on /root: no such device" 
and continuing with other "failed to mount" errors saying "no such file/folder" - no surprise if the device wasn't found!

There were other errors, apparently hda5 does not have sbin/something, and there was some reference to tty that I should have written down.

Can anyone advise me how to resotre this? I am using EXT2IFS on XP to salvage as much as I can from the home folders of my 2 Ubuntu users, and will try again soon.

I'll also note the errors in full if someone thinks they could help with this extra detailed info, in the meantime I'm kind of panicking.

Thanks
SQR

---

### Post by aysiu on 2006-07-10
Do you have a live CD?

Rather than trying to recover individual home folder contents, consider creating a separate home so that a reinstall is relatively painless.
[http://www.psychocats.net/ubuntu/separatehome.html](http://www.psychocats.net/ubuntu/separatehome.html)

---

### Post by skewer on 2006-07-10
aysiu, thank you!

I didn't (yet) create and implement a new home partition, but I did shrink my FAT32 store (for XP <-> dapper file sharing) since I now have XP reading EXT3 and dapper can obviously read NTFS. The 10GB or so I freed up is now EXT3, but unmounted.

I had a warning that "at least one operation was applied to a busy device" - and gParted showed my swap partition was being used (surely by the live session) - and I was advised to reboot. I left the CD out for a test, and hda5 booted fine!

I had to edit /etc/fstab to reassign my FAT32 and SWAP partitions, they had been swapped from ha6 and hda7 to hda7 and hda6 (or the other way round...). I have yet to add a line to put hda8 - the new ext3 - into the list, I will do that as a new HOME soon enough. :)

I would not have thought to edit the partition table as part of the fix, especially since Patition Magic in XP reported that the EXT3 volume was 15.3GB (correct), with 100% used space (NOT correct!!!). Since I could see the files with EXT2IFS I was thinking a full reinstall and large scale restoration of files would be in order, complete with hours of software downloads and updates...

So thanks again, by simply following half a step I found my problem solved, and the home partition makes a lot of sense. I think I'll empty my fat32 drive and merge it into the home partition when the time comes, to get 25GB or so.

---

