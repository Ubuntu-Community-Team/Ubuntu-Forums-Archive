---
title: "The binary nVidia driver does not work in Feisty"
date: 2007-06-11
forum: General Help
---

### Post by Lakefall on 2007-06-11
I don't know where I should post this.

The proprietary nVidia driver in Feisty does not work. Well ok, it sort of works for few days or more, but then when you least expect it the system freezes and does not recover ruining my precious uptime. I have tweaked the system to fall into single user mode when the power button is pressed, but after a freeze it just leaves the screen black and does not seem to respond to keyboard input (limited testing). This kind of behavior makes the driver mostly unusable. I don't want the system to crash when I'm recording something I deem important from TV nor any other moment whatsoever. ;-)

The proprietary nVidia driver in Edgy didn't ever force me to reboot as far as I remember, but the proprietary nVidia drivers have never been problem free for me, so bugs like this do not surprise me. :-(

I'm using the AMD64 version. I'm just curious, does anyone else have exceptionally bad problems with the version of the proprietary nVidia driver in Feisty?

---

### Post by cantormath on 2007-06-11
> **Lakefall said:**
> I don't know where I should post this.

The proprietary nVidia driver in Feisty does not work. Well ok, it sort of works for few days or more, but then when you least expect it the system freezes and does not recover ruining my precious uptime. I have tweaked the system to fall into single user mode when the power button is pressed, but after a freeze it just leaves the screen black and does not seem to respond to keyboard input (limited testing). This kind of behavior makes the driver mostly unusable. I don't want the system to crash when I'm recording something I deem important from TV nor any other moment whatsoever. ;-)

The proprietary nVidia driver in Edgy didn't ever force me to reboot as far as I remember, but the proprietary nVidia drivers have never been problem free for me, so bugs like this do not surprise me. :-(

I'm using the AMD64 version. I'm just curious, does anyone else have exceptionally bad problems with the version of the proprietary nVidia driver in Feisty?

Well, they should work......Try downloading the drivers from the Nvidia website and installing them using their script, it really easy and does an awesome job, make sure you get the right drivers.................or, try using envy to install the drivers, google it....

---

### Post by Sockerdrickan on 2007-06-11
GET DRIVER

sudo apt-get install linux-headers-`uname -r` build-essential gcc gcc-3.4 xserver-xorg-dev

sudo apt-get --purge remove nvidia-glx nvidia-settings nvidia-kernel-common

sudo rm /etc/init.d/nvidia-*

CTRL+ALT+F6+LOG ON TO YOUR UBUNTU ACCOUNT

sudo /etc/init.d/gdm stop

sudo sh NV (PRESS TAB TO GET THE REST)

GO THROUGH THE INSTALL, JUST PRESS ENTER ALL THE TIME

sudo /etc/init.d/gdm start

---

### Post by Nythain on 2007-06-11
silly question but what version of  the driver are you running and what is your cards model

if you are experiencing problems with the 9755 consider switching back to the 9631 or whatever the previous one was...

i've seen many people having issues with the 9755 driver that were resolved by going back to old faithfull, hopefully it can fix your problems too

---

### Post by Lakefall on 2007-06-11
> **Nythain said:**
> silly question but what version of  the driver are you running and what is your cards model
My card is GeForce 6600 GT. I forgot to mention it. The driver is 9631 (nvidia-glx).

> if you are experiencing problems with the 9755 consider switching back to the 9631 or whatever the previous one was...
Actually, I hadn't looked and noticed there also seems to be nvidia-glx-new (9755). Maybe I'll try that.

> i've seen many people having issues with the 9755 driver that were resolved by going back to old faithfull, hopefully it can fix your problems too
That won't work. ;-)

---

### Post by Lakefall on 2007-07-03
Nope.. the hangs still happen with 9755. With both versions, when they do, the UI suddenly freezes followed by a quick black flash and stuff like this appears in kern.log:
> [369402.785022] NVRM: Xid (0005:00): 16, Head 00000000 Count 002ad525
[369406.780043] NVRM: Xid (0005:00): 16, Head 00000000 Count 002ad526
[369410.775059] NVRM: Xid (0005:00): 16, Head 00000000 Count 002ad527
[369414.770078] NVRM: Xid (0005:00): 16, Head 00000000 Count 002ad528
[369422.439107] NVRM: Xid (0005:00): 16, Head 00000000 Count 002ad529
[369424.436629] NVRM: Xid (0005:00): 8, Channel 00000000
[369430.429145] NVRM: Xid (0005:00): 16, Head 00000000 Count 002ad52a
[369432.426667] NVRM: Xid (0005:00): 8, Channel 0000001e
[369438.419182] NVRM: Xid (0005:00): 16, Head 00000000 Count 002ad52b
[369440.416702] NVRM: Xid (0005:00): 8, Channel 00000020
[369446.409219] NVRM: Xid (0005:00): 16, Head 00000000 Count 002ad52c
[369448.406740] NVRM: Xid (0005:00): 8, Channel 00000020
[369454.411235] NVRM: Xid (0005:00): 16, Head 00000000 Count 002ad52d
[369456.408757] NVRM: Xid (0005:00): 8, Channel 0000001e
[369462.405270] NVRM: Xid (0005:00): 16, Head 00000000 Count 002ad52e
[369464.402798] NVRM: Xid (0005:00): 8, Channel 00000020
Kernel logging (proc) stopped.
Kernel log daemon terminating.

I haven't yet tested the nv driver (which does not have 3D) quite long enough to be absolutely certain this doesn't happen with it, but I would be surprised if it does.

This seems to happen after a week of uptime or so.

---

