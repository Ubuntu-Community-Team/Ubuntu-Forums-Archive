---
title: "KVM Switch"
date: 2018-06-08
forum: General Help
---

### Post by Quarkrad on 2018-06-08
I have 2 port startech kvm switch connecting two machines.  One pc dual boots with win10 and I installed a piece of software for the switch on the win10 side - it just seems to configure hotkeys.  On the other pc, which just has ubuntu installed, something strange happens.  When I had 16.04 installed, just as the Desktop launched a message would appear top right of the screen saying Switching KVM input. This intrigued me as  Ubuntu obviously recognised the startech switch connected to a usb port.  The problem is - as the Desktop launches the kvm switches to the other pc. I have to manually press the relevant button on the kvm switch to switch back.  It seems to me as if ubuntu is telling the startech to switch.  Ubuntu is obviously recognising the switch and puts a message on the screen that it is changing input - is there a way I can access something(?) to stop this changing input? (I've just clean upgraded to 18.04 and exactly the same thing is happening).

---

### Post by TheFu on 2018-06-13
I wouldn't assume Ubuntu knows anything. The KVM has smarts inside to recognize changes and I strongly suspect that is what brings the OSD up.  I would find the manual for the KVM and read it for how to make it do what you want.

I've had a few KVMs over the decades.  Never installed any software on any computers to use them.

---

