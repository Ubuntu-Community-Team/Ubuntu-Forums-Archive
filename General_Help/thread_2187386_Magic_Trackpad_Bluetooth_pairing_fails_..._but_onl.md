---
title: "Magic Trackpad Bluetooth pairing fails ... but only with Unity"
date: 2013-11-11
forum: General Help
---

### Post by jjramsey on 2013-11-11
I've been trying out live versions of the various versions of Ubuntu 13.10 on my mid 2010 Mac Mini, mainly to see what works and what doesn't. Now in *almost* all the versions of Ubuntu that I've tried, I can get the Magic Trackpad to pair. Usually, after I press the power button on the trackpad, a little dialog box comes up and prompts me to enter a PIN, which is '0000' in this case. Shortly after that, I can get the trackpad paired. This has worked with Lubuntu, Xubuntu, Kubuntu, and Ubuntu GNOME. In the case of the version of Ubuntu that uses the Unity desktop, however, I've had no joy. First, there isn't even a prompt for a PIN. If I go and use the "Setup a New Device" dialog for Bluetooth, an entry for my trackpad will intermittently appear and disappear from the list of available devices, and it never remains long enough for me to click on the "PIN options" button and choose the option that sends '0000' to the device to be paired.

Any idea what's going wrong?

---

### Post by snapstaldo on 2013-11-19
I am having what could be the same problem using ubuntu (I haven't tried out all the other variations to see if it works). What happens with you use ```
hcitool scan
```? I doesn't find anything for me but I was wondering whether you do?

I have actually had this keyboard and trackpad working in the past but in the process of fooling around trying to get another apple wireless keyboard and trackpad working at home I managed to break something, so that despite connecting when I first logged in it dropped out after a couple of minutes. So then I tried reinstalling bluetooth and now I can't get them to show up again when I do a scan (the trackpad popped up briefly but then I couldn't see it again). When I was first trying to get it to connect it was working better but the connection strength bars on the right of the blueman bluetooth manager kept on popping up and dropping out again very quickly. But after many attempts I could get it to pair (then some more fooling around to get it to keep the pairing in both OS X and Ubuntu simultaneously).

I would have thought it was a hardware problem but the keyboard and trackpad work fine with OS X. The only problem I have in mind is that by pairing it with OS X it seems to change the state of the keyboard so it no longer wants to pair. However, I have tried unpairing the keyboard and mouse and holding down the power button until it is forced to enter pairing mode again (blinking green light) but that doesn't seem to help.

My system is 13.10 and I now only have the following bluetooth packages installed: 


[LIST]
[*]bluez
[*]blueman
[*]libbluetooth3
[*]libgnome-bluetooth11
[/LIST]

I noticed that when attempting to 'complete removal'/'install' all my bluetooth packages that 'libbluetooth3' and 'libgnome-bluetooth11' were dependencies of the 'ubuntu-desktop', 'software-centre' and 'gnome-control-centre' and some other pretty serious sounding packages, so I decided against uninstalling them. Could the 'libgnome-bluetooth11' package be the source of the differences between your other distributions (although I would have thought it was in Ubuntu Gnome)?

---

