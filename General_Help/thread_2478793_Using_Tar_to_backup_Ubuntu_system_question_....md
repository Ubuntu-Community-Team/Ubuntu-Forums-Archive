---
title: "Using Tar to backup Ubuntu system question ..."
date: 2022-09-05
forum: General Help
---

### Post by michael351 on 2022-09-05
What is the best syntax to use (tar command) when backing up an Ubuntu installation to an external USB hard drive so that if my system disk becomes corrupted I can restore easily.

Would someone check that I have the command below correct:

cd/
tar -cvpzf /mnt/backup/backup.tar.gz --exclude=/backup.tar.gz --one-file-system / 

where /mnt/backup is a mounted USB external hard drive.

---

### Post by TheFu on 2022-09-05
Don't use tar to backup anything larger than 500MB.  It wasn't designed for that.

For larger stuff, use a real backup tool. Which of the tools to use depends on your specific compromises around speed, storage, security, risk mitigation and target file system.  For almost everyone, something like duplicity is the best answer. There are GUI tools, if you need that.

Tar is like ZIP.  Would you really attempt to backup a system using ZIP?  I wouldn't.

---

