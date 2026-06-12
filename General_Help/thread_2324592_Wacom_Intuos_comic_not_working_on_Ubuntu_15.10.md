---
title: "Wacom Intuos comic not working on Ubuntu 15.10"
date: 2016-05-15
forum: General Help
---

### Post by kevinamaya04 on 2016-05-15
Hello. So I bought this wacom comic tablet but I havent been able to make it work under Ubuntu 15.10. I have gone to the wiki forums on linuxwacom and I have downloaded the three main drivers they listed but I had no luck on this. The lsusb shows 

Bus 002 Device 008: ID 056a:033c Wacom Co., Ltd 

So I guess is being detected but It just doesn't wok. xsetwacom --list devices shows nothing at all and the wacom program says It's not connected. This is kind of weird since I have seen the Intuous comic being supported on the website of linuxwacom. So I wonder If anyone has gotten this tablet to work. Thank you very much

---

### Post by mörgæs on 2016-05-16
Hi, welcome to the fora.

Wacom drivers are in a fast development and I suggest that you try 16.04, at least in a live boot. 15.10 has only a few months of support left anyway so you will soon have to do a new install.

---

### Post by kevinamaya04 on 2016-05-26
I guess I'll have to work on windows for a while, already upgraded but didn't work :( that said if someone knows how can I help the wacom driver community i would want to know

---

### Post by mörgæs on 2016-05-27
Thanks for the offer. Please post the results from the command ```
uname -a
```

---

