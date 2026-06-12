---
title: "How to install uTorrent server properly in 12.10"
date: 2013-05-06
forum: General Help
---

### Post by josh11 on 2013-05-06
I'm running Elementary OS Luna which is based on Ubuntu 12.10. I installed uTorrent server edition following this guide:


>[http://askubuntu.com/questions/104094/how-to-install-utorrent-step-by-step](http://askubuntu.com/questions/104094/how-to-install-utorrent-step-by-step)


Everything works fine. I go to localhost:8080/gui/ and uTorrent WebUI loads.


However, after a restart it is broken. When I restarted my machine I go to the terminal and type "utserver start" and I get:


    server started - using locale en_GB.UTF-8
    Using locale en_GB.UTF-8
    total physical memory -1 max disk cache 33554432
    IPv6 is installed
    ^Cserver exited with 0


Now, when I go to: localhost:8080/gui/ I get a Chrome error "cannot display the webpage", and so I am forced to install uTorrent again. I can still access all my old downloaded torrent files and so on, so in that respect it isn't so bad but I have to re-install every time I restart which is a PITA.


Does anyone know how to fix this?


Thanks

---

### Post by lokiz on 2013-07-09
I'm running Ubuntu 12.04 and I am experiencing the same problem.

I installed via the same walkthrough as above and after I rebooted it stopped working.

I get the exact same error messages as the previous post, except of course GB is replaced with US.

---

### Post by papibe on 2013-07-09
Hi josh11.

AFAIK, uTorrent server does not include upstart scripts so it does not start automatically after a reboot.

When you start it manually you need to leave it running on the terminal (don't press Ctrl+c as in your example). I personally use 'screen' to detach it from the terminal and get it on the background.

Just a thought.
Regards.

---

### Post by lokiz on 2013-07-09
Problem was solved by doing this

kill all instances of utserver using system monitor and then run the following code


utserver -settingspath /opt/utorrent-server-v3_0/ &

---

