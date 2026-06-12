---
title: "Slow start up..."
date: 2004-11-08
forum: General Help
---

### Post by shad0w on 2004-11-08
"Configuring network interfaces" takes atleast 2 minutes on my machine. It also spits out eth1 -110 errors? Is that what's slowing it down? How can I speed it up? Will hoary speed up the boot process?

---

### Post by Rancoras on 2004-11-08
What network cards do you have?  Which one is on eth1?

---

### Post by shad0w on 2004-11-08
[QUOTE=Rancoras]What network cards do you have?  Which one is on eth1?[/QUOTE]
 I have a wireless lan card (Linksys 802.11b), but pcmcia always starts quickly with no problems. Those errors tend to come a bit later though, so I don't think they have much to do with it.

---

### Post by Rancoras on 2004-11-08
[QUOTE=shad0w]I have a wireless lan card (Linksys 802.11b), but pcmcia always starts quickly with no problems. Those errors tend to come a bit later though, so I don't think they have much to do with it.[/QUOTE]

Well, PCMCIA is not networking.  Have you followed the howto here?

[http://www.ubuntulinux.org/support/documentation/howto/helpcenterhowto.2004-10-07.3532963119](http://www.ubuntulinux.org/support/documentation/howto/helpcenterhowto.2004-10-07.3532963119)

---

### Post by khc on 2004-11-09
Try to do:
sudo ifdown eth1
sudo ifup eth1

And see if you need to wait for 2 minutes to get the 2nd one to finish.

---

