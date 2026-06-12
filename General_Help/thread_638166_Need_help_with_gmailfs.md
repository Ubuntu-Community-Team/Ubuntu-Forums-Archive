---
title: "Need help with gmailfs"
date: 2007-12-11
forum: General Help
---

### Post by jacensolo on 2007-12-11
I get this error when trying to mount gmailfs.
```
Ignored option :rw
HTTP Error 400: Bad Request
fuse: bad mount point `/mnt/gmail': No space left on device
Traceback (most recent call last):
  File "/sbin/mount.gmailfs", line 166, in <module>
    main(mountpoint, namedOptions, useEncfs)
  File "/sbin/mount.gmailfs", line 92, in main
    gmailfs.main(mountpoint, namedOptions)
  File "/usr/lib/python2.5/site-packages/gmailfs.py", line 1180, in main
    server.main()
  File "/usr/lib/python2.5/site-packages/fuse.py", line 713, in main
    main(**d)
fuse.FuseError: filesystem initialization failed
Error in sys.excepthook:
Traceback (most recent call last):
  File "/var/lib/python-support/python2.5/apport_python_hook.py", line 42, in apport_excepthook
    binary = os.path.realpath(os.path.join(os.getcwdu(), sys.argv[0]))
IndexError: list index out of range

Original exception was:
Traceback (most recent call last):
  File "/sbin/mount.gmailfs", line 166, in <module>
    main(mountpoint, namedOptions, useEncfs)
  File "/sbin/mount.gmailfs", line 92, in main
    gmailfs.main(mountpoint, namedOptions)
  File "/usr/lib/python2.5/site-packages/gmailfs.py", line 1180, in main
    server.main()
  File "/usr/lib/python2.5/site-packages/fuse.py", line 713, in main
    main(**d)
fuse.FuseError: filesystem initialization failed

```

Does anybody have any idea what to do? I believe I have all the dependencies since I downloaded it from the repositories.

---

### Post by brennydoogles on 2007-12-11
I have never actually heard of GmailFS working in Ubuntu (although I must admit that my research on the subject was a few months ago and somewhat limited) Another option may be the Gspace extension for Firefox.

---

