---
title: "Windows XP installer doesn't recognize partitions"
date: 2007-06-05
forum: General Help
---

### Post by DeathOnJuice on 2007-06-05
OK, I was recently resizing my NTFS partition to make room for a new MythTV install. I did it in the Ubuntu LiveCD to be safe. Well, for some reason, when I opened GParted, it would automatically remount my Windows partition, which needed to be unmounted to be worked on. I finally unmounted the partition while GParted was open, which seemed to work. Then, I started the job. Guess what happened? During the middle of the resizing, IT MOUNTED THE PARTITION! Windows no longer boots from GRUB, but Ubuntu boots fine. When I look at the Windows partition from Ubuntu, it seems fine (and shrinked), but it simply won't boot.

So, I decided to reinstall XP. However, when I got to the partitioning screen, it said that there was only a single partition that covered my entire harddrive, which is obviously wrong since I had the shrunken-Windows partition, the Ubuntu partition, and the swap partition inside an extended partition. I even deleted the Windows partition and replaced it with an unformatted partition - no dice.

Is this normal for the Windows install? Would it be safe to make a partition about the same size as the shrunken Windows partition, so it wouldn't cut into the Linux partitions, or would it mess up the magical partition table or whatever it's called? Would a fixmbr or GRUB reinstall do any good?

Thanks in advance!

---

### Post by DeathOnJuice on 2007-06-05
I was just reading a GRUB guide and it said that GRUB puts the partition table in the MBR with itself. Is it possible that the resizing of the Windows partition made the partition table wrong, thus making Windows unbootable? Could I have just reinstalled GRUB? It's too late now that I've deleted the Windows partition, but I still want to know. It would make sense that this is a GRUB problem, since the Windows boot hung while saying "Starting up..." Linux does this briefly when it boots, so I am led to believe that it is a GRUB problem.

I've also read that Linux's and Window's fdisks are incompatible. Does this go for GParted, too? That would explain why the Windows installer can't see my partitions. I still don't know if it would be safe for Linux to make a new partition with the Windows installer.

---

### Post by strabes on 2007-06-06
You could try deleting the ntfs partition in grub and then creating a new ntfs one during the windows xp install process.

---

### Post by DeathOnJuice on 2007-06-06
By GRUB do you mean GParted? Also, are you sure this won't mess up my Ubuntu partitions?

---

### Post by DeathOnJuice on 2007-06-06
Posting to get topic back to front page.

---

