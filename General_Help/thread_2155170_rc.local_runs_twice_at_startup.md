---
title: "rc.local runs twice at startup"
date: 2013-06-17
forum: General Help
---

### Post by Deery50 on 2013-06-17
Hello, I use ubuntuserver and In my /etc/init.d/rc.local file I have a line like this.: ```
cd /home/marcus/mcserver/ && ./start.sh
``` This starts the .sh file that starts my gaming server. The only problem is that when the computer starts up, that line gets run twice and it trys to start the server 2 times which generally just doesn't work. Thanks to anyone who can help.

---

### Post by Toz on 2013-06-17
> **Deery50 said:**
> Hello, I use ubuntuserver and In my **/etc/init.d/rc.local** file
The correct file to edit is **/etc/rc.local**. Try removing the commands from the previous file and add them to this one. If it still starts twice, can you post the contents of your start.sh file?

---

### Post by Deery50 on 2013-06-17
> **Toz said:**
> The correct file to edit is **/etc/rc.local**. Try removing the commands from the previous file and add them to this one. If it still starts twice, can you post the contents of your start.sh file?
Oh, I moved the line to /etc/rc.local and it's working fine now. Thanks!

---

