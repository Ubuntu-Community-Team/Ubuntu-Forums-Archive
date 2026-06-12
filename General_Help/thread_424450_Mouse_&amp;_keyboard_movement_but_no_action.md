---
title: "Mouse &amp; keyboard: movement but no action"
date: 2007-04-26
forum: General Help
---

### Post by parsim on 2007-04-26
I'm a Gentoo user of 3 years who made the switch to Feisty this week--so far I loooove it. Installing stuff and not waiting two hours for it to finish compiling; what a great idea. :)

But twice I've hit an odd problem, where suddenly it no longer cares what I do with the mouse and keyboard. It's not a freeze: I can still move the mouse around. But clicking and hovering does nothing, nor does hitting keys on the keyboard.

I can still see my system monitor ticking along, with no unusual activity. I can SSH into the box and everything looks fine. I tried killing Nautilus and the Gnome panel and watched these close and re-start on my monitor, just like they should, but I still couldn't get it to pay any attention to my keyboard and mouse.

I trawled through /var/log/messages, /var/log/X.org.log, and dmesg, but couldn't find anything suspicious. In the end I had to reboot.

Here's my mouse and keyboard:
```
$ lsusb
Bus 003 Device 002: ID 046d:c50e Logitech, Inc. MX-1000 Cordless Mouse Receiver
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 045e:00db Microsoft Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000
```

Next time this happens, what should I try?

---

### Post by parsim on 2007-09-25
I still hit this problem, once a month or so. Pretty weird.

I've found that if I ssh into the box and kill random apps, one of them will free everything up again. As soon as I kill it, all the keypresses that were doing nothing beforehand suddenly get recognized, as if they've been waiting in a buffer somewhere. EG if while the PC was in this unresponsive state I had pressed the volume up/down buttons, then once I kill the app responsible, the onscreen volume icon appears and the volume is modified. And everything works again.

So far Firefox tends to be the app I have to kill the most, followed by Rythmbox.

Still can't find any error messages anywhere.

---

