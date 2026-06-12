---
title: "Backup won't run in 18.04"
date: 2019-03-19
forum: General Help
---

### Post by davidalden on 2019-03-19
I've successfully run the automatic backup many times since installing 18.04.  Now I get the following error message.  Rebooting doesn't help.  Backup hard drive opens just fine and appears to be OK. Error just repeats when backup attempts:

"Backup Failed
Failed with an unknown error:|

Traceback (innermost last):
  File "/usr/bin/duplicity", line 1555, in <module>
    with_tempdir(main)
  File "/usr/bin/duplicity", line 1541, in with_tempdir
    fn()
  File "/usr/bin/duplicity", line 1393, in main
    do_backup(action)
  File "/usr/bin/duplicity", line 1414, in do_backup
    sync_archive()
  File "/usr/bin/duplicity", line 1204, in sync_archive
    copy_to_local(fn)
  File "/usr/bin/duplicity", line 1146, in copy_to_local
    fileobj = globals.backend.get_fileobj_read(fn)
  File "/usr/lib/python2.7/dist-packages/duplicity/backend.py", line 676, in get_fileobj_read
    self.get(filename, tdp)
  File "/usr/lib/python2.7/dist-packages/duplicity/backend.py", line 392, in inner_retry
    util.uexc(e)), code=code, extra=extra)
  File "/usr/lib/python2.7/dist-packages/duplicity/util.py", line 79, in uexc
    return ufn(unicode(e).encode('utf-8'))
 UnicodeDecodeError: 'ascii' codec can't decode byte 0xe2 in position 58: ordinal not in range(128)"

Que pasa amigos?

---

