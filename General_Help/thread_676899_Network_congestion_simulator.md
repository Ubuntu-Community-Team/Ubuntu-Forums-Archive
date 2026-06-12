---
title: "Network congestion simulator"
date: 2008-01-24
forum: General Help
---

### Post by hebetude on 2008-01-24
If you are looking for a tool geared towards simulating real worldish performance, it comes with the default kernel in Ubuntu.  Took me forever to find this, so I'll post my experience.  It's called 'tc'.

Some related tools include netem, NISTnet, etc.  You can do a lot of things with it, I use it to simulate network latency to better optimize large web pages I'm developing.  This gives me the benefit of simulating Joe Bob's 200msec internet connection on my very fast 100mbit 0msec connection to our web servers.

Here's what I did to simulate a 200msec network delay:
```
sudo tc qdisc add dev eth0 root handle 1:0 netem delay 200msec
```



Reference:
[http://www.kdedevelopers.org/node/1878](http://www.kdedevelopers.org/node/1878)

---

