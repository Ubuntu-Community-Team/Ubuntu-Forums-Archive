---
title: "backup drive for deja-dup: encrypt partition, or backups?"
date: 2015-02-08
forum: General Help
---

### Post by Allen McBride on 2015-02-08
I'm about to start using a backup drive with Deja-Dup, and I'm curious: Is there a common wisdom about whether I should encrypt the whole partition when I format the drive? Or should I just tell Deja-Dup to encrypt its backups? Is it just personal preference, or would one be substantially faster or more secure? I'd welcome your insight!

---

### Post by TheFu on 2015-02-10
Don't think there is any common wisdom here.  I'd be more likely to encrypt the backups and not the disk because sometimes disks have failures and when they are encrypted, the only real solution is to restore from backups. If the backups are stored on the bad partition, well ... not so useful.
Without encryption, there are many tools that can be used to restore the data, at least partially.

OTOH, if you are a government agency or any company with personal metadata about people/clients/dogs/cats - please, please, please encrypt the disks AND the backups. I'm tired of reading about data breaches where static encryption would have prevented it completely.  Of course, there are many ways to get the data while the system is running and the partition must be decrypted to be useful, so whole partition encryption isn't the only security needed.

---

### Post by Allen McBride on 2015-02-18
Thanks very much, this is helpful! Sorry I didn't respond sooner; I checked after about a day and no one had responded so I gave up. I'll search around for a setting where I'd get e-mailed when someone responds to one of my questions.

---

