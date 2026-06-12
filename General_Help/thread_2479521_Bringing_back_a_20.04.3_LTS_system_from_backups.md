---
title: "Bringing back a 20.04.3 LTS system from backups"
date: 2022-09-28
forum: General Help
---

### Post by georgesgiralt on 2022-09-28
Hello !
I have a computer with a failed disk. No problem as I've a set of dump backups done regularly.
I used a new disk, partitioned identically and restored the backups on to it. 
The system boot up but a lot of processes refuse to start. 
For example, db-bus subsystem is running (systemctl says) but gdm complain it can't connect, NetworkManager is said by systemctl that "it had an exit code"and everything like that.
I suspect that restoring /var with it's file backed up from a running system is playing havoc so I wonder what I should/could do to recover the system.
I'll be glad to hear your advice about that. 
Thanks for your help !

---

### Post by aug7744 on 2022-09-28
You are restoring copying directories or an full partition restore ?
See the system date if is correct.

---

### Post by georgesgiralt on 2022-09-28
Hello 
I used that type of command : ```

cd /var && restore -ruf /mnt/backups/dump-<dateofbackup>.var 
```
So as this dump was made on the running system, I wonder if it is legit to restore it ? (I bet it is not because the system is not running now...)

---

### Post by vanadium on 2022-09-28
Better perform a fresh install. The system is then optimally configured to the new situation, and it takes less than an hour.

---

### Post by georgesgiralt on 2022-09-28
> **vanadium said:**
> Better perform a fresh install. The system is then optimally configured to the new situation, and it takes less than an hour.

And more than a week to have it set-up to my liking, with all the software and settings set-up. So a no-go....

---

### Post by dragonfly41 on 2022-09-28
Backups should include what you have installed, e.g. through Synaptic Package Manager.
As experienced users here advise, backup your app installation scripts. And *test *your backups.

---

### Post by georgesgiralt on 2022-09-28
> **dragonfly41 said:**
> Backups should include what you have installed, e.g. through Synaptic Package Manager.
As experienced users here advise, backup your app installation scripts. And *test *your backups.

They did as I do dump each filesystem and restored them.

---

### Post by vanadium on 2022-09-28
To restore configuration, backup all files in your user directory. Reinstalling applications will take an extra fifteen minutes, not more than a week.

Just copying an operating system to a new drive is not a supported way for installation. It may or may not work well. In your case, it doesn´t.

None of us have all wisdom of the world, so with some luck, some advice that you like better may come along.

---

### Post by georgesgiralt on 2022-09-28
Hello, 
I've just found where the problem was. Normally, /var/run is a link to /run and /var/lock to /run/lock. Here, /var/run was a plain directory. Not a link. Moving it's content to /run and removing the directory+ making the soft link cured the problem. 
Thank for your help !
Oh, and BTW, a lot of apps where build onto my system. Not installed with .deb packages. And this takes time. It was not the first time I used backups to restore a system. Be it HP-UX, Aix, Sunos or Solaris or Debian or RedHat or Ubuntu. 40 yeas in Unix/Linux IT make me a fan of backup/restore software....

---

### Post by TheFu on 2022-09-28
Don't create backups on running systems if you don't want file corruption. That's the lesson to be learned here.

There are a number of methods to avoid that, most require using advance volume management at install time and invoking the 'snapshot' method for that volume manager, then creating the backups using the named snapshot.  If you didn't select a volume management system at install time, then you'll have to boot from alternate media to create a backup that won't have file corruption.

There are many backup and restore options which are more efficient than dump/restore.  More efficient in storage and time.  But they all have the risk of corrupted files, unless a volume manager is used to quiesce open files BEFORE backing them up.  With your time in IT, I'd expect you know this already.

---

