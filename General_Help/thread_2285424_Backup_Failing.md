---
title: "Backup Failing"
date: 2015-07-05
forum: General Help
---

### Post by ndstate on 2015-07-05
Hello,

The backup program Deja Du keeps failing and it displays the following error:

```
Traceback (most recent call last):
  File "/usr/bin/duplicity", line 1494, in <module>
    with_tempdir(main)
  File "/usr/bin/duplicity", line 1488, in with_tempdir
    fn()
  File "/usr/bin/duplicity", line 1337, in main
    do_backup(action)
  File "/usr/bin/duplicity", line 1422, in do_backup
    restore(col_stats)
  File "/usr/bin/duplicity", line 697, in restore
    restore_get_patched_rop_iter(col_stats)):
  File "/usr/lib/python2.7/dist-packages/duplicity/patchdir.py", line 536, in Write_ROPaths
    for ropath in rop_iter:
  File "/usr/lib/python2.7/dist-packages/duplicity/patchdir.py", line 500, in integrate_patch_iters
    for patch_seq in collated:
  File "/usr/lib/python2.7/dist-packages/duplicity/diffdir.py", line 271, in collate2iters
    relem1 = riter1.next()
  File "/usr/lib/python2.7/dist-packages/duplicity/patchdir.py", line 100, in filter_path_iter
    for path in path_iter:
  File "/usr/lib/python2.7/dist-packages/duplicity/patchdir.py", line 113, in difftar2path_iter
    tarinfo_list = [tar_iter.next()]
  File "/usr/lib/python2.7/dist-packages/duplicity/patchdir.py", line 330, in next
    self.set_tarfile()
  File "/usr/lib/python2.7/dist-packages/duplicity/patchdir.py", line 324, in set_tarfile
    self.current_fp = self.fileobj_iter.next()
  File "/usr/bin/duplicity", line 733, in get_fileobj_iter
    backup_set.volume_name_dict[vol_num],
KeyError: 1
```

Any ideas?

Thank you.

---

### Post by ndstate on 2015-07-10
Anyone?

---

### Post by Bucky Ball on 2015-07-10
How did you install deja-dup?

Searching for 'KeyError: 1 deja dup' I found [this]("http://ubuntuforums.org/showthread.php?t=1902900&p=11607515&viewfull=1#post11607515").

Good idea to look for the error at the end and do a search for that, adding other relevant details as you need. If I found nothing on that last search I would have added 'ubuntu'.

Let us know if it works for you as it did on the link.

---

