---
title: "Deja dub Restore Failed"
date: 2013-09-23
forum: General Help
---

### Post by israelodilan on 2013-09-23
I don't know how to work around it but this is the error log file:


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
  File "/usr/lib/python2.7/dist-packages/duplicity/patchdir.py", line 498, in integrate_patch_iters
    for patch_seq in collated:
  File "/usr/lib/python2.7/dist-packages/duplicity/patchdir.py", line 380, in yield_tuples
    setrorps( overflow, elems )
  File "/usr/lib/python2.7/dist-packages/duplicity/patchdir.py", line 369, in setrorps
    elems[i] = iter_list[i].next()
  File "/usr/lib/python2.7/dist-packages/duplicity/patchdir.py", line 113, in difftar2path_iter
    tarinfo_list = [tar_iter.next()]
  File "/usr/lib/python2.7/dist-packages/duplicity/patchdir.py", line 330, in next
    self.set_tarfile()
  File "/usr/lib/python2.7/dist-packages/duplicity/patchdir.py", line 324, in set_tarfile
    self.current_fp = self.fileobj_iter.next()
  File "/usr/bin/duplicity", line 669, in get_fileobj_iter
    manifest.volume_info_dict[vol_num])
  File "/usr/bin/duplicity", line 690, in restore_get_enc_fileobj
    backend.get(filename, tdp)
  File "/usr/lib/python2.7/dist-packages/duplicity/backends/u1backend.py", line 242, in get
    f = open(local_path.name, 'wb')
IOError: [Errno 2] No such file or directory: '/tmp/duplicity-UgHYdq-tempdir/mktemp-N3jBmO-21' 


Any help will be greatly appreciated, I'm sorry im a noob.

---

