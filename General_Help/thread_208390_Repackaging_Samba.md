---
title: "Repackaging Samba"
date: 2006-07-03
forum: General Help
---

### Post by darkpixel on 2006-07-03
The Dapper Samba package doesn't include support for Posix ACLs.

I need to recompile the samba package with --with-acl-support.

I looked at the FAQ here ([http://www.ubuntuforums.org/showthread.php?t=101097](http://www.ubuntuforums.org/showthread.php?t=101097)) but I don't believe --with-acl-support is a CFLAG...

And if I do a ./configure --with-acl-support --and-whatever-else and then run dpkg-buildpackage -rfakeroot -uc -b it appears to re-run ./configure causing it to lose my --with-acl-support flag.

So my question is how to I add that flag in?

---

### Post by blackjack6.21.91 on 2006-07-03
You would probably have more luck just doing

./configure --parameters
make
sudo make install

It seems like fakeroot is giving you the problem
Peace,
blackjack

---

### Post by darkpixel on 2006-07-03
[QUOTE=blackjack6.21.91]You would probably have more luck just doing

./configure --parameters
make
sudo make install
[/QUOTE]

Yeah--but that would completely bypass the packaging system which would make it more difficult to upgrade or remove as needed.

---

