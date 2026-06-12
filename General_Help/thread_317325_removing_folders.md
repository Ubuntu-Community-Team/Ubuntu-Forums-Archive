---
title: "removing folders"
date: 2006-12-12
forum: General Help
---

### Post by Gargamella on 2006-12-12
is it possible to remove a directory with all files inside, without doing it one by one?

thanks

Andrea

---

### Post by meng on 2006-12-12
Yes.
rm -r [dirname]

---

### Post by Gargamella on 2006-12-12
thank you ;D , i didn't know it

another question... if I installed a software not by .deb, but by source,
Can I remove it in this way? (rm -r dirname)

---

### Post by meng on 2006-12-12
The best way to uninstall from source is to go to the source directory and:
make uninstall
(maybe you need to sudo make uninstall)

However, not all source packages have this option enabled. No harm trying though.

---

### Post by Gargamella on 2006-12-12
I'm talking about quake 3 arena and Enemy territory...they don't work on my Dapper (intel drivers...damned!)


anyway i went to /usr/local/games/   and there are quake and et directories... but there doesn't work "sudo make uninstall"

it answers me with

make: *** No rule to make target `uninstall'. Stop.

---

### Post by bodhi.zazen on 2006-12-12
> **Gargamella said:**
> thank you ;D , i didn't know it

another question... if I installed a software not by .deb, but by source,
Can I remove it in this way? (rm -r dirname)

Take a look at checkinstall. It makes a deb package of those source installations. It sometimes fails, but if it works it is easier to maintain....

[checkinstall](https://help.ubuntu.com/community/CheckInstall)

---

### Post by reclusivemonkey on 2006-12-12
> **Gargamella said:**
> I'm talking about quake 3 arena and Enemy territory...they don't work on my Dapper (intel drivers...damned!)


anyway i went to /usr/local/games/   and there are quake and et directories... but there doesn't work "sudo make uninstall"

it answers me with

make: *** No rule to make target `uninstall'. Stop.

Usually games are installed purely in their own directories, so yes, with rm -Rf *dirname* it should uninstall everything for you.

---

