---
title: "Can't start Google Chrome"
date: 2013-04-16
forum: General Help
---

### Post by Hungry Man on 2013-04-16
If I try to run 'google-chrome' from CLI I get an error:

/opt/google/chrome/chrome: error while loading shared libraries: libudev.so.0: cannot open shared object file: No such file or directory

Strange, as I ran it after install. But after a reboot it will no longer open.

---

### Post by Hungry Man on 2013-04-16
I have no 'libudev' in Ubuntu /usr/lib at all... could someone simply upload theirs?

[http://pkgs.org/centos-6-rhel-6/centos-rhel-x86_64/libudev-147-2.46.el6.x86_64.rpm/download/](http://pkgs.org/centos-6-rhel-6/centos-rhel-x86_64/libudev-147-2.46.el6.x86_64.rpm/download/)

Got it here... works for now.

---

### Post by defaria on 2013-05-07
That didn't work for me as that's and RPM and for Redhat not Ubuntu. I tried downloading the source and compiling but hit all kinds of problems. I ended doing the following:

$ sudo ln /lib/x86_64-linux-gnu/libudev.so.1 /usr/lib/x86_64-linux-gnu/libudev.so.0

Strange (and I don't like it)

---

### Post by z_diver on 2013-06-14
OK... kinda worked but couple o things:
first, I run a i386 install on my 64 bit machine as many do
and second, /usr was inappropriate on this platform. I needed to use "sudo ln /lib/i386-linux-gnu/libudev.so.1 /lib/i386-linux-gnu/libudev.so.0"

---

### Post by z_diver on 2013-06-14
I should also note that you will need to have libudev-dev installed for this to work.

---

