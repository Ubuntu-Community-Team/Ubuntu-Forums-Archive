---
title: "Backup failing under ubuntu 13.10"
date: 2013-11-13
forum: General Help
---

### Post by bonsty on 2013-11-13
Hi,

I've been using ubuntu 13.04 on my machine and been able to backup with no problems, however since upgrading to 13.10 I seem unable to do so. I get an error message as follows which I'm unsure on how to interpret:

```

Traceback (most recent call last):
  File "/usr/bin/duplicity", line 1411, in <module>
    with_tempdir(main)
  File "/usr/bin/duplicity", line 1404, in with_tempdir
    fn()
  File "/usr/bin/duplicity", line 1386, in main
    incremental_backup(sig_chain)
  File "/usr/bin/duplicity", line 572, in incremental_backup
    bytes_written = dummy_backup(tarblock_iter)
  File "/usr/bin/duplicity", line 199, in dummy_backup
    while tarblock_iter.next():
  File "/usr/lib/python2.7/dist-packages/duplicity/diffdir.py", line 509, in next
    result = self.process(self.input_iter.next())
  File "/usr/lib/python2.7/dist-packages/duplicity/diffdir.py", line 188, in get_delta_iter
    for new_path, sig_path in collated:
  File "/usr/lib/python2.7/dist-packages/duplicity/diffdir.py", line 269, in collate2iters
    relem1 = riter1.next()
  File "/usr/lib/python2.7/dist-packages/duplicity/selection.py", line 175, in Iterate
    subpath, val = diryield_stack[-1].next()
  File "/usr/lib/python2.7/dist-packages/duplicity/selection.py", line 144, in diryield
    error_handler, Path.append, (path, filename))
  File "/usr/lib/python2.7/dist-packages/duplicity/robust.py", line 37, in check_common_error
    return function(*args)
  File "/usr/lib/python2.7/dist-packages/duplicity/path.py", line 517, in append
    return self.__class__(self.base, self.index + (ext,))
  File "/usr/lib/python2.7/dist-packages/duplicity/path.py", line 497, in __init__
    self.setdata()
  File "/usr/lib/python2.7/dist-packages/duplicity/path.py", line 513, in setdata
    self.symtext = os.readlink(self.name)
OSError: [Errno 38] Function not implemented: '/run/user/1000/gvfs/sftp:host=myserver.org,user=myuser/etc/blkid.tab'

```

If anyone could give me some insight into what's going on here or where else I should be looking for help then that would be hugely appreciated.

Thanks in advance,
Bonsty

---

### Post by Nick_McKinnon on 2013-11-26
I have the same issue... if I find a solution, I'll post here.

Here's what mine says:

Backup Failed

Giving up on request after 5 attempts, last status 500 Internal Server Error

---

