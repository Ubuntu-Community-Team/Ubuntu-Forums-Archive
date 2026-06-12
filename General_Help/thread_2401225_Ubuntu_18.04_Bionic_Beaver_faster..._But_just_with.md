---
title: "Ubuntu 18.04 Bionic Beaver faster... But just with Unity ?"
date: 2018-09-15
forum: General Help
---

### Post by misosofos on 2018-09-15
Hello everyone,

I was wondering If you could help to figure out what seems to me a complete mystery.

Several years ago I bought a Packard Bell EASYNOTE TE69KB-12502G50MNSK laptop. I regretted its purchase as it was slow under Windows or any Linux distribution than I tried...
I added a second 2 GB RAM module but things didn't get any better. Finally I installed the LXDE desktop environment which was functional but pretty limited. 

Yesterday I tried to upgrade my Ubuntu 16.04 installation to 18.04 version. Gnome 3 is the slowest desktop environment that I've ever run on this computer... But since I upgraded from Ubuntu 16.04 I tried Unity as it remained installed (it was really slow under the previous Ubuntu version.) Then I was nicely surprised: **Unity works really smooth and it's much faster under Ubuntu 18.04 than under Ubuntu 16.04 !!**

Anyone else noticed the same thing ? Could you help me to explain this curious phenomenon ?

Thank you in advance, guys !

---

### Post by Claus7 on 2018-09-15
Hello,

not sure if you can do anything special right now, yet a comparison at the same system with previous configurations, if you have any such messages recorded, might give you any clue; what I mean is that you could try the commands:
systemd-analyze blame
systemd-analyze time

to check your boot times and what is responsible that might slow you down. Now that you have updated though, you will be able to check your current boot times only.

Another thing that you could try is to open system monitor and check your memory consumption. You could also compare different memory usage by using different desktop environments: comparing plasma with your current configuration for example. These are all I can think of.

One additional aspect might be checking your system with a live cd/usb of your old versions yet:
it won't have the configurations you were having at that time and it won't be the same like an installation.

Regards!

---

### Post by misosofos on 2018-09-15
Thank you for your answer.

I will keep you informed.

---

### Post by speartip on 2018-09-15
Sounds to me like it's probably graphics related. What Graphics card are you using? 18.04 ships with newer drivers. Can't think of anything else that would cause the difference.

---

### Post by misosofos on 2018-09-15
It's AMD Radeon HD 8240... I tried proprietary drivers with no success.

---

### Post by speartip on 2018-09-15
That's probably the answer then. The open source drivers are newer in the later version. If you want to try a lighter weight gnome 3 distro, ubuntu budgie is a wonderful alternative. Looks good too.

---

