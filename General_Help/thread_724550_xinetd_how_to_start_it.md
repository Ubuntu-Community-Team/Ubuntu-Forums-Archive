---
title: "xinetd how to start it"
date: 2008-03-14
forum: General Help
---

### Post by Jethro_uk on 2008-03-14
Hi all,
 been playing with this : [http://ubuntuforums.org/showthread.php?t=122402](http://ubuntuforums.org/showthread.php?t=122402) (starting VNC on boot) and after a crash course in all things Linux, I think I've found a snag.

I had no xinetd.conf file at all to start with. No problem, as per the instructions I created it. However, it seems to me that the xinetd program/service isn't running. I did a 

grep xinetd /var/log/syslog and it returned nothing.

How should xinetd be configure to start at boot. Am I correct in thinking there should be a script in /etc/init.d ?

I've googled, but not found much that made sense. I was hoping someone here could ....

---

### Post by Jethro_uk on 2008-03-17
>bump<

---

