---
title: "Testdisk Help"
date: 2013-02-24
forum: General Help
---

### Post by grygub on 2013-02-24
I am in a pretty tight spot here if there are any testdisk experts out there. I have done significant reading but am at a standstill

I have a 4 drive 6tb raid 5 array 
From memory it was partitioned as follows

Very Small MBR partition
~800mb boot partition
~400gb ubuntu root partition
~5.5tb NTFS storage partition
~4 gb swap partition

Everything digitally important to me is on that ntfs partition. Mythtv recordings, videos, family pictures.

When re-installing Ubuntu I chose the "install over Ubuntu 12.10" option not expecting it to install it over all partitions. It made one huge partition on the drive with a small swap partition at the end.

I was optimistic testdisk would be able to help me because there should be plenty of space between where the new operating system files were installed and where the ntfs partition begins.
 
I am loosing this optimism. I added another harddisk to the computer and am running a new install of ubuntu from this new disk. Here is the result of the quick scan. It seems to have found the ntfs partition but do the chs make sense to you for such a large partition?

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=231848&stc=1&d=1361685730[/IMG]

This error about drive size not being right is this a big deal? Im not really sure how many cylinders, heads, sectors there should be with it being a raid array.

Any ideas why it is not recoverable? Is this a lost cause?

I ran a deep scan and the results didn't seem any better. I will post the screen shot after it finishes running again.

Any help will be greatly appreciated

---

### Post by dino99 on 2013-02-24
Steps:
-unmount the array
-use testdisk
-rebuild the array

[http://askubuntu.com/questions/174172/data-hidden-or-lost-on-hdds-in-raid1-on-ubuntu-server-12-04](http://askubuntu.com/questions/174172/data-hidden-or-lost-on-hdds-in-raid1-on-ubuntu-server-12-04)

---

