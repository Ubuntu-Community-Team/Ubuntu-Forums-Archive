---
title: "Bandwidth Limiting"
date: 2005-04-18
forum: General Help
---

### Post by kiddxaq on 2005-04-18
I'm wondering if there is a program available that will limit the download / upload speed of your network traffic (local). I'm not looking to set up a proxy server (squid), and if possible, not use something like NetLimiter through wine. Thanks

---

### Post by heimo on 2005-04-18
Hi!

Just to give you a better keyword - you probably want to look for a "shaper". This feature is in Linux kernel, but I'm not certain if it's enabled in Ubuntus standard kernel. Last time I tried it, it wasn't very good, but I guess the development work has continued.

This looks very, very old article (2.0-2.1 kernel) - so it probably doesn't solve your problem, but it can give you hints:
[http://lwn.net/1998/1119/shaper.html]("http://lwn.net/1998/1119/shaper.html")

And here are some packages you may want to give a look:
 ```
shapecfg - Bandwidth limiter for virtual network interfaces
shaper - Traffic shaper init script (cbq.init) for Linux
shaperd - A user-mode traffic shaper for tcp-ip networks
trickle - User-space bandwidth shaper
wondershaper - Easy to use traffic shaping script

```

---

### Post by rwabel on 2005-04-19
trickle does the job quit well. u start the program with trickle and give uplaod and downlaod parameter. But I made the experience with amule that it consumes a lot of memory. But I've to retry that maybe it depends also on the version of amule

I would be glad to hear some opinions from other users

---

### Post by ubuntu_demon on 2005-04-22
wondershaper is nice see :

[http://ubuntuforums.org/showthread.php?t=25911](http://ubuntuforums.org/showthread.php?t=25911)

But if you want to have more control / do more advanced stuff you should write your own script that's accustomed to your situation. I'm gonna do this en post this script with comments somewhere. But I don't know when.

---

### Post by diskotek on 2007-04-30
wondershaper or shaperd... trickel was not so good with amule..

---

### Post by diskotek on 2007-04-30
trickle with amule is not a so good solution...  :( i'll try wondershaper: sounds like an exercise tool that you can buy from tv-shopping.

my body is great with wondershaper, only 5 minutes a day 
:)

---

