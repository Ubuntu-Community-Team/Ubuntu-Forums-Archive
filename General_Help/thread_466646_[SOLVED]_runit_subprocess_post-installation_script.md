---
title: "[SOLVED] runit: subprocess post-installation script returned error"
date: 2007-06-06
forum: General Help
---

### Post by notwen on 2007-06-06
```
E: runit: subprocess post-installation script returned error exit status 1
```

Get this when trying to update and/or install anything new from terminal.  Any ideas? =]

---

### Post by notwen on 2007-06-07
*bump* 

this may or may not belong in the installation/upgrades forum, if so could a mod move it to the appropriate spot. tia =]

---

### Post by notwen on 2007-06-09
one last *bump*

---

### Post by notwen on 2007-06-09
Think I may have narrowed it down, what may have caused my /etc/inittab to be missing and how could I go about getting it back?  I haven't manually edited it ever, nor played in /etc recently.  Any help would be appreciated. Thanks

---

### Post by notwen on 2007-06-09
Just in case anyone else runs into this, [here]("https://bugs.launchpad.net/ubuntu/+source/runit/+bug/74135") is the bug at launchpad.

---

### Post by notwen on 2007-10-03
Had a request for what I did to get past this error.  Open a terminal and type in the following, this allows 'git-daemon-run' to be installed which depends on runit.

```
sudo touch /etc/inittab
```

---

### Post by eduardoeltortuga on 2007-12-28
Thanks for your solution! Been looking for a couple of weeks:)

---

