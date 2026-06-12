---
title: "Problem installing Gnucash"
date: 2005-06-12
forum: General Help
---

### Post by adamthompson on 2005-06-12
I have been unable to install Gnucash in Ubuntu Linux. I've tried Synaptic, Apt in the terminal, and compiling the source.

Here's what I get in Apt:

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/i/imlib+png2/gdk-imlib1_1.9.14-16.2ubuntu2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/i/imlib+png2/gdk-imlib1_1.9.14-16.2ubuntu2_i386.deb)  MD5Sum mismatch
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/o/oaf/oaf_0.6.10-3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/o/oaf/oaf_0.6.10-3_i386.deb)  MD5Sum mismatch
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/libg/libghttp/libghttp1_1.0.9-15_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/libg/libghttp/libghttp1_1.0.9-15_i386.deb)  MD5Sum mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

I have Universe enabled. I tried running apt-get update, and I got exactly the same error messages.

Gnucash is a must-have application for me. I'll have to go back to Fedora if I can't get it to work on Ubuntu.

---

### Post by TorQ on 2005-06-12
I just ran into this problem today as well!!  I tried to install Grisbi instead and got the same errors.  I agree,  this is a big one.  Any help would be GREATLY appreciated!

---

### Post by kleeman on 2005-06-12
Sounds like some kind of mirror problem (MD5Sum mismatch). Try again tomorrow or switch apt mirrors.

---

### Post by Xian on 2005-06-12
Read in [THIS](http://www.ubuntuforums.org/showthread.php?p=210241#post210241) thread.

---

### Post by adamthompson on 2005-06-12
:) That worked. Thanks.

---

### Post by TorQ on 2005-06-13
Yes! Fixed!  My only remaining question is do I want to leave my repository list as what I changed it to?  Thanks again.

---

