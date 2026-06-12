---
title: "proftpd passive ftp problem"
date: 2006-11-16
forum: General Help
---

### Post by divas on 2006-11-16
Hi. I have a problem which I try to solve during the past three days.
I 've setup proftpd with passive ftp.

PROBLEM:
When I connect from outside my LAN with the unix command ftp tool (ftp -p) I login successfully. I also try the ls command and it works. But when I try a cd command, the connection stops responding. The strange thing is that when I try the cd command before the ls, it works fine.

NOTE1: When I connect from inside my LAN, everything works fine.
NOTE2:I tried to connect through other ftp clients by still no hope.

CONFIGURATION:
I use port 21. I connect from outside my router from port 1717 (I forward 1717 to 21).
I use passive ftp ports 60017-60019. I configured proftpd to use these ports. I forward these ports on my router. I open  these ports on firestarter.
I don't use masquerade since I forward the passive ports on the router.

NOTE3: If someone wonders why I use port 1717, this is because of my stupid router (Sagem 1500), which cannot forward ports less than 1024.

Any help would be greatly appreciated and would save me from many  hours of staying asleep!

---

