---
title: "Howto verify installed files ?"
date: 2006-11-07
forum: General Help
---

### Post by the-linux-guy on 2006-11-07
Hi,

I want to verify all my installed files against all installed deb packages, just like the "rpm -Va" command in rpm-based distros. I played around with dpkg -l and dpkg -L commands, showing me all a) installed packages and b) all files belonging to a certain package, but how do I put these 2 commands together and pipe the result to the find command to check if all files are there (where they suppose to be) ???

I'm not a cli-guru, but I'm sure somebody here is willing to give me a hand ?

Thanks in advance !

---

### Post by the-linux-guy on 2006-11-08
Bump... :rolleyes: Isn't there anybody who can help me with this ?

---

### Post by SirYes on 2008-05-06
How about this:
[Debian Reference - Debian package management](http://www.debian.org/doc/manuals/reference/ch-package.en.html)

See part titled "6.4.14 Verify installed package files".

(that's for start)

---

