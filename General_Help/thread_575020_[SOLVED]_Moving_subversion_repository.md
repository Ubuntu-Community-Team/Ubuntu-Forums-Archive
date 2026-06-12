---
title: "[SOLVED] Moving subversion repository"
date: 2007-10-13
forum: General Help
---

### Post by starfry on 2007-10-13
Hi, I'm low on disk space on the partition housing mu subversion repository /srv/svn .

Can I just move this to another disk using cp -r and then put a symlink in place ?

Something like

cp -r /srv/svn /new/volume
ln -s /new/volume /srv/svn

Will it all still work after I do this?

Thanks!

---

### Post by starfry on 2007-10-14
Well, I went ahead and did it and all is well, so I guess that means it works ok :)

---

