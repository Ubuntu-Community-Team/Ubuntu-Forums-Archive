---
title: "How Backup Entire File System?  tar loop?"
date: 2022-10-26
forum: General Help
---

### Post by papertape on 2022-10-26
Ubuntu 20.10
Installed on its own SSD, i.e. no other OS.
But there is a second SSD with a Windows OS and file system, which Ubuntu can see.

How do I back up the entire Ubuntu file system, excluding the Windows SSD?

I tried tar:
  cd /
  sudo tar --create / --file=/home/rjd/alltar --compress --checkpoint=10000 --totals

It appeared to run OK for several minutes, i.e. it produced checkpoint lines at a reasonable rate.
But I left the computer for about a quarter hour.  When I returned, it was spraying about 4 checkpoints/second, and the file count was larger than the number of files in the file system.

Am I right in thinking tar won't add its output file to its output?
Any thoughts on what I can look at?

---

### Post by hartrumpf on 2022-10-27
> **papertape said:**
> 
Am I right in thinking tar won't add its output file to its output?


tar adds your backup file :-(
One simple solution: Create a directory /backups for your backups and add --exclude=/backups to your tar call.

Storing a backup only on the same computer, or even same drive, or even same partition is not a good idea. Copy it to a safer place ...

---

### Post by tea for one on 2022-10-27
Ubuntu 20.10 has reached End of Life and does not receive security updates.
Therefore, trying to back up the complete file system will be a pointless exercise.

Back up your personal data.
Install a supported version e.g. 22.04LTS.

---

### Post by papertape on 2022-10-27
Skipping details, a particular file is giving me trouble, and I wanted to see whether tar could handle the file system.
I dimly remember reading somewhere that tar omits including its output file -- could have been fake news.
Thanks for your help!

---

### Post by HermanAB on 2022-10-28
How about fsarchiver?

---

