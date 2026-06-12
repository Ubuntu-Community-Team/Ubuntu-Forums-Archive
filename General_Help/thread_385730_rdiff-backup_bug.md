---
title: "rdiff-backup bug"
date: 2007-03-16
forum: General Help
---

### Post by moaxey on 2007-03-16
I get this python exception coming up when i run rdiff-backup, in a simple case from one local disk to another.

the destination is a mounted ieee1394

```
$ sudo rdiff-backup /home/mjoakes/ '/media/MatExternal/Mirrors/macbook/' 
Password:
Exception '' raised of class 'exceptions.AssertionError':
  File "/usr/lib/python2.4/site-packages/rdiff_backup/Main.py", line 295, in error_check_Main
    try: Main(arglist)
  File "/usr/lib/python2.4/site-packages/rdiff_backup/Main.py", line 315, in Main
    take_action(rps)
  File "/usr/lib/python2.4/site-packages/rdiff_backup/Main.py", line 271, in take_action
    elif action == "backup": Backup(rps[0], rps[1])
  File "/usr/lib/python2.4/site-packages/rdiff_backup/Main.py", line 325, in Backup
    rpout.conn.fs_abilities.backup_set_globals(rpin)
  File "/usr/lib/python2.4/site-packages/rdiff_backup/fs_abilities.py", line 602, in backup_set_globals
    dest_fsa = FSAbilities('destination').init_readwrite(Globals.rbdir)
  File "/usr/lib/python2.4/site-packages/rdiff_backup/fs_abilities.py", line 138, in init_readwrite
    self.set_case_sensitive_readwrite(subdir)
  File "/usr/lib/python2.4/site-packages/rdiff_backup/fs_abilities.py", line 242, in set_case_sensitive_readwrite
    assert not upper_a.lstat()

Traceback (most recent call last):
  File "/usr/bin/rdiff-backup", line 23, in ?
    rdiff_backup.Main.error_check_Main(sys.argv[1:])
  File "/usr/lib/python2.4/site-packages/rdiff_backup/Main.py", line 295, in error_check_Main
    try: Main(arglist)
  File "/usr/lib/python2.4/site-packages/rdiff_backup/Main.py", line 315, in Main
    take_action(rps)
  File "/usr/lib/python2.4/site-packages/rdiff_backup/Main.py", line 271, in take_action
    elif action == "backup": Backup(rps[0], rps[1])
  File "/usr/lib/python2.4/site-packages/rdiff_backup/Main.py", line 325, in Backup
    rpout.conn.fs_abilities.backup_set_globals(rpin)
  File "/usr/lib/python2.4/site-packages/rdiff_backup/fs_abilities.py", line 602, in backup_set_globals
    dest_fsa = FSAbilities('destination').init_readwrite(Globals.rbdir)
  File "/usr/lib/python2.4/site-packages/rdiff_backup/fs_abilities.py", line 138, in init_readwrite
    self.set_case_sensitive_readwrite(subdir)
  File "/usr/lib/python2.4/site-packages/rdiff_backup/fs_abilities.py", line 242, in set_case_sensitive_readwrite
    assert not upper_a.lstat()
AssertionError
$ 

```

can anyone help? is this a bug in rdiff-backup?

---

### Post by spiffytech on 2007-08-03
I get the same bug in Gentoo. Has anyone found a solution? The only things I find on Google relate to CIFS.

---

