---
title: "[SOLVED] Broken symbolic links in python"
date: 2008-03-12
forum: General Help
---

### Post by dmitrijledkov on 2008-03-12
After I upgraded to alpha Hardy and installed random packages and did probably something else (can't remember). Python dependent packages no longer could find.
```
/var/lib/python-support/python2.5/bootconfig/__init__.py
```

When I looked into that directory I realised that the following files
```
grub_legacy.py  __init__.py  threads.py  utils.py
grub.py         splashy.py   usplash.py

```
were broken symbolic links.

I reinstalled everything with python in the name, but those symbolic links are still broken.

I know that Hardy is alpha, but resolution to this does not seem to be hardy dependent. Can anyone please help.

ps I posted this on the hardy development forum as well but it has little views and no replies so I thought this issue might be resolved here. Thanks.

---

### Post by dmitrijledkov on 2008-03-12
Does this help? Anyone?

```
Setting up guidance-backends (0.8.0svn20080103-0ubuntu4) ...
Compiling /var/lib/python-support/python2.5/bootconfig/__init__.py ...
Sorry: TypeError: ('compile() expected string without null bytes',)
```

and

```
Setting up python-libxml2 (2.6.31.dfsg-2ubuntu1) ...
Compiling /var/lib/python-support/python2.5/bootconfig/__init__.py ...
Sorry: TypeError: ('compile() expected string without null bytes',)
```

and

```
Setting up guidance-backends (0.8.0svn20080103-0ubuntu4) ...
Compiling /var/lib/python-support/python2.5/bootconfig/__init__.py ...
Sorry: TypeError: ('compile() expected string without null bytes',)
```

Could anyone please look on their installation what does that file look like or where is it pointing to. Please.

---

### Post by dmitrijledkov on 2008-03-12
[https://bugs.launchpad.net/ubuntu/+source/python-support/+bug/174206]("https://bugs.launchpad.net/ubuntu/+source/python-support/+bug/174206")

Launchpad bug file and fix in the comment.

---

