---
title: "synaptic uninstall"
date: 2004-11-07
forum: General Help
---

### Post by zyang on 2004-11-07
i was playing with synaptic and installed kde with 30 some dependencies. now im trying to uninstall it, but it apears that the "kde" stub i used during installation doesnt remove the dependency packages, even when i selected for complete removal (i orinally assumed thats for removing dependencies). so how do i remove a package along with all its dependencies?

<newbie>zee</newbie>

---

### Post by az on 2004-11-07
Everything in KDE used to depend on arts and kdelibs

Remove arts and kdelibs4 and that should do it...



Answer back if it works, since this is based on kde from about six months ago...

---

### Post by jdong on 2004-11-08
use apt-cache depends <package> to list all dependencies. In this case:

```

jdong@jd64:~ $ apt-cache depends kde
kde
  Depends: kde-core
  Depends: kde-amusements
  Depends: kdeaddons
  Depends: kdeadmin
  Depends: kdeartwork
  Depends: kdegraphics
  Depends: kdemultimedia
  Depends: kdenetwork
  Depends: kdepim
  Depends: kdeutils
  Depends: quanta

```

This doesn't look that hard to remove. You may have to apt-cache depend subpackages (I think kdemultimedia , like kde, may be a virtual package!)

---

### Post by zyang on 2004-11-08
thanks for all the help guys. what happend was after i marked the packages jdong showed me, it only accounts for about 40mbs, i distinctly remember the kde stub installed around 300-400 mb of junk into my hard drive. i did a search in synaptic and marked all the packages that has anything to do with kde, and that freed up 344 mb.

im fairly new to linux, and im just curious if its always this messy to uninstall stuff, or is kde just a special case since ubuntu doesnt support it.

---

### Post by liberal_tugboat on 2004-11-10
unintalling kde is like uninstalling Explorer, Internet explorer, outlook express, word pad, note pad, media player, movie maker (yuk), messenger.... blah blah blah... from windows XP. You arent just getting rid of one program yours dumping most of the features of the operating system.

---

### Post by fng on 2004-11-10
At least you can uninstall all those "feautures" in linux :)

Try deleting explorer in winxp.

---

