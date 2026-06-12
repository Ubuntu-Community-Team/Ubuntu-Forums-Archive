---
title: "I accidentally ran CHOWN on half my hard drive. What now?"
date: 2017-07-26
forum: General Help
---

### Post by matthewtexas76 on 2017-07-26
I just accidentally ran chmod -R myuser.myuser * on my root drive.  bin, boot, cdrom, dev, and etc were affected before I hit CTRL+C. 

Should I change all of these back to root, or are there other owners for some of the files in these? I'm especially concerned about "dev".

---

### Post by oldos2er on 2017-07-26
Was it chown or chmod?

---

### Post by HermanAB on 2017-07-26
Were you logged in as root?

If you were not root, then nothing untoward would have happened.

If you were root, then you could run chown root: -R * on each system directory to set it back.

Don't worry about /sys, /proc and /dev - those are not real file directories and will be 'recreated' on reboot.

---

### Post by Impavidus on 2017-07-27
There are many files in /etc with a different group than root. Fixing them one by one is almost impossible.

---

### Post by Habitual on 2017-07-27
re-install.
Chaik it up to experience, is my best advice.

---

### Post by QIII on 2017-07-27
Unfortunately, it is not necessarily always the case that system files/directories are owned by root.  There are a number of "system" users with ownership of some directories, such as /var/www.  (This is probably not problematic if you aren't running a web server, but it is an example.)

Wholesale or random modification of ownership/permissions is one of those very, very few instances where I think  blasting off and nuking from orbit is the only viable option.  But be sure to back up any important data prior to doing so.

---

