---
title: "Desktop freezes when inserting or ejecting USB memory stick"
date: 2020-06-18
forum: General Help
---

### Post by SteveZsuzska on 2020-06-18
Hi, I am running 18.04LTS 64 bit. Recently, I have found that when I insert a USB memory or eject it, the desktop freezes for about 4 minutes. During this time the mouse pointer is still responsive but I cannot tab between windows or type into a terminal window, for example. In fact the mouse pointer is about the only thing still functional. Eventually it recovers. I have tried more than one stick. Any ideas please?

Steve

---

### Post by HermanAB on 2020-06-19
Open a terminal, run top or htop, insert memory stick...

---

### Post by kneutron on 2020-06-20
--Anything in /var/log/messages related to this? Device timeouts, bus resets, etc.  Your USB port maybe going bad or you might need to use a powered USB hub

--I would also use the other person's suggestion about running top while testing, check your free memory and swap space

---

