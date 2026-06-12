---
title: "Scads of nautilus instances spawned when I connect my phone to usb"
date: 2020-06-27
forum: General Help
---

### Post by MgFrobozz on 2020-06-27
I'm running Ubuntu 18.04.4 LTS, and am trying to recharge my android phone (Samsung Galaxy J3 Prime, android 7.0) by plugging it into a USB port in the computer.

In the past, when I've done this, it pops up a dialog on the phone asking to share access to the phone. It usually takes me a second or two to respond, and during that time, 3-4 nautilus instances pop up on my desktop. I grant the access, then close the extra 2-3 instances of nautilus, then things are ok.

In the past week or so (since a software update), when I connect the phone, ubuntu spawns a lot of instances of nautilus, so many that the toolbar at the bottom of the screen is completely filled with nautilus icons, each about 5px wide. I try to grant access on my phone to stop that, and each time I grant it, another request for access pops up. I run a 'killall nautilus" to clear all of them, and then they rapidly pile up again. When this happens, I need to either recharge the phone elsewhere, or give up using the desktop.

Any suggestions on how to limit how many nautilus instances can be spawned? If there's a work-around that requires me to manually connect the desktop to the phone, I'm fine with that, but I'm getting tired of fighting ubuntu for control.

---

### Post by MgFrobozz on 2020-07-10
Here's a work-around (not a fix) for the problem:

```
[COLOR=#000000]gsettings set org.gnome.desktop.media-handling automount false
gsettings set org.gnome.desktop.media-handling automount-open false
[COLOR=#222222]
```[/COLOR]
[/COLOR]

Then manually mount the device if needed, or reverse the settings, authorize the mount, re-establish the settings, and then use 'killall nautilus' to get rid of the swarm.

---

