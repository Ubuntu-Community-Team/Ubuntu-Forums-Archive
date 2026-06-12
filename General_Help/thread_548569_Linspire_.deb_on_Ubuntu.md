---
title: "Linspire .deb on Ubuntu?"
date: 2007-09-11
forum: General Help
---

### Post by Corfy on 2007-09-11
From a package standpoint, how close is Ubuntu and Linspire?

I have a friend that has picked up a used computer without an OS and he wants to try Linux on it as a second computer at his house (he only has one computer, and he needs it for work at home, his wife needs it for work at home, and his son needs it for homework and games). Being a K/Ubuntu user, that is what I want to put on his computer (and since he knows he will probably be coming to me with any help and he knows that is what I use, that is what he wants as well).

However, he still has dialup internet access, and he uses NetZero. NetZero does have software for Linux available for download, but they specify that it is for Linspire. It is a .deb file, which I know how to install, but I wondered if that would work on the K/Ubuntu system, or if there is something special I need to do to make it work, or if we are simply out of luck.

The system will be set up at my house using my broadband internet, so I can get all the packages he needs/wants installed that way, so that isn't an issue. But I was concerned about him getting Internet access after that. He is talking about probably moving to DSL "soon", but that may still be months away.

---

### Post by dabl on 2007-09-11
> **Corfy said:**
> From a package standpoint, how close is Ubuntu and Linspire?

 It is a .deb file, which I know how to install

AFAIK, all .debs are created equal, in terms of *buntu's ability to install them.  If there's a problem, then it must not have been "truly Debian".  :)

---

### Post by Corfy on 2007-09-11
> **dabl said:**
> AFAIK, all .debs are created equal, in terms of *buntu's ability to install them.  If there's a problem, then it must not have been "truly Debian".  :)

Actually, they aren't, or so I have heard. I have heard repeated complaints over the last couple of years from the Debian crowd about how Ubuntu has "forked" so far out from Debian that Ubuntu  packages are incompatible with Debian's packages. Granted, not being a package builder myself, I have no idea why they wouldn't be compatible, but that doesn't mean anything.

---

### Post by fragos on 2007-09-11
Linspire was notorious for having their own versions of libraries that created all kinds of depedency problems.  It's true that some deb packages intended for other than Ubuntu don't work correctly.  I suggest you try installing.  If dependency issues for Linspire libraries appear the install will fail and nothing lost.  If it installs and doesn't work, you can uninstall it.

---

### Post by az on 2007-09-11
Even debian is not binary-compatible with itself.  You cannot install a deb made for one version of Debian and expect it to work on another.

No debian-based linux distribution is binary-compatible.  GNU/linux in general is compatible only on the source code level, never the binary level.

This is an important feature for development as well as a security feature.  Being source-based helps make development easier.

---

