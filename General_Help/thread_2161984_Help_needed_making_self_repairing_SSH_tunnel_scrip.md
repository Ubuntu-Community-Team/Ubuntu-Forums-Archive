---
title: "Help needed making self repairing SSH tunnel script"
date: 2013-07-12
forum: General Help
---

### Post by CaptainMark on 2013-07-12
Hi all.

The boss at work has asked me to make the wifi available to the public for our customers meaning I am now forced to use what is a completely unsecure connection to do any web browsing. I now use a socks proxy to make a secure ssh tunnel to my home server (named raspberrypi_mobile in my ssh setup) any time I want to go on my work laptop, I wanted to automate the process so it could run in the background and I don't have to bother creating the tunnel every time I use the laptop so I have this script which runs on login (not boot)```
#!/bin/bash

while true; do
     sleep 5
     ping www.google.com -c 1 && break
done
ssh -D 2808 raspberrypi_mobile

```This allows time for the laptop to connect to the wireless network and then creates the ssh tunnel

The problem here is that this only works whilst the network remains connected, as soon as I slightly go out of range or I close the laptop lid or anything that severs the tunnel, it hangs and I'm left with a dead ssh tunnel which I have to manually kill and reinstate to get it back and running.

I'm completely open to suggestions if anyone wants to help me out with this one, there must be a way to alter this script so that if the network goes down the tunnel is closed automatically and then I can loop the whole thing back to the start and await a fresh internet connection to make a fresh tunnel?

Many Thanks 

Mark

---

### Post by markbl on 2013-07-12
"apt-get install autossh" is easier and FAR more robust to all the edge condition problems you haven't discovered yet.

---

### Post by CaptainMark on 2013-07-13
I'd never heard of autossh until now, thanks it's really good and does exactly what I need simply swapping out ssh for autossh

---

