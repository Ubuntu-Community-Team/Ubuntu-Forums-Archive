---
title: "Azureus - VERY slow p2p. Probably NAT problem."
date: 2008-05-07
forum: General Help
---

### Post by jakupl on 2008-05-07
My download speed is amazingly slow!
Right now Azureus is downloading at a breathtaking 24 B/s (not kB but B/s)... occasionally it speeds up to 1 kB/s ;)
This is driving me mad, as I have a 4000 kB/s cable.

I have tried all sorts of stuff but nothing works.

I am in a dormitory, but this can't be the problem, because I got full download speed in windows.

do you have any ideas?


btw. this is the output of 'sudo iptables -L -nv'

```
Chain INPUT (policy ACCEPT 116K packets, 110M bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 101K packets, 12M bytes)
 pkts bytes target     prot opt in     out     source               destination 
```

thankyou very much.

---

### Post by jakupl on 2008-05-07
a-very-slow-bump

---

### Post by ghost_ryder35 on 2008-05-07
do you have the proper ports open in azureus and your router for incoming connections?  (i.e. port forwarding)

---

### Post by jakupl on 2008-05-07
my incoming TCP listen port in auzerus is 32262.
When I try to test it, i get:

"Testing port 32262 ... 
NAT Error - Connection to 130.225.165.18:32262 (your computer) refused."

[QUOTE="ghost_ryder35"]and your router for incoming connections? (i.e. port forwarding) [/QUOTE]

this is where I pack my stuff ;)
what is a router? My internet goes through a cable from the computer, and straight to the wall.

---

### Post by jakupl on 2008-05-08
bump

---

### Post by stomm on 2008-05-08
Hi mate,

To a home user a router is a device that lets multiple PC's/Consoles/Etc.. access to the internet. The router would connect to the modem and your PC would connect to the router in turn. You can find them in most computer shops quite cheaply these days and its a better alternative to just connecting straight from your PC.

If you find Azureus isn't connecting at all, you might find that your Internet Service Provider is trying to block the connection. A router would help in this scenario as you can change the ports that Azureus connect with to something else without affecting your speed or connection.

If you don't want to buy new equipment, it may be worth searching for your ISP's name through google and the term 'port forwarding' - that would give you the instructions you need to get Azureus connecting properly.

---

### Post by Gerafin on 2008-10-12
Since you're not using a router, your problem is with your ISP. My ISP runs all their connections through a firewall. Here's something that should help:

-Make sure download speed is set to "unlimited" (seems obvious, but... right-click on the download speed in the bottom right-hand corner to change)
-The NAT problem is making it so that people who you receive data from are not recognizing any data that you upload. So, most peers/seeds that you download from will then disconnect after you've only got a little piece of data. The way around this is to increase the number of people that you download from. 
[LIST=1]
[*]Go to tools->options
[*]Click on "Transfer", making sure that your "mode" is set to advanced
[*]Set "Max Connections per Torrent default" to 0 [unlimited]
[/LIST]

This made my speed go from 20 kbps to over 200. Let me know if that helps.

---

