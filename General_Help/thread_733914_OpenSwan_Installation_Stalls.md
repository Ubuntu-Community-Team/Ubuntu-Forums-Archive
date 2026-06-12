---
title: "OpenSwan Installation Stalls"
date: 2008-03-24
forum: General Help
---

### Post by wak88 on 2008-03-24
Hi everyone,

I'm running 7.10 Server and attempting to install OpenSwan.  I'm simply running apt-get install openswan, but it seems to stall during the configuration process.  I've let it sit for over 20 minutes with no progress and the processor is idling.  Any ideas?  

:confused:

---

### Post by GermanShepherd on 2008-04-15
Hey! I don't know if you need this anymore, but I thought I'd give a heads up for anyone who finds this thread via Google (like I did). OpenSwan generates a 2048 bit key when you pick plain RSA... When it was stuck on "configuring openswan" for more than 5 minutes, I checked the hard drive lights and CPU activity and everything was idle, so I started to worry... But I read some posts that said it took a few minutes. Heh, boy, was that was an understatement! I installed it on Ubuntu 7.10 Server, with a 1.8GHz Pentium III, and it took me 38 minutes to generate the key. Just wanted to say that it takes an astronomical amount of time, but if you hang in there, it'll get done!

---

