---
title: "Double screen doesnt save settings"
date: 2017-02-03
forum: General Help
---

### Post by Dr_Lion on 2017-02-03
I have a laptop and an external monitor. Happens that i use the laptop on the right side of the external, and default is the external on the right. I go to system settings, and i choose to change the monitor position, i click apply, close, and reboot the pc. It reboots to the default and doesnt save my changes.

I'm using ubuntu 16.04 and at the moment um using gnome2 or classic without unity!

Does anyone know how to get this issue solved?

Thanks in advance.

---

### Post by DuckHook on 2017-02-04
It depends how finicky you want to get. The easy way is to download arandr, set up your configuration the way you like, export it using arandr and then save the resulting file to your ${HOME} directory as .xsession. The tiny drawback to this method is that the resulting ~/.xsession is local, must be reproduced for all users and doesn't load till *after* you log in, which means that your monitors will be flipped before lightdm logs you in. You can also create a xorg.conf file that loads earlier in the process to get rid of the flicker as your screens go through the reversal process. xorg.conf was deprecated a number of versions ago and won't even work from /etc/X11 anymore (new location: /usr/share/X11/) but it will still be read if it exists.

---

### Post by Dr_Lion on 2017-02-06
Ok, thanks for your help. I will try that and let you know if it worked.

It's weird that it doesnt work by default, as i thought it would, but as i know linux, it happens not to save some configurations many times without tweaks.

---

### Post by DuckHook on 2017-02-06
Ubuntu has changed rather dramatically at the system level over the last few releases. A lot of the old techniques that we relied on no longer work. I suspect that even the developers don't have everything really straight in their own minds yet. It's become a big and complex OS. If the .xsession method doesn't work for you, let us know. There are a few other techniques that still might.

---

### Post by DuckHook on 2017-02-06
> **Dr_Lion said:**
> …It's weird that it doesnt work by default… without tweaks.
> **DuckHook said:**
> …A lot of the old techniques that we relied on no longer work…
Further info: [https://bugs.launchpad.net/ubuntu/+source/unity-settings-daemon/+bug/1425000](https://bugs.launchpad.net/ubuntu/+source/unity-settings-daemon/+bug/1425000)

The developers don't seem to be in a big hurry to come up with a solution. In the meantime, we will have to make up a solution using a combination of arandr, shell scripts, .desktop files and the "Startup Applications" app. I used to know which folders would autostart scripts and applications. But with Xenial and the advent of systemd, most of those techniques don't work anymore and even the files and folders have disappeared. It can be very frustrating even for experienced users and outright intimidating for new users. Google is of limited help since all of the hits are for those old techniques that no longer work.

---

### Post by Dr_Lion on 2017-02-08
I tried what you said, but you didnt mention, to load the script you mean add it to startup applications?

I was searching through the ubuntu and the file you said ~/.config/monitors.xml has the right settings after reboot, so the problem that i see is that ubuntu isnt applying that config, or is but has something changing them after because i set a different (small) resolution to laptop screen and it doesnt take it into account. It keeps loading laptop screen with default resolution.  

But i decided to play with that monitors.xml file and i got something, i changed the primary monitor from laptop to external, and got the screen position right!!! It seems that ubuntu assumes the first screen to be the right positioned one. 

So now the only problem that i've got is keeping screen resolution!

---

