---
title: "Cannot install XFCE4.2 on Ubuntu..."
date: 2005-07-08
forum: General Help
---

### Post by fannymites on 2005-07-08
I've been trying to install XFCE4.2 on Ubuntu but I'm getting an "MD5SUM mismatch" on many of the required packages when trying to install via Synaptic.
I've tried downloading the XFCE4.2 graphical installer but I'm missing some dependencies and when I try to install those I get the "MD5SUM mismatch" error again.  

I'm using the sources from here - [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories) include the backports.  Is that the cause of the problem?  I haven't had any problems with any other packages so far.

---

### Post by PMO6022 on 2005-07-08
[QUOTE=fannymites]I've been trying to install XFCE4.2 on Ubuntu but I'm getting an "MD5SUM mismatch" on many of the required packages when trying to install via Synaptic.
I've tried downloading the XFCE4.2 graphical installer but I'm missing some dependencies and when I try to install those I get the "MD5SUM mismatch" error again.  

I'm using the sources from here - [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories) include the backports.  Is that the cause of the problem?  I haven't had any problems with any other packages so far.[/QUOTE]
 see [http://www.ubuntuforums.org/showthread.php?t=41647&highlight=md5sum](http://www.ubuntuforums.org/showthread.php?t=41647&highlight=md5sum)

---

### Post by fannymites on 2005-07-08
The fix suggested in that thread didn't solve the problem.
However, after commenting out the backports sources in sources.list, I was able to install XFCE4.2 without any problems.

---

