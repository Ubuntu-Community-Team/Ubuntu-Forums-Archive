---
title: "Error when backing up using Backups"
date: 2016-07-09
forum: General Help
---

### Post by nmyrick on 2016-07-09
My backups keep failing. I'm backing up to a USB hard drive, and I'm getting the following error. Can anyone tell me what might be causing this? I'm only trying to back up my home folder, not any system folders. I'm running Ubuntu 14.04 LTS.

Traceback (most recent call last):
  File "/usr/bin/duplicity", line 1494, in <module>
    with_tempdir(main)
  File "/usr/bin/duplicity", line 1488, in with_tempdir
    fn()
  File "/usr/bin/duplicity", line 1337, in main
    do_backup(action)
  File "/usr/bin/duplicity", line 1458, in do_backup
    full_backup(col_stats)
  File "/usr/bin/duplicity", line 542, in full_backup
    globals.backend)
  File "/usr/bin/duplicity", line 403, in write_multivol
    globals.gpg_profile, globals.volsize)
  File "/usr/lib/python2.7/dist-packages/duplicity/gpg.py", line 327, in GPGWriteFile
    bytes_to_go = data_size - get_current_size()
  File "/usr/lib/python2.7/dist-packages/duplicity/gpg.py", line 320, in get_current_size
    return os.stat(filename).st_size
OSError: [Errno 2] No such file or directory: '/tmp/duplicity-haOyjb-tempdir/mktemp-E1j0jL-3181'

---

### Post by mastablasta on 2016-07-09
try with some other program. there are plenty with gui. duplicati, backintime, areca, lucky backup, rdiff-backup (this one is CLI), grsync...

have a look here: [http://askubuntu.com/questions/2596/comparison-of-backup-tools](http://askubuntu.com/questions/2596/comparison-of-backup-tools)

---

### Post by nmyrick on 2016-07-09
> **mastablasta said:**
> try with some other program. there are plenty with gui. duplicati, backintime, areca, lucky backup, rdiff-backup (this one is CLI), grsync...

have a look here: [http://askubuntu.com/questions/2596/comparison-of-backup-tools](http://askubuntu.com/questions/2596/comparison-of-backup-tools)

Thank you, Mastablasta. I'm trying back in time right now. I've always had minor issues with Deja Dup, where it wouldn't backup certain files, but everything else would back up so I continued to use it.

---

