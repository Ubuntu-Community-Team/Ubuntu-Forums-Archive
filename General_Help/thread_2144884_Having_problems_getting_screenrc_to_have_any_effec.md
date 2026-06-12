---
title: "Having problems getting screenrc to have any effect"
date: 2013-05-13
forum: General Help
---

### Post by Curtis.Everingham on 2013-05-13
Hello, and thanks in advance for any help with this

On previous systems I have set up a screenrc to launch multiple windows on login. On my new system, however, I cannot seem to get this working.


I have a simple file with nothing besides the extra screen windows:

screen -t "sYs" 0 
screen -t "rtPass" 1 rtorrent -n -o import=/mnt/rt1.rc
screen -t "rtWhat" 2 rtorrent -n -o import=/mnt/rt4.rc
screen -t "rtPub" 3 rtorrent -n -o import=/mnt/rt3.rc
screen -t "BaSh" 4

I have this saved as ~/.screenrc


After running into problems I tried moving this to /etc/screenrc,  but still see no difference when logging in

Byobu was enabled, running screen on its own did not solve the problem either.

Not really sure whats going on here. Do I need to make a startup script or make a special entry in crontab or anything like that? I don't remember having to do that last time but not sure how else to tell my system to acknowledge the configuration file

Thanks again

---

