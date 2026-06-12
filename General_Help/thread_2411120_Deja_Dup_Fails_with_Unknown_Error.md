---
title: "Deja Dup Fails with Unknown Error"
date: 2019-01-24
forum: General Help
---

### Post by James_Nostack on 2019-01-24
Apologies if this is in the wrong sub-forum.

I'm using Ubuntu 18.04 LTS, and over the last month or two I've had a problem with Deja Dup saving to my external hard drive.  It responds with the following error message, even when I've removed the program and re-installed a fresh copy:

```
Traceback (innermost last):
  File "/usr/bin/duplicity", line 1555, in <module>
    with_tempdir(main)
  File "/usr/bin/duplicity", line 1541, in with_tempdir
    fn()
  File "/usr/bin/duplicity", line 1393, in main
    do_backup(action)
  File "/usr/bin/duplicity", line 1472, in do_backup
    restore(col_stats)
  File "/usr/bin/duplicity", line 728, in restore
    restore_get_patched_rop_iter(col_stats)):
  File "/usr/lib/python2.7/dist-packages/duplicity/patchdir.py", line 558, in Write_ROPaths
    for ropath in rop_iter:
  File "/usr/lib/python2.7/dist-packages/duplicity/patchdir.py", line 521, in integrate_patch_iters
    for patch_seq in collated:
  File "/usr/lib/python2.7/dist-packages/duplicity/patchdir.py", line 389, in yield_tuples
    setrorps(overflow, elems)
  File "/usr/lib/python2.7/dist-packages/duplicity/patchdir.py", line 378, in setrorps
    elems[i] = iter_list[i].next()
  File "/usr/lib/python2.7/dist-packages/duplicity/patchdir.py", line 107, in filter_path_iter
    for path in path_iter:
  File "/usr/lib/python2.7/dist-packages/duplicity/patchdir.py", line 121, in difftar2path_iter
    tarinfo_list = [tar_iter.next()]
  File "/usr/lib/python2.7/dist-packages/duplicity/patchdir.py", line 339, in next
    self.set_tarfile()
  File "/usr/lib/python2.7/dist-packages/duplicity/patchdir.py", line 333, in set_tarfile
    self.current_fp = self.fileobj_iter.next()
  File "/usr/bin/duplicity", line 764, in get_fileobj_iter
    backup_set.volume_name_dict[vol_num],
 KeyError: 1
```

Obviously I'm not entirely sure what's going on here.  At one point, Deja Dup would grey out the "back up now" option on the main screen, but that seems to be working fine now.

---

