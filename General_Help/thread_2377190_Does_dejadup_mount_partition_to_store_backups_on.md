---
title: "Does dejadup mount partition to store backups on"
date: 2017-11-10
forum: General Help
---

### Post by robpeteuk on 2017-11-10
Hi, I run deja-dup to backup my files and have done so for a few months. It appears to be working fine, but have not so far tried to restore any of the files.. I have 2 hard drives on my pc , one I use for the operating system and normal use and the other I use for backup. Deja-dup stores the backup files on the backup disk. Neither of the disks is mounted at bootup apart from the lubuntu operating system partition. Deja-dup appears though to automatically mount the partitions and backup the required files at its requested 4 day intervals. Is it necessary or safer to configure the partition containing the files I want backed up and the partition I want the backed up files to be stored on to mount automatically at boot up ?  The partitions are NFTS  as I occasionally use windows.

---

### Post by DuckHook on 2017-11-10
> **robpeteuk said:**
> Hi, I run deja-dup to backup my files and have done so for a few months. It appears to be working fine, but have not so far tried to restore any of the files
Were I you, I would try restoring a couple of files immediately. A backup is not worthy of the name if it can't be restored and will only give you a false sense of security.
> Is it necessary or safer to configure the partition containing the files I want backed up and the partition I want the backed up files to be stored on to mount automatically at boot up ?  The partitions are NFTS  as I occasionally use windows.I don't use deja-dup (I stick with rsync), so perhaps someone else can answer your question more specifically. However, I can say that you may wish to change your backup strategy to a more robust one in any case, irrespective of your backup software. Right now, you are not really backing up in the strict sense of the phrase; you are just sort of mirroring your data every 4 days. The problem with backing up to a permanently installed second HDD is that it is susceptible to the same failure/corruption/attack as the rest of your system. For example, suppose you inadvertently activate a piece of ransomware? That's not that hard to imagine these days. Some of them are very sophisticated and make use of very subtle social engineering to sucker us. These nasties will mount all drives that they can (including network drives that you have permissions to) before encrypting the whole lot. Your backups would be lost along with your primary data.

The best way to backup is to a rotating set of off-machine media (preferably off-site media) that is then disconnected from your computer until the next backup. With the price and capacity of USB sticks these days, it's not that expensive to set up a system of incremental backups that protect you properly.

Just my 2-pennies.

---

