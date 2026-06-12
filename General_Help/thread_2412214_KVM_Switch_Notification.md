---
title: "KVM Switch Notification"
date: 2019-02-09
forum: General Help
---

### Post by Quarkrad on 2019-02-09
Running 18.04.  I use to have a kvm switch (startech) that had software installed on my win10 pc - for some unknown reason a notification appeared on my ubuntu pc when I booted (see attached top right of screen).  I no longer have the kvm switch but something in 'start up' launches this window/notification.  Any ideas on how to stop this window appearing (briefly - a few seconds) would be most appreciated.

---

### Post by TheFu on 2019-02-09
I'd check the automatic statup programs inside the DE you run.
I googled "ubuntu 18.04 startup applications" ...








[https://help.ubuntu.com/stable/ubuntu-help/startup-applications.html.en](https://help.ubuntu.com/stable/ubuntu-help/startup-applications.html.en) was returned.

---

### Post by Quarkrad on 2019-02-09
Yes - I've checked (Preferences/Start up Applications); nothing.  In fact, when the kvm switch was used/connected the Desktop would switch to the other pc(!).  I assumed when the ubuntu machine booted to the Desktop, not only was this notification window launched, but a signal was initiated to the kvm switch that caused it to switch leaving me with a blank screen. (I would have to manually switch the KVM back to the ubuntu machine.  (There was some Startech software on the win10 machine for the kvm that allowed hot keys to be configured - it is basic piece of kit: [www.startech.com/uk/Server-Management/KVM-Switches/2-Port-Mini-USB-KVM-Kit-with-Cables-and-Audio-Switching~SV211KUSB](www.startech.com/uk/Server-Management/KVM-Switches/2-Port-Mini-USB-KVM-Kit-with-Cables-and-Audio-Switching~SV211KUSB)).

---

### Post by Quarkrad on 2019-02-09
note:  Also unchecked a number of items in gnome-session-properties - window still launches.

---

### Post by TheFu on 2019-02-09
[https://www.startech.com/Server-Management/KVM-Switches/16-Port-1U-Rack-Mount-USB-KVM-Switch-with-OSD~SV1631DUSBU](https://www.startech.com/Server-Management/KVM-Switches/16-Port-1U-Rack-Mount-USB-KVM-Switch-with-OSD~SV1631DUSBU) this says there aren't any OS drivers and that the OSD is added by the switch.  I didn't see any software for the KVM linked above.  If the KVM isn't connected anymore, seems odd that any OSD would be displayed.  How could that happen?  Automatic if the GPU card sees a paused connection?

I don't have any answer.  My KVM doesn't do OSD, but it isn't startech.

---

