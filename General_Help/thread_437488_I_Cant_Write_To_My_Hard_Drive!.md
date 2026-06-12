---
title: "I Cant Write To My Hard Drive!"
date: 2007-05-08
forum: General Help
---

### Post by scorpedion on 2007-05-08
Ok, new here and to Ubuntu. I tired to install to ubuntu edgy eft to my drive. Unfortunately, I cant seem to save/move files to anywhere except the desktop. Everytime i try to i get an error message saying I dont have permission to write to the drive or folder. About four attempts to install it using different partitions has rsluted in the same thing. So can anyone tell what I'm doing wrong?

If it's of any consequence, I used ext3.

---

### Post by abc123456 on 2007-05-08
sudo chmod -R 777 to directorys.  If you are on the net all the time then use 444.:)

---

### Post by aysiu on 2007-05-08
What are you trying to save/move in? /home/scorpedion? Or somewhere else (/etc or /usr)? If it's somewhere else, you should read this:
[http://www.psychocats.net/ubuntu/permissions#gui](http://www.psychocats.net/ubuntu/permissions#gui)

If it's /home/scorpedion, try ```
sudo chown -R scorpedion:scorpedion /home/scorpedion
``` If it's a separate partition, try this:
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by scorpedion on 2007-05-09
Thanks. That permissions page explained a lot, aysiu.

---

