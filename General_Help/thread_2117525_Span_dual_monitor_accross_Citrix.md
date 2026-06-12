---
title: "Span dual monitor accross Citrix"
date: 2013-02-18
forum: General Help
---

### Post by Hendry on 2013-02-18
I Installed Ubuntu 12.04LTS and have a NVIDIA Geforce 9500GS dual head displaycard in my system. I already got my Ubuntu desktop extended over my 2 monitors. Now I want to do the same for my Citrix Session. 

I installed the latest Citrix receiver and did a check with the HDX util to see if my dual monitor is detected: 

-- Checking that your XServer supports Multi-Monitor...
-------------------------------------------------------
Success! - Multi-monitor is supported!
Found the following Monitors:
  head #0: 1920x1080 @ 1280,0
  head #1: 1280x1024 @ 0,0

I then changed my wfica.sh to the following command:

$ICAROOT/wfica -span 0,1 -file $1

When now connecting to out XenDesktop environment I still get stuck running my Citrix session on one screen. I also changed 0,1 to 1,2 but also no luck.

Anybody succes with the spanning of a Citrix display accross 2 monitors?

---

### Post by the_tiger on 2013-04-03
You need to change the way the ICA Client launches in Firefox to use the shell script you have created. Go to Edit > preferences > applications.

Ben

---

### Post by handheld-penguin on 2013-06-11
You can also set an environment variable:
[http://brogrammador.blogspot.co.uk/2013/04/citrix-from-web-interface.html](http://brogrammador.blogspot.co.uk/2013/04/citrix-from-web-interface.html)

---

### Post by handheld-penguin on 2013-06-16
```

-span a

```
works well for me

---

