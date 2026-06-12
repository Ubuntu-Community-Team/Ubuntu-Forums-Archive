---
title: "Nautilus slow in opening windows partition"
date: 2007-11-03
forum: General Help
---

### Post by Mateo on 2007-11-03
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/159775](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/159775) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Only the first time when I start the computer and go to the windows partition.  I think what it is doing is cataloging the entire disc each time.  is this a trackerd issue maybe?  i don't know.  This has only happened since Gutsy.  what is the first step to remedying this problem?

---

### Post by noynac on 2007-11-03
Is your Windows partition NTFS or FAT32? I've had the same problem but only with FAT32 partitions.

---

### Post by Mateo on 2007-11-03
i believe it is fat32.  what is the solutoin?

---

### Post by noynac on 2007-11-03
> **Mateo said:**
> i believe it is fat32.  what is the solutoin?

This problem has been around since Gutsy was in Alpha. I spent some time researching the issue but never found a solution. I finally converted the partition to NTFS, which works fine.

---

### Post by Mateo on 2007-11-03
that's odd.  is it a gutsy problem or a problem of the newer version of nautilus?

---

### Post by noynac on 2007-11-04
> **Mateo said:**
> that's odd.  is it a gutsy problem or a problem of the newer version of nautilus?

That's an interesting question--I had always assumed it was a Gutsy problem. 

I still have a FAT32 partition that Nautilus is slow to access. I accessed and did some stuff on this partition from a terminal, and there was no delay at all. So, perhaps it is Nautilus.

I really don't know all that much about how disks and operating systems work. But, I do hope they fix it soon.

---

### Post by Mateo on 2007-11-04
The "System Monitor"  application does the same thing.  If you press the "File Systems" tab, it takes a while.  Only on that tab, though.  And only the first time you use it when the computer starts.  I don't know if the System Monitor is connected to Nautilus in any way.

---

### Post by Mateo on 2007-11-04
I think I might have found a solution.  Stay tuned.

---

