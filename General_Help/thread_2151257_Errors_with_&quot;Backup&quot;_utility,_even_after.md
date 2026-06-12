---
title: "Errors with &quot;Backup&quot; utility, even after patching Ubuntu One"
date: 2013-06-03
forum: General Help
---

### Post by pjs@stoddard.us on 2013-06-03
I am trying to backup to Ubuntu-One using the "Backup" program that was loaded with the distro, Ubuntu 13.04 (fully patched).

Here is the error message I am getting:

**************************************

Failed with an unknown error:

Traceback (most recent call last):
  File "/usr/bin/duplicity", line 1411, in <module>
    with_tempdir(main)
  File "/usr/bin/duplicity", line 1404, in with_tempdir
    fn()
  File "/usr/bin/duplicity", line 1338, in main
    restore(col_stats)
  File "/usr/bin/duplicity", line 632, in restore
    restore_get_patched_rop_iter(col_stats)):
  File "/usr/lib/python2.7/dist-packages/duplicity/patchdir.py", line 526, in Write_ROPaths
    for ropath in rop_iter:

++++++++++++++++++++++++++++++++++++++++

  File "/usr/lib/python2.7/dist-packages/duplicity/patchdir.py", line 499, in integrate_patch_iters
    final_ropath = patch_seq2ropath( normalize_ps( patch_seq ) )
  File "/usr/lib/python2.7/dist-packages/duplicity/patchdir.py", line 466, in patch_seq2ropath
    assert len( patch_seq ) == 1, len( patch_seq )
AssertionError: 8

**************************************

Later, I applied some patches, including one about Ubuntu One.  After that I got the same error message, MINUS all the stuff below the ++++++++ line.

Just for laughs, I just tried a restore, and got this error message:

**************************************

Traceback (most recent call last):
  File "/usr/bin/duplicity", line 1411, in <module>
    with_tempdir(main)
  File "/usr/bin/duplicity", line 1404, in with_tempdir
    fn()
  File "/usr/bin/duplicity", line 1282, in main
    sync_archive(decrypt)
  File "/usr/bin/duplicity", line 1082, in sync_archive
    copy_to_local(fn)
  File "/usr/bin/duplicity", line 1023, in copy_to_local
    fileobj = globals.backend.get_fileobj_read(fn)
  File "/usr/lib/python2.7/dist-packages/duplicity/backend.py", line 590, in get_fileobj_read
    self.get(filename, tdp)
  File "/usr/lib/python2.7/dist-packages/duplicity/backends/u1backend.py", line 242, in get
    f = open(local_path.name, 'wb')
IOError: [Errno 2] No such file or directory: '/home/peter/.cache/deja-dup/tmp/duplicity-Sen34G-tempdir/mktemp-7Bi9Gu-2'

***************************************

Ubuntu One under "System Setings" shows 7.2 GB of 65 GB used, so something is getting uploaded, but I can't see it or restore it.

Can someone tell me what is going on here?

---

### Post by pjs@stoddard.us on 2013-06-04
I want to add that I have used the Backup utility to back up files on my home network using SSH, and it works fine.

---

### Post by pjs@stoddard.us on 2013-06-04
Good news.  I don't get error messages any more.  Now for both uploadig and restoring I just get "Giving up on request after 5 attempts, last status 503 Service Unavailable."

---

### Post by pjs@stoddard.us on 2013-06-06
It just started working again.

One thing I did learn though, was that when I start to restore and choose a date fro the menu, I don't get the files uploaded on that date, I get all the files uploaded, through that date.  So be careful when you do a restore -- you re likely to get a lot of stuff.

---

