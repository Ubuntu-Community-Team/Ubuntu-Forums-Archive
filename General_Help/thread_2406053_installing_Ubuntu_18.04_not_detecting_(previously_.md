---
title: "installing Ubuntu 18.04 not detecting (previously existing) encrypted home partition"
date: 2018-11-15
forum: General Help
---

### Post by 0ll0 on 2018-11-15
Hello
saying the 18.04 released and testing is over, the admin closed this thread: [https://ubuntuforums.org/showthread.php?t=2386852](https://ubuntuforums.org/showthread.php?t=2386852)
and proposed to open a new one — which as far as I see didn't happen.

The thread was was about accessing an existing ecryptfs-encrypted home after a new installation, quote

@roma24ster
> I have two '/' partitions, one with Ubuntu 16.04, and another with 18.04. I've pointed them both to the same home partition, which is encrypted.

this doesn't work. you can still login on 16.04 but not on 18.04 
if you point its home partition to the encrypted one of 16.04, 
because 18.04 doesn't know that you use an existing encrypted home — and it seems there is no way to tell.

Since there is no way to upgrade from 32 to 64 bit ubuntu (or linux in general), 
I actually ran into the same situation after installing 16.04 (64 bit) in a new partition 
trying to access the encrypted home of my old 16.04 (32 bit) partition.
To make things more difficult, my home was not in a separate partition but part of the 32 bit root.

I got my old encrypted home working under 16.04 (64 bit) following this guide:
[http://www.interesting-books-selector.com/index.php?m=select&id=linux32u64](http://www.interesting-books-selector.com/index.php?m=select&id=linux32u64)

---

### Post by TheFu on 2018-11-15
18.04 removed the encrypted HOME capability. There were a number of issues with it.  Security and performance were the most important.

[https://wiki.ubuntu.com/BionicBeaver/ReleaseNotes#Other_base_system_changes_since_16.04_LTS](https://wiki.ubuntu.com/BionicBeaver/ReleaseNotes#Other_base_system_changes_since_16.04_LTS) is the 18.04 release notes where this is mentioned.  Always review the release notes for every release and always make a know-you-can-restore backup before beginning the process.

There are upgrade paths between 32-bit and 64-bit Ubuntu installations. They just happen to be complicated and use data backups and restores.  I can understand why some people might find this less than ideal.

[https://help.ubuntu.com/community/EncryptedHome](https://help.ubuntu.com/community/EncryptedHome) has information about handling some different situation with an encrypted HOME, including some caveats.

---

