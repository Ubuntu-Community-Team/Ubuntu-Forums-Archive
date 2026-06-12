---
title: "Stability issues"
date: 2007-01-18
forum: General Help
---

### Post by !nkubus on 2007-01-18
Since about 2 or 3 days it looks like my main computer have some stability issues if I leave the comp open for a long time let's say 10 hours downloading or doing nothing , when I come back the computer is in a strange sleep mode where it looks open but nothing respond, and the screen say no input , I cannot wake him up, I have too reboot. I also have really frequent network problems, where suddenly my comp is looking like it's connected but I have to force a networking restart: /etc/init.d/networking restart. :-k 


Is nobody having theses issues?


I don't have much details I know , but I don't know where to start.

Nothing looks wrong in my /var/log/messages

I'm running Edgy, and I do all the updates as they come, so I'm assuming theses come from an update but I can be wrong, but there have been couple of kernel upgrades lately.

Thanks for your help

---

### Post by bernied on 2007-01-18
A quick thought - have you done a memory (RAM) test recently? It should be one of your boot menu options.

---

### Post by !nkubus on 2007-01-18
Unfortunatly the RAM test went ok. I just had a thought I installed network manager that could be the problems with my networking , I'll ry remove it

---

### Post by tronica on 2007-01-18
do you have it set to turn of hard disk's or turn of monitor or go into sleep mode. If so disable all of those and see what happends.

---

### Post by Hendrixski on 2007-01-18
oh that's an easy one to fix.  change your power-management settings to not do that.

---

### Post by !nkubus on 2007-01-18
> **Hendrixski said:**
> oh that's an easy one to fix.  change your power-management settings to not do that.

The monitor was set to turn ff after 40 minutes.. that might be one of the problems, I set it to never. Thanks

And by navigating my logs I think I found interesting  network activity in deamon.log:

> 
Jan 18 17:25:15 frank-desktop dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
Jan 18 17:25:57 frank-desktop last message repeated 4 times
Jan 18 17:27:04 frank-desktop last message repeated 4 times
Jan 18 17:27:57 frank-desktop last message repeated 4 times
Jan 18 17:29:06 frank-desktop last message repeated 5 times
Jan 18 17:29:52 frank-desktop last message repeated 4 times
**Jan 18 17:29:58 frank-desktop dhclient: bogus UDP packet length: 324**
Jan 18 17:30:00 frank-desktop dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
**Jan 18 17:30:06 frank-desktop dhclient: Discarding packet with bogus hlen.**
Jan 18 17:30:13 frank-desktop dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
Jan 18 17:30:13 frank-desktop dhclient: bogus UDP packet length: 324
Jan 18 17:30:16 frank-desktop dhclient: bogus UDP packet length: 324
Jan 18 17:30:26 frank-desktop dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
Jan 18 17:30:30 frank-desktop dhclient: bogus UDP packet length: 324
Jan 18 17:30:34 frank-desktop dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
Jan 18 17:30:42 frank-desktop dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
Jan 18 17:30:57 frank-desktop dhclient: bogus UDP packet length: 324
Jan 18 17:30:58 frank-desktop dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
Jan 18 17:31:18 frank-desktop dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
Jan 18 17:31:21 frank-desktop dhclient: bogus UDP packet length: 324
Jan 18 17:31:29 frank-desktop dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
Jan 18 17:31:29 frank-desktop dhclient: bogus UDP packet length: 324
Jan 18 17:31:32 frank-desktop dhclient: bogus UDP packet length: 324
Jan 18 17:31:34 frank-desktop dhclient: DHCPACK from 192.168.1.1
Jan 18 17:31:34 frank-desktop NetworkManager: <information>^IDHCP daemon state is now 3 (renew) for interface eth0 
Jan 18 17:31:34 frank-desktop dhclient: bound to 192.168.1.101 -- renewal in 42587 seconds.
Jan 18 17:31:40 frank-desktop dhclient: bogus UDP packet length: 324
Jan 18 17:31:57 frank-desktop last message repeated 2 times
Jan 18 17:33:03 frank-desktop last message repeated 4 times
Jan 18 17:33:22 frank-desktop dhclient: bogus UDP packet length: 324
**Jan 18 18:16:15 frank-desktop NetworkManager: <information>^IGoing to sleep. **
**Jan 18 18:16:15 frank-desktop dhclient: receive_packet failed on eth0: Network is down**


this is really weird

---

