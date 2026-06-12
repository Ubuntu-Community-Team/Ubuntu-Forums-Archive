---
title: "Kernel-package MD5 Error"
date: 2005-07-08
forum: General Help
---

### Post by Akita on 2005-07-08
Newb to Ubuntu (lots of time on Debian) here. Not sure where the best place is to report this so...

[http://us.archive.ubuntu.com/ubuntu/pool/main/d/dpkg/dpkg-dev_1.10.27ubuntu1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/d/dpkg/dpkg-dev_1.10.27ubuntu1_all.deb)  MD5Sum mismatch

---

### Post by kc1di on 2005-07-08
must report it's very fustrating i've been trying in both synaptic and apt-get to install kde and I'm getting a ton of MD5Sum errors also.  anyone have any clue to what's wrong?

dave

---

### Post by acascianelli on 2005-07-08
I had a similar problem installing other packages.  I can't find the thread I read it in but I saw that somebody suggested editing the /etc/apt/sources.list file and removing all the "us." from all the repositories, so that they would look like "http://archive."  That worked for me and I no longer get the MD5 mismatch error.

---

### Post by Akita on 2005-07-08
Removing the ".us" worked like a charm - Thank You! 

OTOH it's still breakage that wasn't there a couple of days ago...

---

