---
title: "bitchx irc client"
date: 2008-06-29
forum: General Help
---

### Post by utab on 2008-06-29
Dear all,

How can I install bitchx?

I uncommented universe and multiuniverse in sources.list but it did not work however it is finding software pork which I am not sure if related to the bithcx.

apt-cache search bitchx
pork - Console-based AOL Instant Messenger & IRC client

Regards,

---

### Post by manfer on 2008-06-29
prompt:~$ apt-cache show pork

Package: pork
Priority: optional
Section: universe/net
Installed-Size: 1608
Maintainer: Benjamin Seidenberg <astronut@dlgeek.net>
Architecture: i386
Version: 0.99.8.1-1
Depends: libc6 (>= 2.4-1), libncurses5 (>= 5.4-5), libperl5.8 (>= 5.8.7)
Filename: pool/universe/p/pork/pork_0.99.8.1-1_i386.deb
Size: 248076
MD5sum: 58d469ae3e828b5e06391b7e877de074
SHA1: 2b1e4f1397496ae1c88acd1344dfb7ac501c104f
SHA256: 07e621f34909d1776f4b75d9029c59158f92c52c663ec30ffeaf9f8df36e571a
Description: Console-based AOL Instant Messenger & IRC client
 pork is an ncurses-based AOL Instant Messenger and IRC client. It uses the
 OSCAR protocol (the one the windows client uses) to access AIM. Pork
 features Perl scripting; an online help system; the ability to
 configure nearly all aspects of the program's look-and-feel; an alias
 system; and a powerful, fully-configurable key binding system. It
 supports being logged in with more than one screen name at the same
 time. The default look-and-feel of the client is modeled after the
 ircII IRC client. Anyone comfortable using ircII (or any clients
 derived from it -- e.g., epic, BitchX, etc.) will feel comfortable
 using pork.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

As you can see no, pork is not bitchx. Only mentions bitchx in its description and that is why apt-cache search finds it.

I think bitchx is not in hardy repositories.

---

### Post by x1a4 on 2008-06-29
Hi,

Did you update the package lists?
```
sudo apt-get update
```

EDIT: manfer is right, it's not in the hardy repos.  Visit [bitchx.org/]("http://www.bitchx.org/") to download.

---

