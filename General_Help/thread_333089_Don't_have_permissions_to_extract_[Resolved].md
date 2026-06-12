---
title: "Don't have permissions to extract [Resolved]"
date: 2007-01-06
forum: General Help
---

### Post by GolfGeek on 2007-01-06
Hi all
I just recently reinstalled edgy on a laptop (Compaq presario 2100) and want to set up wifinfgi. This laptop has the bcm4306 chipset. I downloaded the necessary file, moved it into the /sbin folder and tried to extract the 2 files (bcmwl5.inf & .sys) When I go to extract the files I enter my password and click extract and get the following error:
"You don't have the necessary permissions to extract archives in folder /sbin"
I checked the permissions tab in the properties for that folder and it indicated that I am not the owner of the folder so I can't change the permissions. The owner is root.  What do Ido to correct thius

thanks

Got it. After reading another unrelated thread, I needed to use terminal mode, cd into sbin and sudo unzip bcmwl5.zip to get the contents out.

---

### Post by taurus on 2007-01-06
What is the name of that file and where is it right now?  You can extract it from a terminal if you wish...  It works better than the point and click thing!  ;)

---

### Post by aysiu on 2007-01-06
This will help:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by GolfGeek on 2007-01-06
Taurus
Thanks. I just edited my message with the solution. Another thread mentioned using sudo in terminal mode, tried it and it worked. Thanks

---

### Post by taurus on 2007-01-06
Yip.  Need to use sudo each time you need to write/modify something outside your $HOME directory.  ;)

---

