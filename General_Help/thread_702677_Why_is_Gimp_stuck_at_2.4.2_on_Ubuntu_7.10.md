---
title: "Why is Gimp stuck at 2.4.2 on Ubuntu 7.10?"
date: 2008-02-20
forum: General Help
---

### Post by crosswalker21 on 2008-02-20
Hi everybody!

I'm fairly new (though persistent) to Ubuntu, so if this is painfully obvious to the more experienced users, don't yell, a hardy smack on the head will do just fine ;)

First problem: I have Gimp installed at version 2.4.2 (installed it through add/remove).  I know from gimp.org that the current stable version is 2.4.5, but nothing shows up in system update or in add/remove.  Is there any particular reason?

Second problem: I've noticed when I try to install packages (via. synaptic or add/remove, but apparently not through apt-get install), I sporadically get a "items couldn't be authenticated" error.  I click through it (I'm installing known packages) but I'm assuming this isn't as it should be.  Any suggestions?  Reinstalling is an option, but I'd rather not at this point in the process.

I'm not sure if these problems are in any way related, but it seemed they might be, so I put them in one post.

Any help would be greatly appreciated!

---

### Post by apastuszak on 2008-02-20
The version number of most packages are frozen in Ubuntu.  You won't see 2.4.5 until Hardy Heron comes out, or it's backported and made available in the backports repository.

Andy

---

### Post by habtool on 2008-02-20
Above reply is correct.
Ubuntu versions, like Gutsy 7.10, only get bug fixes and security updates.
No new program versions until each new release of Ubuntu, like 8.04 in this case.

The other method is whats called a rolling release distro , like Arch Linux.
Arch is however a lot more hands on and takes more time and knowledge/research to setup correctly.

---

### Post by disturbedite on 2008-02-20
you can ask for a backport of the lastest version though...

---

### Post by crosswalker21 on 2008-02-20
Wow, that was fast.  Thanks!

---

### Post by Irony on 2008-02-20
Go here to download 2.4.4 for Gutsy;

[http://www.getdeb.net/release.php?id=2055](http://www.getdeb.net/release.php?id=2055)

---

