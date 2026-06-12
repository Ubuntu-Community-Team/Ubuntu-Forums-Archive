---
title: "On line: But Browser can't find server"
date: 2007-11-15
forum: General Help
---

### Post by Poppyelvin on 2007-11-15
I have been trying for months now to get online with ubuntu 7.04

I am writing this from xp on the same machine. It didn't have a serial port, so now I have added one. I also plugged in a serial modem that I know worked fine on another machine I have with Fedora on it.

The modem dials and gets on-line. (Or at least ties up my phone line like it is on.) But when you go to FireFox and try to go to google or something, It says: Can't find server.

I've tried everything I know, but I must be missing something.

I am very new to linux, but I am trying to learn. Any advice would be appreciated.

Thank You

PoppyElvin

---

### Post by mike555 on 2007-11-15
sounds like a DNS problem , try putting the DNS numbers manually , if you don't know the numbers put in these ...     208.67.222.222 and 208.67.220.220.      ..... they are for "OpenDNS" , a great DNS server .

---

### Post by Poppyelvin on 2007-11-16
Thank You mike555 for the help. I did find 2 DNS numbers in my ipconfig file in windows, and I tried to add them to my pppd in ubuntu. Guess I'm just not smart enough yet to do what you are asking. But Thank You

Poppyelvin

---

### Post by zvacet on 2007-11-16
network manager>manual configuration>network>DNS tab<put yours DNS there and if you find nay other DNS address there and you are not use router,just delete that address.That will leave just two you add.Close.go to the general tab and tick your modem and you should see box with **changing network interfaces**.When it is finish close.

```
pppoeconf
```

---

### Post by Poppyelvin on 2007-11-17
Thank You ZVACET for your help. I'm still working on trying to get that to work. I don't have a lot of spare time though. I will let you know when I either get it or give up. Meanwhile thanks again for the help.

Poppyelvin

---

### Post by Poppyelvin on 2007-11-18
SUCCESS!!! I'm sending this reply on Mozilla Firefox on my ubuntu. Thank You ZVACET and mike555 for your help. I'm not real sure what happened I've been trying to follow your instructions and anyway this is SUCCESS!!! Praise The Lord and Thank You very much mike555 and ZVACET. 

Poppyelvin

---

### Post by zvacet on 2007-11-18
Tnx,and wellcome to Ubuntu!

---

