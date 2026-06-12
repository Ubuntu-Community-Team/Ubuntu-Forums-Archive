---
title: "Auto-boot a Virtual Machine..."
date: 2008-01-01
forum: General Help
---

### Post by crazycarlt on 2008-01-01
This is a tricky and possibly hopless hack, but to get to the short bit:

I want to boot a windows XP virtual machine automatically on my Ubuntu Feisty server.

Long bit:

My family just picked up a Kodak EasyShare digital picture frame with wireless. Yeah, yeah, the short answer is already apparent: build a ubuntu box in a small form factor and put a nice, big monitor in front of it.

Let's roll with the kodak POS first, though.

It can access Windows Media Extender hosts' libraries over wifi. It's quite neat, except that all of the relevant media is currently being hosted on the Ubuntu server. The only capable media extender is a not-always-on laptop.

Windows media player 11 is the cincher, apparently it allows you to add its media library and allow certain devices to access it for media extension.

Now the long plan:
Get a virtual machine running windows XP on the ubuntu server, map a network drive to a samba share of the photo archive, install windows media player 11 and tell it to share with the frame.


So, am I crazy?

---

### Post by RC Howe on 2008-01-01
Nope, there are people in the enterprise world that do stuff like that all day. Seems easy enough, you would just have to put the command in a startup script or a user script. Once you get everything working you can have it run in the background.

As to mapping network shares, I do not have much experience with that, but so long as Windows doesn't complain about it you should be fine. You may run into a little turbulance when you are getting the VM to talk to the frame, depending on the level of hardware support the VM has. I would advise that the first thing you do, before you go to the trouble of mapping a network drive, would be to make sure that the frame works with the VM, because networking to something external can be hard.

---

### Post by Mike'sHardLinux on 2008-01-01
In VMware Server and you can set the virtual machine to start up whenever the computer boots up.

---

### Post by markiep on 2008-01-19
If you make it work they will come:)

---

