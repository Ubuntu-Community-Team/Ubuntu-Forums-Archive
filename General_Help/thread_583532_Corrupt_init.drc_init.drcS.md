---
title: "Corrupt init.d/rc init.d/rcS"
date: 2007-10-20
forum: General Help
---

### Post by erkokite on 2007-10-20
I was using Kubuntu Feisty, and was in the process of upgrading to Gutsy.  During the package configuration phase, I was prompted to configure PAM, upon doing this, my machine crashed.  I tried to restart, but found that both etc/init.d/rc and etc/init.d/rcS had been corrupted (they have both turned into garbage).  I can only boot into recovery mode, and then only with a read only fs.

I should be able to fix the read only problem with mount -o remount,rw /dev/

Once I do this, I am wondering how to fix the corrupt init.d.  Anyone have a sample init.d/rc and rcS that I can use?  Could I simply delete the contents of these files and let them repair themselves?

Another thing that I might try is dpkg --reconfigure -a, as this should pick up the upgrade process where it left off and may repair the files.

Thoughts?

---

