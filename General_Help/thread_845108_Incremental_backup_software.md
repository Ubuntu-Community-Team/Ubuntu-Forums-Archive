---
title: "Incremental backup software"
date: 2008-06-30
forum: General Help
---

### Post by LK_gandalf_ on 2008-06-30
Hi, I'm searching for a software ( I use kubuntu 8.04 ) that makes incremental backup. I've tried Flyback, but I have a problem.

I've created a backup, manually, of my home directory. Then some days before I've created another snapshot, but...on my backup drive (external usb) I see the two directory of the snapshots but each one has the same size of the original one!!

Original: 11 gb
snapshot #1: 11gb
snapshot #2: 11gb

I don't think this is a clever incremental backup mode, it uses an huge amount of memory!
I think only the first backup should occupy the same amount of memory of the original folder, then the following backups should only register the differences in the files, isn't?

---

### Post by sa_venkatesan on 2008-06-30
It seems like your program has created multiple full backup images.  Btw, have you tried rsnapshot? I have been using it for a while and it works great. It uses hard links to create full backup images but conserves disk usage because each file appear only once across  backups. The rest of the backups have only links to the file. 

This combines the best features of the incremental backups (space utilization) and full backups (easy restore).   Check it out, it is available in Ubuntu universe repositories.



> **LK_gandalf_ said:**
> Hi, I'm searching for a software ( I use kubuntu 8.04 ) that makes incremental backup. I've tried Flyback, but I have a problem.

I've created a backup, manually, of my home directory. Then some days before I've created another snapshot, but...on my backup drive (external usb) I see the two directory of the snapshots but each one has the same size of the original one!!

Original: 11 gb
snapshot #1: 11gb
snapshot #2: 11gb

I don't think this is a clever incremental backup mode, it uses an huge amount of memory!
I think only the first backup should occupy the same amount of memory of the original folder, then the following backups should only register the differences in the files, isn't?

---

### Post by pawnrocket on 2008-06-30
sbackup

```
sudo apt-get install sbackup
```

---

