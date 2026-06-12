---
title: "Problem with repositries - ubuntu.com can NOT be found (I can't access website too)"
date: 2005-10-23
forum: General Help
---

### Post by sneax on 2005-10-23
I've seen a lot of posts of people having problems using synaptic, I too am having this problem. The problem is easy: I can not reach ubuntu.com - firefox can't access it either so it must be an 'internet' problem. I have no problems reaching any other site, just ubuntu.

What's happening? Who can acces them and who can't? I can't find much info about it, I don't know if this problem is known (I'm having it since yesterday). This is my ISP info:
Telenet Cable (Belgian ISP)

---

### Post by mykey on 2005-10-23
.. seems to happen occasionally - breezy is probably getting real popular so the servers have to handle a lot more load .. ;)

---

### Post by sneax on 2005-10-23
No this is a serious issue in my eyes. Why I think that it's something that needs more attention:
- I see a few others having the same problem, though they are newbies (like me) and what they say doesn't make big impact (als they don't make the link that if synaptic doesn't work it could be related to ubuntu.com not working).
- I'm definately sure something's wrong. I can not ping ubuntu.com, it simply times out. I would be happy to try to ping it's ip number directly if someone could post it.

Ubuntulinux.org isn't working either.

---

### Post by tiefling on 2005-10-23
[quote=sneax]- I'm definately sure something's wrong. I can not ping ubuntu.com, it simply times out. I would be happy to try to ping it's ip number directly if someone could post it.[/quote]

ubutnu.com IP is 82.211.81.130.

No similar problems here.

---

### Post by sneax on 2005-10-24
Gives time-outs too :( I don't understand ... Maybe I'll have to check with my ISP and give them a call! Thanks for the help so far.

---

### Post by guiriduro on 2005-10-24
traceroute to ubuntu.com (82.211.81.130), 30 hops max, 38 byte packets
 1  10.44.38.254 (10.44.38.254)  0.706 ms  0.626 ms  0.674 ms
 2  212.36.35.129 (212.36.35.129)  3.792 ms  1.305 ms  1.268 ms
 3  83-244-134-89.cust-83.exponential-e.net (83.244.134.89)  4.065 ms  1.973 ms  1.668 ms
 4  83.244.255.5 (83.244.255.5)  5.133 ms  2.660 ms  2.387 ms
 5  ge-2-1-524.ipcolo1.London1.Level3.net (212.113.11.113)  6.466 ms  2.964 ms  4.834 ms
 6  ae-0-51.bbr1.London1.Level3.net (212.187.131.1)  7.560 ms  2.793 ms  2.426 ms
 7  ae-1-0.bbr1.London2.Level3.net (212.187.128.46)  6.076 ms  2.448 ms  2.365 ms
 8  ge-3-0-0.gar1.London2.Level3.net (4.68.124.62)  5.137 ms  64.171 ms  23.962 ms
 9  * * *
etc. to 30 hops...

its not there (for me) - if others can see it then its a routing prob.

---

### Post by sourc3 on 2005-10-24
no problems here.
ubuntu.com: 82.211.81.130

---

### Post by awakatanka on 2005-10-24
Got the same problem can't get on ubuntu.com, ubuntulinux.org our kubuntu.org.

Also can't get on repositries.

I'm from Holland and run kubuntu 5.10 and have it for a few days now morning , midday and evening all the same.

Little frustrating want to install some things ;).

The forums are no problem but the rest is.:confused: :confused: :confused:

traceroute to ubuntu.com (82.211.81.130), 30 hops max, 38 byte packets
 1  192.168.2.1 (192.168.2.1)  0.316 ms  9.661 ms  8.808 ms
 2  nopenono.speedxs.nl (83.98.252.1)  28.698 ms  27.595 ms  27.913 ms
 3  ge3-5-779.redbus.speedxs.as25232.net (213.247.32.165)  28.492 ms  27.931 ms  27.939 ms
 4  g0-2-245.core01.ams03.atlas.cogentco.com (130.117.23.197)  35.339 ms  27.891 ms  27.904 ms
 5  p5-0.core01.lon02.atlas.cogentco.com (130.117.1.225)  41.246 ms  35.881 ms  34.117 ms
 6  p1-0.core01.bos01.atlas.cogentco.com (130.117.0.185)  109.941 ms  109.979 ms  180.034 ms
 7  p5-0.core01.jfk02.atlas.cogentco.com (66.28.4.118)  114.152 ms  116.037 ms  118.023 ms
 8  ge-7-13.car1.NewYork1.Level3.net (4.68.111.45)  113.990 ms  113.955 ms  114.039 ms
 9  ae-1-55.bbr1.NewYork1.Level3.net (4.68.97.129)  115.942 ms ae-1-51.bbr1.NewYork1.Level3.net (4.68.97.1)  109.959 ms ae-1-53.bbr1.NewYork1.Level3.net (4.68.97.65)  127.943 ms
10  ae-1-0.bbr1.London2.Level3.net (212.187.128.46)  175.980 ms  175.936 ms  176.073 ms
11  ge-3-0-0.gar1.London2.Level3.net (4.68.124.62)  196.052 ms  179.938 ms  178.049 ms
12  * * *
13  * *

---

### Post by Bavo on 2005-10-24
I have the same problem,

i'm also on Telenet in Belgium.

Looks like a problem with the ISP :s

---

### Post by rugglez on 2006-01-15
I have just had exactly the same problem after editing my sources.list file.

I commented out the first server that was giving me an error, then tried again (repeat as necessary I assume) and after that my downloads started working again.

---

