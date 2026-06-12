---
title: "Bazaar Error"
date: 2007-06-11
forum: General Help
---

### Post by stealth17 on 2007-06-11
I get this error while trying to commit a change using Bazaar:

```
stealth17@stealth17-desktop:~/ubercart$ bzr commit -m'Fixed some descriptions in the UPS module to make it more user-friendly'
bzr: ERROR: bzrlib.errors.UnlockableTransport: Cannot lock: transport is read only: <bzrlib.transport.http._urllib.HttpTransport_urllib url=http://bazaar.ubercart.org/ubercart/alpha/ubercart/.bzr/repository/>

Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/bzrlib/commands.py", line 650, in run_bzr_catch_errors
    return run_bzr(argv)
  File "/usr/lib/python2.5/site-packages/bzrlib/commands.py", line 612, in run_bzr
    ret = run(*run_argv)
  File "/usr/lib/python2.5/site-packages/bzrlib/commands.py", line 304, in run_argv_aliases
    return self.run(**all_cmd_args)
  File "/usr/lib/python2.5/site-packages/bzrlib/builtins.py", line 2118, in run
    reporter=reporter)
  File "/usr/lib/python2.5/site-packages/bzrlib/decorators.py", line 165, in write_locked
    return unbound(self, *args, **kwargs)
  File "/usr/lib/python2.5/site-packages/bzrlib/workingtree_4.py", line 244, in commit
    result = WorkingTree3.commit(self, message, revprops, *args, **kwargs)
  File "/usr/lib/python2.5/site-packages/bzrlib/decorators.py", line 165, in write_locked
    return unbound(self, *args, **kwargs)
  File "/usr/lib/python2.5/site-packages/bzrlib/mutabletree.py", line 160, in commit
    revprops=revprops, *args, **kwargs)
  File "/usr/lib/python2.5/site-packages/bzrlib/commit.py", line 265, in commit
    self._check_bound_branch()
  File "/usr/lib/python2.5/site-packages/bzrlib/commit.py", line 486, in _check_bound_branch
    self.master_branch.lock_write()
  File "/usr/lib/python2.5/site-packages/bzrlib/branch.py", line 1308, in lock_write
    self.repository.lock_write()
  File "/usr/lib/python2.5/site-packages/bzrlib/repository.py", line 235, in lock_write
    self.control_files.lock_write()
  File "/usr/lib/python2.5/site-packages/bzrlib/lockable_files.py", line 234, in lock_write
    self._lock.lock_write()
  File "/usr/lib/python2.5/site-packages/bzrlib/lockdir.py", line 420, in lock_write
    self.wait_lock()
  File "/usr/lib/python2.5/site-packages/bzrlib/lockdir.py", line 387, in wait_lock
    self.attempt_lock()
  File "/usr/lib/python2.5/site-packages/bzrlib/lockdir.py", line 198, in attempt_lock
    raise UnlockableTransport(self.transport)
UnlockableTransport: Cannot lock: transport is read only: <bzrlib.transport.http._urllib.HttpTransport_urllib url=http://bazaar.ubercart.org/ubercart/alpha/ubercart/.bzr/repository/>

bzr 0.15.0 on python 2.5.1.final.0 (linux2)
arguments: ['/usr/bin/bzr', 'commit', '-mFixed some descriptions in the UPS module to make it more user-friendly']
```

Any idea what I did wrong?

---

### Post by AboSamoor on 2008-03-15
Look at this bug report you have to join the team as a member to have write authority
[https://bugs.launchpad.net/launchpad-bazaar/+bug/196913](https://bugs.launchpad.net/launchpad-bazaar/+bug/196913)

---

