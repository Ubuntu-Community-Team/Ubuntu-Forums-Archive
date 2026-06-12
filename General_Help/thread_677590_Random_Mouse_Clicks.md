---
title: "Random Mouse Clicks"
date: 2008-01-25
forum: General Help
---

### Post by malfist on 2008-01-25
This is driving me crazy, I cannot find any cause for such behavior of my mouse. It clicks, randomly, even when my had is not on it. I was laying in bed reading about the Greeks and my mousereadhttp://www.stumbleupon.com/url/www.lewrockwell.com/orig3/monahan1.html changes the music on me, from linkin park to Johnny Cash. ! I can't figure out why it is doing this, it's done it twice while trying to type this.

It doesn't seem to do a left click because it doesn't act like I clicked on something but middle clicks and right clicks are common (third click typing this), sometimes it does a rightclick and selects something from the right click menu.

Anyone have any idea what's causing this? It's driving me nuts. The mouse is a laser wireless and the receiver is about 8-14 inches away from it at any given time. I can often use this mouse past it's 3ft range.

edit: thought it might be the vibrations from my music but it happened when the music was turned off too.

edit 2: I think it's telepathic too, I just closed a tab by accident so I went to click and reopen the tab, but my mouse beat me to it and already had it open. But, mind you, the right click menu was still open which leads me to think it may be something besides the mouse.

---

### Post by wieman01 on 2008-01-25
Interference with other 'wireless' devices? What hardware are we talking about?

---

### Post by malfist on 2008-01-25
Nothing. The only wireless I have is the mouse, my keyboard is cabled. I have a bluetooth headset for my phone but that shouldn't affect and is also turned off. Wireless internet is forbiden in the dorms (although there is one on channel 11), but the mouses frequency shouldn't be that high.

It goes in spurts too. I won't have it do it for a day or two, than all of a sudden it will do it 50-100 times in 45 minutes or so, then it will start tapering off and go away. Currently it's stopped.

Dmesg if filled with this repeating over and over:
```
[300617.185120] NVRM: API mismatch: the client has the version 100.14.23, but
[300617.185124] NVRM: this kernel module has the version 100.14.19.  Please
[300617.185126] NVRM: make sure that this kernel module and all NVIDIA driver
[300617.185127] NVRM: components have the same version.
[300890.274143] Inbound IN=eth0 OUT= MAC=00:30:18:fb:e4:ab:00:15:c7:02:cf:80:08:00 SRC=***.**.***.*** DST=***.**.***.*** LEN=48 TOS=0x00 PREC=0x00 TTL=126 ID=32529 DF PROTO=TCP SPT=2493 DPT=445 WINDOW=16384 RES=0x00 SYN URGP=0 
[300893.518951] Inbound IN=eth0 OUT= MAC=00:30:18:fb:e4:ab:00:15:c7:02:cf:80:08:00 SRC=***.**.***.*** DST=***.**.***.*** LEN=48 TOS=0x00 PREC=0x00 TTL=126 ID=32624 DF PROTO=TCP SPT=2493 DPT=445 WINDOW=16384 RES=0x00 SYN URGP=0 

```

IP addresses replaced.
eth0 is my wired connection too.

---

### Post by malfist on 2008-01-25
It's doing it again today.

---

### Post by malfist on 2008-01-25
Switched batteries to no avail, changed frequency the mouse and recieve was on and has not happened since, but that was less than a minute ago.

---

### Post by rosegarden78 on 2008-01-25
Wowzers!  Someone is using 'remote viewing' and a 'psi amp' to exert 'mind control' over your desktop.  Good luck!

---

### Post by malfist on 2008-01-25
I think it's the renovated Dark Templars from Starcraft II *nods*

---

### Post by wieman01 on 2008-01-26
What hardware is it then? Logitech?

---

### Post by malfist on 2008-02-01
Mirco I think, after reconnecting the mouse (it's self connecting) it resolved the issue. I'm blaming it on some type of interference.

---

