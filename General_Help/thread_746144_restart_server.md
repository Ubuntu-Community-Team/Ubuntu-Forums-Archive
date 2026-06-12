---
title: "restart server"
date: 2008-04-05
forum: General Help
---

### Post by d0tn3t on 2008-04-05
i want to make my server auto restart every 2 hours
how can i make that ???
coz it hang up 
i'm using  a card sharing server cccam

i'm using ubuntu 6.6

---

### Post by cmnorton on 2008-04-05
Will you daemon respond to a start, stop, or restart?

sudo /etc/init.d/your_server restart

If it does, you can put a cron entry into /etc/cron.

# m h dom mon dow user    command
00 *    * * *    root /etc/init.d/your_server restart

If you daemon does not respond to these commands, you have a scripting job to find the process id; kill -9 process-id-of-your-daemon, and then restart the daemon.

But there looms a larger question, which is getting your daemon fixed.

---

### Post by pandokrator on 2008-05-25
i search also for this solution.
every 20 hours , CCcam crash.
a good way for that is , one script in ubuntu server for restart /usr/local/bin/CCcam or just a command "reboot".

---

