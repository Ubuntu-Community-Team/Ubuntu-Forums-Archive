---
title: "luckyBackup permissions problem - permission denied(13)"
date: 2013-07-14
forum: General Help
---

### Post by scruffyeagle on 2013-07-14
I'm trying to do a backup using Ubuntu v10.04 LTS on a Dell laptop & the "luckyBackup" program.  I'm having a problem that I don't understand.

I have 2 external HD's.  One of them is my primary storage, and the secondary is mirrored storage for the main external HD.  Both external drives are partitioned to contain 8 partitions.  All 8 on both are encrypted using TrueCrypt.  All 8 on both mount & dismount normally w/ Read/Write permissions.

I'm trying to do a backup of partition 1 on the main external drive to partition 1 of the secondary external drive.  I can manually copy, paste, & delete files on both partitions. However, when I try to do an automated backup, I receive the error message

rsync: opendir "media/truecrypt1/System Volume Information" failed: permission denied(13)

This is about the source drive; i.e., the primary that I use all the time. The reason this puzzles me, is that I've done this exact same backup before, and it worked without any problem at all.  In fact, immediately after the backup of partition 1 failed, I did a backup of partition 2 and it worked flawlessly.

What may be a cause (somehow) is that I'd been doing backups involving the primary's partition 1 using a Ubuntu v10.04 LTS installation on a Toshiba laptop earlier in the evening.  I have that laptop's internal HD partitioned into multiple partitions because I've got several different OS's installed on it for  the sake of playing around with.  However, it has one partition that contains a subset of the contents of the primary external drive's partition 1.  So, I was using luckyBackup on the Toshiba, to maintain sync of the subset of files mirrored on the primary external HD. (Maybe that somehow changed "System Volume Information" permissions on the primary external HD's partion 1?)

I tried searching online, and did find some links involving this error message - but, I couldn't find any references to it happening involving the source drive of the backup operation.

Can anybody explain to me what's gone wrong here?  Thanks in advance.

---

### Post by scruffyeagle on 2013-07-16
I found a solution, although I'm not sure it's a very good one.  Here's what I did:

I opened a terminal, and typed in the command

```
gksu /usr/bin/luckybackup
```

After providing my password, it opened luckyBackup in superuser mode.  The various backup tasks I'd defined previously in normal mode weren't there, so I had to create a new set of tasks - but, those newly created tasks did run without generating any errors.

I think my problem was caused by the fact that I've opened several of the partitions using TrueCrypt in Windows.  (I'd formatted them as NTFS for exactly that purpose.)  The Windows OS created the "System Volume Information" directories hanging around in the partitions, and Ubuntu was smart enough to know that not only were those directories system folders, but those directories were also proprietary to some other user besides my currently logged in identity; that's why it balked at modifying them.  When my identity was the root, I had the authority to modify them.

So, this issue has been solved.  Sort of.  I don't know yet if there will be any malfunctions caused by monkeying w/ the System Volume Information folders or not.  I guess, I'll discover that later; probably, the next time I use those partitions in Windows.

---

