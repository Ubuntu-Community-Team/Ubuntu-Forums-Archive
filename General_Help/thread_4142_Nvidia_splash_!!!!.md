---
title: "Nvidia splash !!!!"
date: 2004-11-12
forum: General Help
---

### Post by Marauder1 on 2004-11-12
Anybody knows what line to put in XF86Config-4 so that
the nvidia splash screen wont show on startup or at a 
user change.

I know it a true or false variable but what is the name ?

TIA

---

### Post by Rancoras on 2004-11-12
I can't remember the setting, but I think it's listed in the readme for the nvidia driver.

---

### Post by neutron on 2004-11-12
[QUOTE=Marauder1]Anybody knows what line to put in XF86Config-4 so that
the nvidia splash screen wont show on startup or at a 
user change.

I know it a true or false variable but what is the name ?

TIA[/QUOTE]
 "NoLogo" "True"

put this into your XF86Config-4

---

### Post by Marauder1 on 2004-11-12
Thanks Neutron
Thats it, now my XF86Config-4 file looks like this :

...

Section "Device"
        Identifier      "NVIDIA Corporation NV20 [GeForce3 Ti 200]"
        Driver          "nvidia"
        Option          "NoLogo"                "True"
        BusID           "PCI:1:0:0"
EndSection

...

Under my device section, i insert it and i works !!!!

Ciao.

---

