---
title: "Constant random crashes"
date: 2014-03-16
forum: General Help
---

### Post by michael125 on 2014-03-16
Hi, I'm hoping you guys could help me. I have an old machine with athlon xp 1800 and 512mb of ram. It is running ubuntu 10.04 and I keep getting constant crashes, when it crashes it doesnt respond to any commands not even alt+ sysreq. Sometimes it crashes within seconds of booting up, sometimes when I open the browser, usually within just a couple of minutes. I was able to go into tty and it crashed but I have no idea what It means, I took a picture of it and will post it. I'll appreciate any help you guys could give me with this. Thanks

---

### Post by michael125 on 2014-03-16
Thanks
[http://i.imgur.com/wJu485f.jpg](http://i.imgur.com/wJu485f.jpg)

---

### Post by tgalati4 on 2014-03-16
What you have posted is a trace dump of lots of "oops" in the kernel at 87 seconds after boot.  Not helpful.  How old is the machine?  Check the voltages in BIOS or with a voltmeter.  Remove extra hardware from the machine.  Inspect it for bulging or leaking capacitors.  Blow out the dust and reseat all of the cables.

---

### Post by sanderj on 2014-03-17
I would run Memtest86 from the Ubuntu Grub boot menu, and keep it running for a few hours. If any errors, then the hardware is the problem. Not Linux

---

