---
title: "where to report issues with packages distributed in Ubuntu ?"
date: 2014-06-21
forum: General Help
---

### Post by Nosphky on 2014-06-21
I have issues with a couple of packages provided with both Ubuntu Desktop and UbuntuStudio.  I have gone as far as I can with both of them and have raised queries on their own forums.  In one case getting no suggestions and in the other case suggesting a problem with the package supplied in Ubuntu.I suppose that for each software provided in the different Ubuntu distributions, there is someone responsible or connected with preparing it for release ?  I have in each case some supporting notes I can provide.  Where is the correct place to report these issues ?Thanks.

---

### Post by LastDino on 2014-06-21
[https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu)

Do tell what packages we are talking about.

---

### Post by oldos2er on 2014-06-21
```
ubuntu-bug <package>
```

---

### Post by Nosphky on 2014-06-21
@ LastDino :  I have a problem with KeePass2 on both Desktop 14.04 and Studio and also on gnupg2 on Studio.

@ oldos2er :  (I also used os2 way back - it must have been end of the 80's or early 90's ?)  I tried the code snippet you suggested but it just collects data from my machine.  This info can certainly be forwarded to wherever but how does that describe the problem and tell how to reproduce it ?

In the case of gnupg2, it just says that it's not installed - and that's because I had to remove it to get thunderbird to encrypt my mail.

Can you explain a bit more how and where I send a description ?

---

### Post by Nosphky on 2014-06-21
I just checked the launchpad link that LastDino posted.  I think that my KeePass problem has found its way there as a new bug.  I hadn't understood that launchpad was connected to Ubuntu.  I'll try and add some remarks to that bug.

---

### Post by oldos2er on 2014-06-21
ubuntu-bug should offer to send its information to the developers for you. *apport-bug* can also be used too.

---

### Post by Nosphky on 2014-06-21
Thank you both - I've plundered the launchpad pages and succeeded in getting both issues done.

---

