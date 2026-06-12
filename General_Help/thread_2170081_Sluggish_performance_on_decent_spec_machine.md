---
title: "Sluggish performance on decent spec machine"
date: 2013-08-24
forum: General Help
---

### Post by santahul on 2013-08-24
Hi guys

I'm new to the forum but have mucked about with Ubuntu in the past, never had any problems with it till now although don't mistake me for an experienced user.

I've just installed 13.04 on a decent machine but performance seems very poor. Any transitions/effects on the desktop are juddery and buggy, dragging windows round seem to lag a lot etc. Its also often freezing when trying to do these tasks. Usually the whole thing including mouse etc totally locks up but one time only it gave me an error message about the GPU although tbh I can't quite remember what it said. I don't have internet to the machine however and I don't have the hardware to hand to get it online I'm afraid.

Searching around t'internet suggested my nforce chip wasn't supported properly so I've spent the afternoon figuring out how to manually install the drivers but it's not really made any difference that I can tell although it hasn't crashed yet. FWIW I've tried 32 and 64 bit versions and the hard drive is encrypted.

Specs:
Intel Core 2 Duo E7300 (steady around 25 degrees)
Gigabyte GA-73PVM-S2H using onboard graphics (nforce 630i)
4GB RAM
120gb sata hard drive. Old but seems to check out.

Not sure what else to say but any suggestions would be very much appreciated. As mentioned I'm a Linux newbie but don't mind searching/learning if somebody can point me in the right direction.

Thanks,
Stephen

---

### Post by SweetAurora on 2013-08-24
So have you installed the nvidia graphics drivers yet?  
```
sudo apt-get install nvidia-current
```
But only run the command **IF **you didn't already install them manually. If you did install manually using the Nvidia provided driver on their site, uninstall the driver by doing "sudo ./whahtever.run --uninstall", then run the command.

---

### Post by SweetAurora on 2013-08-24
Also, to fix the Compiz screen tearing, you can also do this:
```
sudo apt-get install compizconfig-settings-manager
```
Then open it and disregard the warning. Do as I say, and no problems should arise. Just click on the "composite" settings and untick "detect fresh rate". Then close the app.
Now open the startup apps by searching the dash and open it. Click "add" button to the left and in the name and comments section, put wherever you want, the command section is what is immportant.

In the command section put:
```
sh -c "sleep 10 && dconf write /org/compiz/profiles/unity/plugins/composite/refresh-rate "60" &"
```
Click the "add" button and close out the windows. Now reboot.

---

