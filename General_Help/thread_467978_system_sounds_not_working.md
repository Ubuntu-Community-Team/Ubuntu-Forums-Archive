---
title: "system sounds not working"
date: 2007-06-08
forum: General Help
---

### Post by ronbrooks on 2007-06-08
It seams that I can play sound file on the system but the system sounds will not work.  

I tried the test button on the sound folder and all I get is the pop up but no sound on the system.  I don't know what I can do to get it to work.  I don't know why the other sounds work and not the system sounds.  

Is there any help out there for this. By reading the threads in the forum it look like a lot of audio trouble is out there.   I am new to Ubuntu so I am now up to speed on all the things that need to be fixed.  Most everything works so I am happy about that but the sound thing I would like to fix.

---

### Post by crispy_420 on 2007-06-08
Do you have two sound cards? One onboard and a pci based one. I had these types of issues until I disabled the onboard via bios.

---

### Post by Crafty Kisses on 2007-06-08
> **crispy_420 said:**
> Do you have two sound cards? One onboard and a pci based one. I had these types of issues until I disabled the onboard via bios.

Yeah same here, and that solved the issue, try that.

---

### Post by ronbrooks on 2007-06-08
Yes I have a pci card via8237 so what you are saying is that I need to disable the on board audio.  How do I do that ?

---

### Post by crispy_420 on 2007-06-08
Check your bios options. How you get there is on boot. You'll be prompted to hit a key to enter the setup (examples are F2, Esc, Delete, etc.). Then browse around looking some thing like onboard devices or such. The bios is usually broken up in sections like Boot Order, Onboard devices, etc. Look for an option to disable sound. Save changes and exit. It will reboot and onboard sound should be gone.

---

### Post by ronbrooks on 2007-06-11
My misstake I only have an on board card for my audio.  I have sounds when I go on the web and when I play a sound in my system but the system sounds don't work.  when I test in the sound under the devices tap all work except sound capture.  When I go to the sound tab and hit play logout or login nothing happens.  So I am sure it is some kind of sitting that needs to be changed but I don't know what is it. 

Any help please.

---

