---
title: "Custom /etc/issue"
date: 2007-02-10
forum: General Help
---

### Post by passonno on 2007-02-10
hello

just wondering if anyone can tell me how to send commands to /etc/issue at boot, for example, to: 

run the 'clear' command, 
then run fortune(like slackware)
then login prompt.

Any ideas?

---

### Post by neilp85 on 2007-02-11
I'm not sure of the correct way for doing this but here's a hack that would work. For a new fortune each day you could just add a cron job as root that cat's the fortune to the /etc/motd file.

---

### Post by neilp85 on 2007-02-11
My previous solution was pretty dumb, here's a better one. Just add clear and fortune to the end of your ~/.bashrc file.

---

### Post by passonno on 2007-02-11
Sweet!! Thanks!!!

---

### Post by jason_Xtreme on 2007-06-18
> **neilp85 said:**
> My previous solution was pretty dumb, here's a better one. Just add clear and fortune to the end of your ~/.bashrc file.

been trying to find this 4ever i love this community thanks.

used it to run a get ip info script on login.

---

