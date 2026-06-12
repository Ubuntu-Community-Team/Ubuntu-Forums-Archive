---
title: "Boot Issues."
date: 2016-06-16
forum: General Help
---

### Post by brad48 on 2016-06-16
Hey all. I'm having some boot problems. I'm typing this on my iPad, so I'll have to post links instead of inserting images.

as you can see here, I can't boot - [http://i.imgur.com/4qWsM8U.png](http://i.imgur.com/4qWsM8U.png)

im unsure as to whether there's an issue mounting the root device, or if there's an issue with the uuid. I've checked via a bootable USB my grub.cfg file, and from what I can tell, the uuid's match up fine - [http://m.imgur.com/MOueLvo](http://m.imgur.com/MOueLvo)

i should probably note that my bootable USB can't boot into a graphical mode, but I can login via tty1, which is how I got that above screenshot. Where do I go from here? Thanks.

also, the only thing I did before shutting down that could relate is I installed grub to a USB using a program whose name I cannot recall. It's one of those bootable USB programs.

edit: blkid shows the same uuid too

---

### Post by gordintoronto on 2016-06-16
What version of Linux is on your USB? How did you create it? Did you install Linux on your hard drive? What version?

And perhaps you could describe your computer: CPU, memory, video adapter, hard drive size?

---

### Post by brad48 on 2016-06-16
Usb: Ubuntu 15.10; created with with the startup disk creator provided by Ubuntu    
Pc: Ubuntu 15.04; on a partition part of a single 1tb HDD

Pc Specs: i5 4210u; R7 m260(uninstalled); Currently using integrated graphics; 8GB RAM

---

