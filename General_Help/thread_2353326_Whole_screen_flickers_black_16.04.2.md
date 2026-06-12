---
title: "Whole screen flickers black 16.04.2"
date: 2017-02-20
forum: General Help
---

### Post by dlalonde2 on 2017-02-20
[COLOR=#111111][FONT=Ubuntu]This is a problem I feared would happen with time as kernel's got up in numbers as I've tried versions of Linux with 4.8.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]So I've installed Ubuntu 16.04.2. Once in a while, very randomly (using the backspace in terminal for example) my whole screen becomes black. It's very very annoying.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Before with Ubuntu 16.04.1, I didn't have that problem. I would update to Kernel 4.6 and install the Intel Graphics Update Tool and everything worked perfectly. Doing the same (without the Kernel update) on 16.04.2 does the same thing as other distros with Kernel 4.8 (or Ubuntu Gnome at 4.6).[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Is there anything I can do?[/FONT][/COLOR]

---

### Post by dlalonde2 on 2017-02-22
Surely I can't be the only one this happens to?

---

### Post by dlalonde2 on 2017-03-10
[COLOR=#333333][FONT=Ubuntu]I tried adding i915.enable_psr=0 and i915.enable_rc6=0 to GRUB to no avail. Can anyone help? Certainly I'm not the only one with this issue! On a LTS![/FONT][/COLOR]

---

### Post by dlalonde2 on 2017-03-13
Turns out it was the old stack for the X server that doesn't work. I'm not the only one with this problem. 

[COLOR=#111111][FONT=Ubuntu]The X server in 16.04.2 point release has been back-ported from 16.10. That must be why you're facing the same issue on both of them.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I had been experiencing a lot of random flickering as well, after the upgrade. Here's the help I got on AskUbuntu: [/FONT][/COLOR]
> [COLOR=#111111][FONT=Ubuntu]Removing the new X stack seems to have fixed it:[/FONT][/COLOR]

sudo apt remove xserver-xorg-core-hwe-16.04 xserver-xorg-input-all-hwe-16.04 linux-generic-hwe-16.04 xserver-xorg-video-all-hwe-16.04[COLOR=#111111][FONT=Ubuntu]However, ubuntu-dekstop will also be removed![/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]
So, you need to do the following straight away:[/FONT][/COLOR]

sudo apt install xserver-xorg-core

sudo apt install ubuntu-desktop xserver-xorg xserver-xorg-video-all xserver-xorg-input-all libgl1-mesa-dri libgl1-mesa-glx

[COLOR=#111111][FONT=Ubuntu][Source]("http://ubuntuhandbook.org/index.php/2017/02/install-remove-enablement-stacks-ubuntu-16-04/")[/FONT][/COLOR]


---

