---
title: "Deja Dup no longer working: UnicodeDecodeError"
date: 2014-06-05
forum: General Help
---

### Post by diegoma on 2014-06-05
Hi,

Deja Dup stopped working, I think it stopped when I upgraded to KUbuntu 14.04. Below is the error message. I searched the forums and I saw a couple of similar posts a few years ago but nobody gave a solution/explanation... can someone help?

Diego

Traceback (most recent call last):
  File "/usr/bin/duplicity", line 1494, in <module>
    with_tempdir(main)
  File "/usr/bin/duplicity", line 1488, in with_tempdir
    fn()
  File "/usr/bin/duplicity", line 1337, in main
    do_backup(action)
  File "/usr/bin/duplicity", line 1366, in do_backup
    sync_archive(decrypt)
  File "/usr/bin/duplicity", line 1100, in sync_archive
    remote_metafiles, ignored, rem_needpass = get_metafiles(remlist)
  File "/usr/bin/duplicity", line 992, in get_metafiles
    pr = file_naming.parse(fn)
  File "/usr/lib/python2.7/dist-packages/duplicity/file_naming.py", line 389, in parse
    pr = check_full()
  File "/usr/lib/python2.7/dist-packages/duplicity/file_naming.py", line 308, in check_full
    t = str2time((m1 or m2).group("time"), short)
  File "/usr/lib/python2.7/dist-packages/duplicity/file_naming.py", line 281, in str2time
    t = dup_time.genstrtotime(timestr.upper())
  File "/usr/lib/python2.7/dist-packages/duplicity/dup_time.py", line 278, in genstrtotime
    return override_curtime - intstringtoseconds(timestr)
  File "/usr/lib/python2.7/dist-packages/duplicity/dup_time.py", line 190, in intstringtoseconds
    error()
  File "/usr/lib/python2.7/dist-packages/duplicity/dup_time.py", line 181, in error
    raise TimeException(bad_interval_string % interval_string)
UnicodeDecodeError: 'ascii' codec can't decode byte 0xe7 in position 15: ordinal not in range(128)

---

### Post by diegoma on 2014-06-11
I got round the problem by deleting the old back up and making a new back up. Of course this doesn't solve the problem, I still don't know why the above error happened, and I lost all the past backups. Clearly this is not a way to solve this issue and I'll consider using a different backup program if the problem happens again.

A side-effect of deleting the old back up is that now the computer is much faster. It looks that deja dup was running in the background and taking computing resources...?

If anybody knows the answers to any of these questions please post here.

Diego

---

