---
title: "(Ubuntu 14.0)Please help! I cant restore my backup done with deja dup in ubuntu 12.04"
date: 2014-04-25
forum: General Help
---

### Post by tiappendi on 2014-04-25
im trying to restore my backup in ubuntu 14.04 but he dont want to collaborate (as you can see from some letter non recognized)
Deja dup gives me some errors trying to restore my backup also using terminal.

How i can resolve? i have tried all ways](*,)

```
Data dell'ultimo backup completo: Thu Mar 13 11:28:38 2014Errore "[Errno 1] Operation not permitted: '/home /giulio/Scrivania/bakp/home/giulio/.config/gedit/accels'" elaborando home/giulio/.config/gedit/accels
Errore "[Errno 1] Operation not permitted: '/home/giulio/Scrivania/bakp/home/giulio/.config/gedit'" elaborando .
Error '49' patching home/giulio/Scrivania/DOC/FOTO ROBA/e-books/il male sconosciuto (andrea pazienza).pdf
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
  File "/usr/lib/python2.7/dist-packages/duplicity/patchdir.py", line 380, in yield_tuples
    setrorps( overflow, elems )
  File "/usr/lib/python2.7/dist-packages/duplicity/patchdir.py", line 369, in setrorps
    elems[i] = iter_list[i].next()
  File "/usr/lib/python2.7/dist-packages/duplicity/patchdir.py", line 120, in difftar2path_iter
    multivol_fileobj.close() # aborting in middle of multivol
  File "/usr/lib/python2.7/dist-packages/duplicity/patchdir.py", line 240, in close
    if not self.addtobuffer():
  File "/usr/lib/python2.7/dist-packages/duplicity/patchdir.py", line 223, in addtobuffer
    fp = self.tf.extractfile( self.tarinfo_list[0] )
  File "/usr/lib/python2.7/dist-packages/duplicity/patchdir.py", line 340, in extractfile
    return self.tarfile.extractfile( tarinfo )
  File "/usr/lib/python2.7/dist-packages/duplicity/tarfile.py", line 2111, in extractfile
    self._check("r")
  File "/usr/lib/python2.7/dist-packages/duplicity/tarfile.py", line 2394, in _check
    raise IOError("%s is closed" % self.__class__.__name__)
IOError: TarFile is closed



```

---

### Post by coffeecat on 2014-04-25
Support, not an Ubuntu, Linux & Other OS Chat thread.

*Thread moved to **General Help**.*

---

