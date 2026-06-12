---
title: "Backup Fails can't change permissions after fresh install of Ubuntu 18.04"
date: 2019-02-23
forum: General Help
---

### Post by AnimalMother! on 2019-02-23
First, a little background on my setup:  I have a hybrid setup with my / mounted on a 500 GB SSD and my /home mounted on a 2 TB HDD.  I recently tried upgrading from 16.04 to 18.04 but after encountering several errors opted for a fresh install of 18.04.  The benefit to my setup is that I can install a fresh copy of the OS without touching my home folder.  So I don't have to go through the additional step of restoring a backup.  However, I believe this to be the root of my problem.

When attempting to backup I was encountering errors that indicate a permissions issue.  Looking at other forum posts I discerned that deja-dup requires root permissions or at least uses another account to write to my external hard drive.  I can access everything on my external hard drive and even write to it, but when attempting to change permissions for other users it fails.  A chmod appears to work but upon checking permissions after nothing has changed.  Additionally, in the GUI I cannot change the permissions for other users from anything but access only.

---

### Post by AnimalMother! on 2019-02-23
Here is the initial fail log from deja-dup:

Traceback (innermost last):
  File "/usr/bin/duplicity", line 1555, in <module>
    with_tempdir(main)
  File "/usr/bin/duplicity", line 1541, in with_tempdir
    fn()
  File "/usr/bin/duplicity", line 1393, in main
    do_backup(action)
  File "/usr/bin/duplicity", line 1511, in do_backup
    full_backup(col_stats)
  File "/usr/bin/duplicity", line 572, in full_backup
    globals.backend)
  File "/usr/bin/duplicity", line 454, in write_multivol
    (tdp, dest_filename, vol_num)))
  File "/usr/lib/python2.7/dist-packages/duplicity/asyncscheduler.py", line 146, in schedule_task
    return self.__run_synchronously(fn, params)
  File "/usr/lib/python2.7/dist-packages/duplicity/asyncscheduler.py", line 172, in __run_synchronously
    ret = fn(*params)
  File "/usr/bin/duplicity", line 453, in <lambda>
    vol_num: put(tdp, dest_filename, vol_num),
  File "/usr/bin/duplicity", line 342, in put
    backend.put(tdp, dest_filename)
  File "/usr/lib/python2.7/dist-packages/duplicity/backend.py", line 395, in inner_retry
    % (n, e.__class__.__name__, util.uexc(e)))
  File "/usr/lib/python2.7/dist-packages/duplicity/util.py", line 79, in uexc
    return ufn(unicode(e).encode('utf-8'))
 UnicodeDecodeError: 'ascii' codec can't decode byte 0xe2 in position 37: ordinal not in range(128)

---

