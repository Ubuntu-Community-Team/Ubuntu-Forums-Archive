---
title: "Sonata crash"
date: 2008-05-28
forum: General Help
---

### Post by gnav on 2008-05-28
Hello :)

Yesterday Sonata stopped working on my Ubuntu 8.04. It just crashed and now it won't start. When I try to start it in the terminal, this comes up:

```
Traceback (most recent call last):
  File "/usr/bin/sonata", line 47, in <module>
    app = sonata.Base()
  File "/usr/lib/python2.5/site-packages/sonata.py", line 1148, in __init__
    self.iterate_now()
  File "/usr/lib/python2.5/site-packages/sonata.py", line 1771, in iterate_now
    self.iterate()
  File "/usr/lib/python2.5/site-packages/sonata.py", line 1728, in iterate
    self.handle_change_status()
  File "/usr/lib/python2.5/site-packages/sonata.py", line 3415, in handle_change_status
    self.browse(root=self.wd)
  File "/usr/lib/python2.5/site-packages/sonata.py", line 2512, in browse
    bd += [('f' + lower_no_the(song.title), ['sonata', song.file, self.parse_formatting(self.libraryformat, song, True)])]
  File "/usr/lib/python2.5/site-packages/mpdclient3.py", line 311, in __getattr__
    raise AttributeError
AttributeError
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/apport_python_hook.py", line 78, in apport_excepthook
    report_file = open(pr_filename, 'wt')
IOError: [Errno 13] Permission denied: '/var/crash/_usr_bin_sonata.1000.crash'

Original exception was:
Traceback (most recent call last):
  File "/usr/bin/sonata", line 47, in <module>
    app = sonata.Base()
  File "/usr/lib/python2.5/site-packages/sonata.py", line 1148, in __init__
    self.iterate_now()
  File "/usr/lib/python2.5/site-packages/sonata.py", line 1771, in iterate_now
    self.iterate()
  File "/usr/lib/python2.5/site-packages/sonata.py", line 1728, in iterate
    self.handle_change_status()
  File "/usr/lib/python2.5/site-packages/sonata.py", line 3415, in handle_change_status
    self.browse(root=self.wd)
  File "/usr/lib/python2.5/site-packages/sonata.py", line 2512, in browse
    bd += [('f' + lower_no_the(song.title), ['sonata', song.file, self.parse_formatting(self.libraryformat, song, True)])]
  File "/usr/lib/python2.5/site-packages/mpdclient3.py", line 311, in __getattr__
    raise AttributeError
AttributeError

```

Got any idea that may fix it?

Thanks in advance :)

---

### Post by pointone on 2008-05-28
Try:

```
sudo apt-get install sonata --reinstall
```

---

### Post by gnav on 2008-05-28
I've tried that, and it doesn't seem to fix it.

---

### Post by gnav on 2008-05-29
Bumpedibump :)

---

### Post by gnav on 2008-05-30
Still haven't fixed it, so here comes another bump.

---

### Post by pointone on 2008-05-30
```
IOError: [Errno 13] Permission denied: '/var/crash/_usr_bin_sonata.1000.crash'
```

It seems like it's encountering an error that may or may not be recoverable, but then when it tries to log the error, it's hitting a truly unrecoverable error.

You could try the following:

```
sudo touch /var/crash/_usr_bin_sonata.1000.crash
sudo chmod 777 /var/crash/_usr_bin_sonata.1000.crash
```

...and try running the program again. Otherwise, I'm stumped.

---

### Post by gnav on 2008-05-30
It didn't help, but thanks anyway. :smile:

---

