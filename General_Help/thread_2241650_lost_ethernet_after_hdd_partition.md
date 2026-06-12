---
title: "lost ethernet after hdd partition"
date: 2014-08-27
forum: General Help
---

### Post by jdefed on 2014-08-27
I did a clean install of 14.04 lts and lost a partition I had on the hdd. Everything was working fine, but I wanted to put the partition back. I loaded Parted Magic from cd and ran it live, then put in partition. Then removed cd and started the hdd normally. After loading I didn't have ethernet connection. Green light was not flashing on ethernet connection, so it wasn't talking to router. Did a google search and found these instructions, 1) sudo ifconfig eth0 up, 2) sudo service networking restart. After doing that ethernet was working. Can someone explain what happened, I'm guessing the live cd did something to the ethernet.

---

### Post by varunendra on 2014-08-29
All I can say is yes, you are right. It must have been the Live Parted Magic session. Partitioning operations have nothing to do with network configurations, so it might have the older driver in the session, or something else that sent the card into a sleep/off state, maybe while shutting down.

So it seems you don't need help for anything? Just an explanation which I guess can only be different guesses now? :p

If so, I think you should mark the thread as [SOLVED] since I doubt there can be any other explanation to the behaviour you described.

---

