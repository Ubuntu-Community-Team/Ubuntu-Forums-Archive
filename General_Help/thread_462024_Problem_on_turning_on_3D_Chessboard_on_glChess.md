---
title: "Problem on turning on 3D Chessboard on glChess"
date: 2007-06-02
forum: General Help
---

### Post by tL0z on 2007-06-02
Hello,

I am following [this]("http://www.mikesplanet.net/2007/03/turning-on-3d-chessboard-in-feisty/") tutorial in order to turn on 3D Chessboard on glChess. However, I since I have a AMD64 CPU, I downloaded [this]("http://ftp.uk.debian.org/debian/pool/main/p/python-gtkglext1/python-gtkglext1_1.1.0-3_amd64.deb") package on step 3. The problem occurred when I tried to install it. I had the following error:

```
Selecting previously deselected package python-gtkglext1.
(Reading database ... 113600 files and directories currently installed.)
Unpacking python-gtkglext1 (from python-gtkglext1_1.1.0-3_amd64.deb) ...
dpkg: dependency problems prevent configuration of python-gtkglext1:
 python-gtkglext1 depends on libc6 (>= 2.5-5); however:
  Version of libc6 on system is 2.5-0ubuntu14.
 python-gtkglext1 depends on libpango1.0-0 (>= 1.16.4); however:
  Version of libpango1.0-0 on system is 1.16.2-0ubuntu1.
dpkg: error processing python-gtkglext1 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python-gtkglext1

```

What am I supposed to do to solve this? 

Thanks!

---

### Post by Lord Illidan on 2007-06-02
Personally, I'd leave it alone if I were you. You are not missing anything believe me.

Here is a screenshot. And you can't rotate, see the board from a different angle or anything..it's a waste of time if you ask me...not to mention that it eats CPU, and is not anti-aliased.

---

### Post by tL0z on 2007-06-02
As a matter of fact, I don't need it to be 3D. I only wanted the library to be correctly installed because other programs may need it... or not?

---

