---
title: "Peer Guardian Linux - Ubuntu 14.04 install"
date: 2014-05-15
forum: General Help
---

### Post by DOS286 on 2014-05-15
I'm having some trouble installing PGL on Ubuntu 14.04. I used the PPA, but the last step gives this error:

```
find: `/home/*/.config/pgl/': No such file or directory
```

Has anyone seen this, or know a solution?

---

### Post by jre on 2014-05-20
What exactly is your last step?
What did you do so far?
Please post the output of ```
dpkg -l "pgl*"
```

btw, currently a frequently reproted problem while installing pgl is that iblocklist.com removed the list atma_atma. So in order to complete the installation edit /etc/pgl/blocklists.list and remove the corresponding list.
EDIT: I contacted iblocklist and the atma list is now available again. So there is no need to remove it any more if you choose to use this list.

---

