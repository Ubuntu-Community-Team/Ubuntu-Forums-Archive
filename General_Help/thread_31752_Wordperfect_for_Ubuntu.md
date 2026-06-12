---
title: "Wordperfect for Ubuntu ?"
date: 2005-05-04
forum: General Help
---

### Post by freelsjd on 2005-05-04
Apparently, the new release of Libranet to version 3.0 also retains compatibility of Wordperfect 8.1 (according to Linux Journal).  The previous version of Libranet also retained this compatibility. Has anyone figured out how to do this with Hoary Unbuntu ?  Since all are Debian-based (Ubuntu, Libranet, Wordperfect), it seems that it should be possible if the right run-time libraries are determined and some type of configuration script, etc. ?

---

### Post by ct_srvnt on 2005-06-05
Check out the advice at [www.linux-sxs.org](www.linux-sxs.org).  Check on Utilities: There will be a link to Wordperfect.  Look for the instructions for installing wordperfect on Debian systems.  There is also a Wordperfect on Linux FAQ at [www.linuxmafia.com/wpfaq](www.linuxmafia.com/wpfaq).  
Once you've installed the needed libraries, you'll still need to get around the Ubuntu automount permissions weirdness for ./install to work.  See my comment in the other "wordperfect" thread for details -- Basically, you have to unmount the CD as root (sudo), then remount with exec privileges as root (sudo), both in a terminal, before invoking  the,/ install script as root (sudo) from the /media/cdrom dir.
Warning: I've seen warnings that installing multiple versions of libraries can lead to system instability.  I know nothing personally about this issue.  I used this fix on a couple of systems (but not Ubuntu) without any such problems, but others would know better than I would.

---

### Post by nashjc on 2006-10-09
Has anyone managed a usefully working WP8 on Dapper?

I've made a couple of attempts, but the install script seems be have a lot of trouble finding things. I suspect a whole load of ownership and permission issues, as well as library locations, though I did manage to do everything that the WP FAQ suggested.

JN

---

