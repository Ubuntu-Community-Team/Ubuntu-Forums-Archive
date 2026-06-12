---
title: "no GUI for a session"
date: 2006-08-18
forum: General Help
---

### Post by Kaspertje on 2006-08-18
I'm new working with Ubuntu 5.10 Breezy Badger.
I've tried to install some software for home
banking. After installation my system boots normally but I don't get the GUI for the login session any more. After booting the screen is black and the following message appears:

UBUNTU 5.10 "Breezy Badger" kasper tty1
Kasper login:

I'm able to introduce my password and get redirected to /home in a terminal mode.
I can list and introduce commands.

After logging out the following error messages appear:

amixer: error when loading shared libaries
libasound.so.2 cannot open shared object file: no such file found

and

user/bin/filelist_order libstdc++.so.6
no such file or directory

I would be most greatful if somebody could help resolving this problem.

Respectfully,

Kasper
Forward Message

---

### Post by TripleE on 2006-08-18
[I]It looks like a:
```
[/I]*sudo apt-get install libasound2 *[I]libstdc++6

```
will resolve your issue.
[/I]

---

### Post by Kaspertje on 2006-08-19
Thanks, but that didn't help. I get the following error message:

apt-get: error while loading shared libraries: libapt-pkg-libc6.3-6.so.3.10:
Can not open shared object file: no such file or directory

---

