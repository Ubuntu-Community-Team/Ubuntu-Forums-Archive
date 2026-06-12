---
title: "How to symlink..?"
date: 2004-11-04
forum: General Help
---

### Post by Verlager on 2004-11-04
[B]tar -xzf thunderbird-0.9-i686-linux-gtk2+xft.tar.gz
mv thunderbird /usr/local/bin [/B]

Now I need to create a symlink within the user path that refers to the executable (thunderbird) which is in the /usr/local/bin/thunderbird directory.

**sudo ln -s /usr/local/bin/thunderbird/thunderbird /usr/local/bin/tbird**

verlager@ubuntu:~ $** tbird**
[COLOR=DarkRed]**bash: tbird: command not found**[/COLOR] [SIZE=3]**<---- Why not?**[/SIZE]

verlager@ubuntu:~ $** $PATH**
[COLOR=DarkRed]**bash: /usr/local/bin:/usr/local/sbin:/sbin:/usr/sbin:/bin:/usr/bin:/usr/bin/X11:/usr/games: No such file or directory**[/COLOR]
verlager@ubuntu:~ $

---

### Post by triad169 on 2004-11-04
Looks like /usr/local/bin has a group permission of "staff"  are you part of that group?

Triad

---

