---
title: "[SOLVED] Installin awn"
date: 2008-07-01
forum: General Help
---

### Post by daggerx on 2008-07-01
trying to install awn and when I do here is what i get:

```
Install these packages without verification [y/N]? y
Selecting previously deselected package libawn0-bzr.
(Reading database ... 135515 files and directories currently installed.)
Unpacking libawn0-bzr (from .../libawn0-bzr_0.3.1.bzr302.1~hardy_i386.deb) ...
Unpacking avant-window-navigator-bzr (from .../avant-window-navigator-bzr_0.3.1.bzr302.1~hardy_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/avant-window-navigator-bzr_0.3.1.bzr302.1~hardy_i386.deb (--unpack):
 trying to overwrite `/usr/share/avant-window-navigator/avant-window-navigator-24.png', which is also in package avant-window-navigator-data
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Selecting previously deselected package awn-core-applets-bzr.
Unpacking awn-core-applets-bzr (from .../awn-core-applets-bzr_0.3.1.bzr591.1~hardy_i386.deb) ...
Selecting previously deselected package python-awn-bzr.
Unpacking python-awn-bzr (from .../python-awn-bzr_0.3.1.bzr302.1~hardy_i386.deb) ...
Selecting previously deselected package awn-manager-bzr.
Unpacking awn-manager-bzr (from .../awn-manager-bzr_0.3.1.bzr302.1~hardy_i386.deb) ...
[B]Errors were encountered while processing:
 /var/cache/apt/archives/avant-window-navigator-bzr_0.3.1.bzr302.1~hardy_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code[/B] (1)

```

please advise and thanks in advance.

---

### Post by rainwalker on 2008-07-01
I'm pretty sure AWN is in the repos now

---

### Post by daggerx on 2008-07-01
Ok, can someone give me a little bit more data than rainwalker? thanks in advance.


edit: I guess it was enough info, I installed it via synaptic but now im looking for the "start auto with ubuntu" check box

---

### Post by Tomatz on 2008-07-01
> **daggerx said:**
> Ok, can someone give me a little bit more data than rainwalker? thanks in advance.

Open synaptic package manager and search for it there

---

### Post by rainwalker on 2008-07-01
> **daggerx said:**
> Ok, can someone give me a little bit more data than rainwalker? thanks in advance.


edit: I guess it was enough info, I installed it via synaptic but now im looking for the "start auto with ubuntu" check box

Add ```
avant-window-navigator
``` to your startup programs in System > Preferences > Sessions

---

### Post by daggerx on 2008-07-02
Thanks :popcorn:
This is solved...

---

### Post by rainwalker on 2008-07-02
> **daggerx said:**
> Thanks :popcorn:
This is solved...

Up at the top of the thread, click "Thread Tools" and choose "Mark as solved" :)

---

### Post by daggerx on 2008-07-02
Thanks rainwalker

---

### Post by rainwalker on 2008-07-02
No problem :)
Have fun with AWN!

---

