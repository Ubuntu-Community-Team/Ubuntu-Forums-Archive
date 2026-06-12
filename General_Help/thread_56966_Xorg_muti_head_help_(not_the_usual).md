---
title: "Xorg muti head help (not the usual)"
date: 2005-08-14
forum: General Help
---

### Post by kokiri on 2005-08-14
Ok... so I finally figured out how to get all my heads running in linux...
I've got a i855 on the mobo and I can't shut it off  :-|  so it's my number 1 card and the system really likes that card... I've got my nvidia running with twinview for my other two heads... now... here's the question... is there a way for xorg to completely ignore and not grab the i855 so that I can just have a tty1 window all the time with the other two doing xorg niftyness or is xorg just going to enjoy grabbing all my cards

Basically I'd like to have xorg be completely oblivious to the fact that the i855 exists and just use the 2 nvidia heads. The reason for this is all my boot messages and grub run on the i855, then xorg starts the nvidia fires up and activates the other two monitors and I have the i855 commented out so it sits there blacked out but no console because xorg is still grabbing the card but because it's not config'd it doesn't have a display.

So am I completely crazy or can this be done?

---

### Post by nad on 2005-08-14
If the i855 driver is not bound to any display in your xorg.conf, it is not being used. xorg is oblivious to this device.

The controlling terminal is using this display device. Try the key combination CTRL>ALT>F2 to see your console. ALT>F7 to get back to x.

---

