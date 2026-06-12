---
title: "vivid broken after today's updates"
date: 2015-05-21
forum: General Help
---

### Post by jbinpg on 2015-05-21
Updates came in this morning. Installed them then rebooted. Entered password at login screen and was punted back to login screen. Tried again but endless loop. SSHd in from another box and did startx. Error saying cannot get file descriptor and Xbox will not load. Then rebooted with upstart but same thing. I am locked out of my box at this point.

---

### Post by jbinpg on 2015-05-21
SOLVED: I rebooted using the -16 kernel then did updates which installed a whole new load of kernel and header files. -18 kernel now booting fine. I suspect there was one earlier update which should not have got through but did and screwed everything up.

---

### Post by Hugh_Barstead on 2015-05-21
I had the same issue. It took me half an hour to purge the -18 kernel & associated stuff, now back to -16 where all works well. After reading your post I thought I would try again and guess what - the only software update available was a printer update. This morning's kernel upgrade seems to be missing in action. I guess there was a big OOPS somewhere along the line. I am surprised that you got -18 working. 

Hugh Barstead

---

