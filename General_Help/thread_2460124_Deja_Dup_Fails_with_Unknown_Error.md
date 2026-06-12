---
title: "Deja Dup Fails with Unknown Error"
date: 2021-04-03
forum: General Help
---

### Post by doubletop12 on 2021-04-03
I'm getting this error on Ubuntu 20.04. Backups are running daily and regular verifies don't fail. I seem to be able to full restore to my system disk but single file or folders restores will fail and and attempts to full restore to another folder fails.

Ive set ```
export DEJA_DUP_DEBUG=1
``` but don't get messages, even in the "details text box"

I have tried starting Deja Dup as root from a terminal session ```
sudo deja-dup.
``` That fails as well 

> Traceback (innermost last):
  File "/usr/bin/duplicity", line 106, in <module>
    with_tempdir(main)
  File "/usr/bin/duplicity", line 92, in with_tempdir
    fn()
  File "/usr/lib/python3/dist-packages/duplicity/dup_main.py", line 1525, in main
    action = commandline.ProcessCommandLine(sys.argv[1:])
  File "/usr/lib/python3/dist-packages/duplicity/commandline.py", line 1175, in ProcessCommandLine
    globals.backend = backend.get_backend(args[0])
  File "/usr/lib/python3/dist-packages/duplicity/backend.py", line 225, in get_backend
    obj = get_backend_object(url_string)
  File "/usr/lib/python3/dist-packages/duplicity/backend.py", line 211, in get_backend_object
    return factory(pu)
  File "/usr/lib/python3/dist-packages/duplicity/backends/giobackend.py", line 82, in __init__
    ensure_dbus()
  File "/usr/lib/python3/dist-packages/duplicity/backends/giobackend.py", line 37, in ensure_dbus
    output = p.communicate()[0].decode("utf8", errors="replace")
 AttributeError: 'str' object has no attribute 'decode'

Duplicity is the latest version? ```
duplicity is already the newest version (0.8.11.1612-1).
```

Any clues please?

---

### Post by doubletop12 on 2021-04-05
[SIZE=3][FONT=arial]Sorted, I think. It looks like it was a space issue on my system disk as /home/user/.cache/deja-dup and /home/user/.cache/duplicity had filled with files from aborted backups. It took a long time to find out what the problem was, not helped by a corrupted/truncated cache file that caused deja-dup to loop repeatedly asking for authentication every 10 mins or so. It also took a while to find a way to get debugging messages.

This works from the CLI and provides debug information
```


export DEJA_DUP_DEBUG=1
deja-dup --backup


```

**RESOLVED**[/FONT][/SIZE]

---

