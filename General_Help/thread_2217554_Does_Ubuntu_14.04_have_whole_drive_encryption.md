---
title: "Does Ubuntu 14.04 have whole drive encryption?"
date: 2014-04-17
forum: General Help
---

### Post by Vannyi on 2014-04-17
I know 12.04 did not but I understand that newer version included an easy to setup whole drive encryption.  I was just wondering if anyone knows if whole drive encryption made its way into 14.04?

Thank you

---

### Post by oldfred on 2014-04-17
It was in 13.10, so I would expect it to be in 14.04. It uses LVM with a separate /boot partition (and seperate efi partition if UEFI). 
Some users also did not understand that it is a full drive encryption and thought they could dual boot or keep another data partition. It erases entire drive.

I have not used it, but see the encrypt Ubuntu install option.

---

### Post by grier-devon on 2014-04-17
Yes it does, I have mine set up with it and was super easy to set up.

---

### Post by 3rdalbum on 2014-04-18
Yes, whole drive encryption is present on 14.04, but there is a fairly sizable speed penalty.

It would be better for you to just tick the "Encrypt my home directory" option in the installer. Your personal files and application settings will still be encrypted, but the base operating system will not. I really struggle to think of a situation where home directory encryption is not just as good as encrypting the whole drive.

---

### Post by tellapu on 2014-04-28
Interesting article:
The Performance Impact Of Linux Disk Encryption On Ubuntu 14.04 LTS
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_1404_encryption&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_1404_encryption&num=1)
When looking at the CPU usage overall for all of the tests, the standard install  without any form of disk encryption averaged out to 26% for this Intel Core i7  Ultrabook while in the end for the LUKS on LVM and eCryptfs encryption the cost  both averaged out to be about 30~31%.
 From these results, I would continue to highly recommend using full-disk encryption  via LUKS on LVM as opposed to just the eCryptfs-based home directory solution  where the performance actually seemed worse and you're then also not protecting  */tmp* and other areas of the disk.

---

### Post by 3rdalbum on 2014-04-28
Based on the experience on my netbook, whole drive encryption was at least twice as slow as home directory encryption. I reformatted and reinstalled with home directory only and it was much faster.

---

