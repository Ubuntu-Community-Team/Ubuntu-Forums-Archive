---
title: "Hardy 8.04 Upgrade on D620 Kills Video Resolution"
date: 2008-05-18
forum: General Help
---

### Post by paulnema on 2008-05-18
Took the plunge and upgrade to hardy 8.04 from my previous version of 7.10 (which was running GREAT).  Now my hardy version will not give me a resolution greater than 800X600 with a fixed refresh rate of 61 Hz.  

After enabling the restricted NVIDIA driver and rebooting I get an error msg stating "Ubuntu is running in low-graphics mode".  I go through the configure screens but cannot find the current driver. So, something is not healthily.

With 7.10 I was running a restricted driver from NVIDIA.

Some details:
Chip Set: 256MB NVIDIA Quadro NVS 110M TurboCache, Latitude D620
Dell: Latitude D620

Any help would greatly be appreciated.

Thanks

---

### Post by mano cazalet on 2008-05-18
:confused:

I use the very same notebook and card, and graphics is doing fine. 
I installed it with envy. Maybe you can set only the resolution in recovery mode, and then try installing the nvidia driver with envy (envyng from synaptic) see what happens.

---

### Post by paulnema on 2008-05-18
Downloaded envyng.  Great little tool but it did not solve the problem.  Maybe better to do a clean install instead of an upgrade...

Any other ideas?

Thanks

---

### Post by mano cazalet on 2008-05-18
do you have a backup of your gutsy's xorg.conf?
If everything is installed it should work with that.

Another option would be generating a new one with nvidia-settings

---

### Post by paulnema on 2008-05-18
Yes, previously tried copying a gutsy xorg.conf and rebooted.  Was given the "Ubuntu is running in low-graphics mode" message upon reboot :(

Not sure how to gen another version with nvidia-settings?  Can you point me to a thread/URL?

Thanks again

---

### Post by mano cazalet on 2008-05-18
```
sudo apt-get install nvidia-settings
```

after that nvidia settings is placed in system - administration 

and there is an option to edit the settings and generate or save it to xorg.conf

however i suspect this only works if nvidia drivers are installed correctly

---

### Post by paulnema on 2008-05-22
Closing this issue out
Seems this is a reoccurring issue...
My solution, back everything, fresh install of 8.04
All is well

---

