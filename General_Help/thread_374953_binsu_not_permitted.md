---
title: "/bin/su not permitted"
date: 2007-03-03
forum: General Help
---

### Post by Starlights on 2007-03-03
Hello,

I've got a script that uses tcpdump. I want to run it on Ubuntu. Each time I use sudo, it asks for password, but when I run this script, it doesn't give a prompt, it just halts, till I give it a Ctrl^C. The box doesn't let me to use "sudo su", and as I am not the administrator of the box, I don't want to change that. is there any other way of becoming root? I might be helpful to say that, I am ssh-ing to the box, therefore I'm only using command line, no window manager. 

It's also good to know how to enable /bin/su, because now it says that it's not permitted.


Thank you in advance
Starlights:KS

---

### Post by yabbadabbadont on 2007-03-03
sudo -s -H

Will drop you into a root shell.  Then you can run the script.

---

