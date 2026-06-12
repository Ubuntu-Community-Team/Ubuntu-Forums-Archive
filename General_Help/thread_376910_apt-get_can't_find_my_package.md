---
title: "apt-get can't find my package"
date: 2007-03-05
forum: General Help
---

### Post by letheology on 2007-03-05
Hi.  Brand new to Ubuntu, came from Gentoo.

I'm trying to install a package, libpam-pwdfile.  apt-get doesn't find the package, nor can I see it listed if I use dselect.  However, the package does seem to be in the Ubuntu source tree ([see](http://packages.ubuntu.com/edgy/admin/libpam-pwdfile)).  So how do I install it?  Why doesn't my apt-get find it?

I'm trying things like $sudo apt-get install libpam-pwdfile.

Thanks in advance.

---

### Post by Ramses de Norre on 2007-03-05
It's in the universe repo which isn't enabled by default, so edit /etc/apt/sources.list and remove the comments from the lines for universe.

---

### Post by Erik Trybom on 2007-03-05
That's right. And don't forget:

1) You have to be root to change sources.list (use sudo).
2) "sudo apt-get update" after you've saved the file. 

Then try again and it should work!

---

### Post by letheology on 2007-03-05
Thanks guys!  That worked for me, with one proviso: I had to do an apt-get update first.

Thanks again!

---

