---
title: "Error with rdiff-backup"
date: 2008-05-02
forum: General Help
---

### Post by Amt0571 on 2008-05-02
Hello,

I'm trying to make a backup using rdiff-backup from my desktop computer to my server using the following command:

rdiff-backup /home/amt0571/test 192.168.1.4::/media/sda1/Backups/test

After entering the ssh password, however I'm getting this error:

```
Warning: Local version 1.1.14 does not match remote version 1.1.15.
Exception 'backup_set_globals() takes exactly 2 arguments (1 given)' raised of class '<type 'exceptions.TypeError'>':
  File "/var/lib/python-support/python2.5/rdiff_backup/Main.py", line 302, in error_check_Main
    try: Main(arglist)
  File "/var/lib/python-support/python2.5/rdiff_backup/Main.py", line 322, in Main
    take_action(rps)
  File "/var/lib/python-support/python2.5/rdiff_backup/Main.py", line 278, in take_action
    elif action == "backup": Backup(rps[0], rps[1])
  File "/var/lib/python-support/python2.5/rdiff_backup/Main.py", line 332, in Backup
    rpout.conn.fs_abilities.backup_set_globals(rpin)
  File "/var/lib/python-support/python2.5/rdiff_backup/connection.py", line 447, in __call__
    return apply(self.connection.reval, (self.name,) + args)
  File "/var/lib/python-support/python2.5/rdiff_backup/connection.py", line 369, in reval
    if isinstance(result, Exception): raise result

Traceback (most recent call last):
  File "/usr/bin/rdiff-backup", line 23, in <module>
    rdiff_backup.Main.error_check_Main(sys.argv[1:])
  File "/var/lib/python-support/python2.5/rdiff_backup/Main.py", line 302, in error_check_Main
    try: Main(arglist)
  File "/var/lib/python-support/python2.5/rdiff_backup/Main.py", line 322, in Main
    take_action(rps)
  File "/var/lib/python-support/python2.5/rdiff_backup/Main.py", line 278, in take_action
    elif action == "backup": Backup(rps[0], rps[1])
  File "/var/lib/python-support/python2.5/rdiff_backup/Main.py", line 332, in Backup
    rpout.conn.fs_abilities.backup_set_globals(rpin)
  File "/var/lib/python-support/python2.5/rdiff_backup/connection.py", line 447, in __call__
    return apply(self.connection.reval, (self.name,) + args)
  File "/var/lib/python-support/python2.5/rdiff_backup/connection.py", line 369, in reval
    if isinstance(result, Exception): raise result
TypeError: backup_set_globals() takes exactly 2 arguments (1 given)
Fatal Error: Lost connection to the remote system

```

The desktop machine is running ubuntu 7.10 64bits and the server is running ubuntu 8.04 32bits.

Can somebody help me sort this out? Thanks!

---

### Post by lenticular on 2008-05-05
No answers, but I am seeing exactly the same problem backing up my Hardy laptop to my Gutsy desktop.  Restoring from desktop to laptop worked without a hitch (other than complaint about version mismatch), so it is only backing up that produces this problem.

-John

---

### Post by lenticular on 2008-05-06
I have gotten things working by upgrading rdiff-backup on my Gutsy desktop to 1.1.15. There may be a more straightforward way of doing this, but here is what I did:
All on my gutsy desktop
1) Removed rdiff-backup via synaptic
2) Downloaded and installed librsync .0.9.7 from:
[https://sourceforge.net/project/showfiles.php?group_id=56125](https://sourceforge.net/project/showfiles.php?group_id=56125)
actually, this seems screwy, since Gutsy had a more advanced version of librsync but none of the header files needed to build the new version of rdiff-backup.  

3) Downloaded and extracted rdiff-backup 1.1.15 from:
[http://www.nongnu.org/rdiff-backup/](http://www.nongnu.org/rdiff-backup/)

Afterwards, I was able to backup normally from my Hardy laptop.

Good luck.

-John

---

### Post by tgrimley on 2008-05-19
My error was 

```

Warning: Local version 1.1.15 does not match remote version 1.1.14.

```

I had previously tried upgrading gutsy (my server) to 1.1.15 (like my desktop) with the hardy debs but it didn't like that (wanted to upgrade libc6 too) so I downgraded it back to 1.1.14 and compiled and installed rdiff-backup as lenticular suggests.

Works for me now :)

---

