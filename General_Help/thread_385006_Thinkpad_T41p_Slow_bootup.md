---
title: "Thinkpad T41p: Slow bootup"
date: 2007-03-15
forum: General Help
---

### Post by MrJavalava on 2007-03-15
After I upgraded Ubuntu directly from Dapper, I've had some problems getting the bootup to go quick.

I dunno where to begin to setup the startup more correctly. All I know is that it hangs somewhere around the hardware and kernel event manager (don't know how to really put it).
The Thinkpad takes 2 minutes to startup, at least because of it.

---

### Post by thesoothsayer on 2007-03-15
Not sure if this is the problem but one think that comes to my mind is whether your system is configured to use dhcp. If it is and it's not plugged in to the network at boot time, it probably waits for dhcp to time out before continuing.

Sorry if this is a red herring but it happened to me many years ago on a redhat system. :lolflag:

---

### Post by MrJavalava on 2007-03-15
how do I figure that out?

---

### Post by thesoothsayer on 2007-03-15
I'm in Xubuntu so I'm not exactly sure what the Gnome configuration for networking is called. But if you go into the networking settings, you should be able to see your interfaces.

See if any of them is set to DHCP. Try to change them to static first and reboot and see if you still get the slow boot time.

Another way to check is to view the /etc/network/interfaces file and see if there's anything like

> iface eth1 inet dhcp

If there is, you can comment the line out with a # in front.

Reboot and see if the slowness persists. If it does, well just restore the previous settings. :)

---

### Post by thesoothsayer on 2007-03-15
Oh yeah, have you tried removing the "quiet" option from grub during the boot-up?

1. Press escape to go into grub menu.
2. Go to the line of the kernel you want to boot and press e.
3. Press e again on the line with the "quiet" word.
4. Delete the quiet word and press enter.
5. Press b to boot up.

You should be able to see a list of what happens during the booting and which part slows down the boot process. I just tried it with an interface looking for a non-existent DHCP server and it was stuck at "Configuring network interfaces" or something similar for quite a while. You can take a look at which part slows down the booting.

---

