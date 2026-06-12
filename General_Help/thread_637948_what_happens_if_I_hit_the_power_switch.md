---
title: "what happens if I hit the power switch?"
date: 2007-12-11
forum: General Help
---

### Post by lscritch on 2007-12-11
I have 7.10 server edition installed on a Dell server.

Normally it runs headless. But I reconfigured the network, so I needed to plug in a monitor and keyboard to get in.

I plugged them in, and got it connected to the network. I unplugged the keyboard and monitor. Then I remembered I still wouldn't be able to get in over the network, because I needed to disable DenyHosts.

But when I plugged the keyboard and monitor back in, the keyboard didn't respond (USB keyboard). I plugged it into a different port...then the monitor stopped working!

So now I'm locked out. I'm considering just hitting the power switch and rebooting that way.

But that's bad for Unix-like systems. I've seen it seriously bork a Sun box.

Can I just turn off the power to my Gutsy server?

---

### Post by evil316 on 2007-12-11
Seems you have no other option.  Really depends on what you have running when you shut it off but it should do a filesystem check upon reboot and work itself out.

---

### Post by lscritch on 2007-12-11
It's an apache/mysql/php server.

Here goes nothin'!

[later] It came up, it seems. And the first thing it said was Keyboard Error. A brand new keyboard too!

Time will tell if the database was corrupted.

---

### Post by dcstar on 2007-12-11
> **lscritch said:**
> I have 7.10 server edition installed on a Dell server.
.........
So now I'm locked out. I'm considering just hitting the power switch and rebooting that way.

But that's bad for Unix-like systems. I've seen it seriously bork a Sun box.

Can I just turn off the power to my Gutsy server?

One press of the Power button should start the shut-down process, holding it in will (after a few seconds) just cut the power off with the risk of filesystem corruption (although EXT3 is pretty good at insulating you from many problems).

You can experiment with just pressing the power button and then waiting for the shutdown sequence to run - then you can be confident that it will be ok to do it in the future.

---

