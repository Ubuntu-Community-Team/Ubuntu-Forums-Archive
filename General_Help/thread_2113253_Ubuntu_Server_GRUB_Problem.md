---
title: "Ubuntu Server GRUB Problem"
date: 2013-02-06
forum: General Help
---

### Post by yellowcrash10 on 2013-02-06
Hello! I'm having a very strange problem with my server.

When I turn on the server, the GRUB shows up. It never showed up before. This is a problem because I don't have a monitor for my server, to cut down on space. Instead, I hook it up to my TV so I can see what the problem is.

I think this started happening after there was a power outage. After that, I turned on the server, and then it was working fine until I accidentally bumped into the power strip 30 seconds later. When I turned it back on, I tried to ssh into it, and it couldn't connect. I went and plugged my server into my TV, and then the GRUB shows up with no timeout.

Is there a way to fix this?

---

### Post by papibe on 2013-02-06
Hi yellowcrash10.

I've experienced similar problems before. Here are a few thoughts:
[LIST]
[*]Believe or not, sometimes the lack of a keyboard produce more booting problems in regular headless desktops.
[*]Check your BIOS for something like 'Server operation' or 'Keyboardless operation'.
[*]Another source of problem could be the network boot (PXE). Disable it on the BIOS.
[/LIST]In rare occasions, as the one you described, I had to connect a monitor and press enter manually. This is what I've done to get it to boot automatically again:
[LIST]
[*]Connect a monitor, select correct kernel, boot normally and reboot.
[*]If that doesn't work, I boot into recovery mode and check the disks.
[*]In case that fails also, upgrade grub by doing:
```
sudo update-grub
```
and restart.
[/LIST]
I hope this ideas help you. Let us know how it goes.
Regards.

---

### Post by yellowcrash10 on 2013-02-24
> **papibe said:**
> 
[LIST]
[*]Connect a monitor, select correct kernel, boot normally and reboot.
[/LIST]


Thanks! I just had to wait for it to wait for the network configuration before restarting it :D

---

