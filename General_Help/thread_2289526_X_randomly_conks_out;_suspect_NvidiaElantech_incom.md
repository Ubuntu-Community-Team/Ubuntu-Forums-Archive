---
title: "X randomly conks out; suspect Nvidia/Elantech incompatibility"
date: 2015-08-04
forum: General Help
---

### Post by ThatBum on 2015-08-04
Hiya. I recently acquired an Asus K52Jc (i5 M460, GeForce 310M, 4GB DDR3-1067, promptly put Xubuntu 14.04.2 LTS on it at the first opportunity :p).  It's been working great so far, but occasionally my X session freezes, though any audio continued to play normally. At first I REISUB'd my way out of it, but later I discovered I can fix it and save the session by going to a tty then back to X (Ctrl-Alt-F1, Ctrl-Alt-F7), and everything's still running when I get it back, even running 3D programs. As such this appears to be some sort of [GPU lockup]("https://wiki.ubuntu.com/X/Troubleshooting/Freeze").

I did some poking around and I found [this]("https://devtalk.nvidia.com/default/topic/766166/elantech-touchpad-related-nvidia-driver-freeze/"). I meet the hardware requirements for the bug, the workaround works, and the lockups seem to happen while using the cursor, though the probability of a freeze goes up with increased GPU activity. I also have a netbook with Xubuntu 14.04.2 LTS on it, with an Intel GPU and Elantech touchpad, and it does not have this problem. I believe this doesn't happen with the Nouveau driver, but I want to do some light gaming on this laptop, and the Nouveau driver is so slow it's unplayable. I'm using Nvidia driver 440.76, I can't use the most recent Nvidia driver because the 310M is classified as legacy.

I've tried [this]("https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1387428/comments/4") and [this]("https://bugs.launchpad.net/xorg-server/+bug/1220426/comments/18"), neither helped. Does anyone have a similar issue, and is there a fix? It would be nice if it was fixed upstream.

Attached are some log files I thought relevant. They were recently cleared and there's a couple of freeze events in them.

Thanks for your time.

---

### Post by ThatBum on 2015-08-05
Bump. I fixed the issue by installing xserver-xorg-lts-vivid, which upgraded Xorg to 1.17.1, but that created a bunch of other problems, borked ACPI and missing WiFi being among them (presumably because the respective modules from trusty's repos don't work with the 3.19 kernel). If there's no available workaround I suppose I'll just install Vivid as a stopgap until 16.04 comes out.

EDIT: Upgraded to Vivid, consider it solved. :/

---

