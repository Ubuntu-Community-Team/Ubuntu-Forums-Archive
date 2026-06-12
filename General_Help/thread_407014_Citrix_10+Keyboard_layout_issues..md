---
title: "Citrix 10+Keyboard layout issues."
date: 2007-04-11
forum: General Help
---

### Post by jungleb on 2007-04-11
Hi Guys ... I've successfully installed citrix10 ... I run the script provided by Diego Torres Milano ... 

Everytime I need to open a citrix session, I've to run in terminal "xset fp rehash"

What really concerns me ... is that the citrix keyboard layout differs from what i have in ubuntu...

In ubuntu i use the latin american layout ... but for some reason ... In citrix I don't have characters like @, |, - ... 

I don't even know which file should I tweak ... or what ...

Can you guys help me troubleshoot this?

Thanks in advance!

---

### Post by dtmilano on 2007-04-12
Running the latest version of the citrix-icaclient-10-ubuntu script ([http://codtech.com/downloads/citrix-icaclient-10-ubuntu](http://codtech.com/downloads/citrix-icaclient-10-ubuntu)) turns unnecesary to issue the "xset fp rehash" manualy everitime.

See the screenshot attached, may help with your keyboard problem (wfcmrg->Tools->Settings->Preferences)

---

### Post by jungleb on 2007-04-12
Thanks bro!
Both things solved the issue ...

I've selected Latin American layout in Tools->Settings->Preferences section.

Thanks for your time and help!

Fernando.

---

