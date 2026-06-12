---
title: "Problem getting gnome baker"
date: 2005-04-27
forum: General Help
---

### Post by Jujimufu on 2005-04-27
I can't download gnome baker from synaptic because I need vorbis-tools.  So I try sudo apt-get vorbis tools and I get this error:

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

I installed the extra repositories, but I was having problems with this line:

gpg --armor --export 1F41B907 | sudo apt-key add -

I typed it in and it just wasn't working right.  Maybe there's something else I'm not understanding, but if someone could help it be really nice.   Thanks!

---

### Post by Jujimufu on 2005-04-27
Nevermind I got it working.  I just had to shutdown synaptic.

---

