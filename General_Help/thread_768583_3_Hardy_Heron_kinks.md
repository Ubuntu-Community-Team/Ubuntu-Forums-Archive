---
title: "3 Hardy Heron kinks"
date: 2008-04-26
forum: General Help
---

### Post by Stealth on 2008-04-26
1. Firefox is constantly hanging and freezing while I do any quick browsing. I've noticed with my little System Monitor app in the top bar, every time it does, there's a spike of hard drive activity for a few seconds. What is this, and how do I stop it?

2. Compiz won't start on boot. I have it in my sessions as "compiz &" but it never stars up on log in.

3. Compiz has pink shadows. I've read this is a bug with the 8000 series for Nvidia. Anyone have a solution?

---

### Post by autocrosser on 2008-04-26
As far as #2 look in synaptic for "Fusion-Icon". It will install a easy way to start/stop Compiz.

Several people have reported problems with FireFox B5--All I can say is to wait until the final release---there were several heated posts about including a beta of FireFox in Hardy--but with FireFox 2 loosing most support when 3 is finaled----you can see why Fox 3 is on.

Not sure about the shadows--have you installed Emerald? It might be a compiz vs Metacity issue.....

---

### Post by FuturePilot on 2008-04-26
Yes, the Compiz shadow problem only effects the 8 series cards. A workaround for the issue was discovered minutes ago.
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/194851/comments/37]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/194851/comments/37")

This should fix it.
```
sudo mv /usr/lib/xorg/modules/libwfb.so /usr/lib/xorg/modules/libwfb.so_bak
```
```
sudo ln -s /usr/lib/nvidia/libwfb.so.xserver-xorg-core /usr/lib/xorg/modules/libwfb.so
```
Logout and log back in, should be working.

As for the Firefox issue, it's a known issue.
[http://ubuntuforums.org/showthread.php?t=759673]("http://ubuntuforums.org/showthread.php?t=759673")

[Bug report]("https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/215728")

[Upstream bug report]("https://bugzilla.mozilla.org/show_bug.cgi?id=430530")

---

### Post by chrisccoulson on 2008-04-26
-

---

### Post by ibuclaw on 2008-04-26
Ace, Pink Shadows! How do you get them? (Mine are currently yellow)

It would be an awesome screenshot for the OMG PINK PONIES forum.:popcorn:

But on the question on compiz.
Have you tried using the proper command?:
```
compiz --replace &
```

I put it in my "/etc/gdm/Init/Default" file.
As a result, gdm takes a little longer to load, but the login is quicker.

Regards
Iain

---

### Post by Stealth on 2008-04-26
Thanks for the help. I was able to fix all 3 problems :D

1. I uninstalled Swiftfox and went back to the stock FF, so far it hasn't given me any problems.

2 and 3. I had to uninstall all NVidia stuff, reinstall from the official driver script, and no more pink shadows. From there I just used the Appearance option to enable the Desktop Effects, and now it starts on boot. :)

---

