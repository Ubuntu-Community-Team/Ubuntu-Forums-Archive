---
title: "my last update on 16.04.2 never finished and now laptop Asus disfunctional"
date: 2018-01-12
forum: General Help
---

### Post by okkie2 on 2018-01-12
I am  lately afraid to do anything. I agreed to the update, computer restarts, Ubuntu pink screen, name UBUBTU, grey screen and I can hear computer working. Been a week  now, tried to reinstall 16.04 lts, no go. At least a reinstall should have worked but how do I format the laptop hard drive which is apparently necessary.Normally the install disk takes care of that.
All my everything is on a remote drive by luck so I can do anything needed to reload.  Help will be most appreciated. Over 70 might also come into play somewhere but here in Ubuntu country we keep trying. Thanks.

---

### Post by Autodave on 2018-01-12
You shouldn't need to do anything but put your install disk.thumb drive in, boot to it, choose to install, and finally when presented to the options screen choose to install using entire disk (erase ?buntu and install using entire disk).

---

### Post by okkie2 on 2018-01-18
Thanks and sorry for only coming back now Dave. I must travel far to get to a computer.
Ubuntu is loaded, boots to the pink screen, UBUBTU then grey screen but carries on with the update which takes for ever but is very very slowly making progress. Update screen only visible  very short while and i am too old now to read it.in all the years never seen before.I tried another disk, same result. when I post this I will download another Ubuntu on a memory stick, try that and give you feedback.   Enjoy!

---

### Post by okkie2 on 2018-01-18
Just noticed that I cannot get into bios either. Going to try a fresh install with memory stick and latest stable Ubuntu. Will give you feedback.

---

### Post by MgFrobozz on 2018-01-18
I had a problem in which I rebooted after a 16.04 lts update, and the system wouldn't boot with the default setting ("Ubuntu", 4.4.0-104-generic). I tried rebooting and using the previous setting, and it worked ok.

Finally noticed that /boot was missing initrd.img-4.4.0-104-generic, though /boot did contain abi-4.4.0-104-generic, config-4.4.0-104-generic, System.map-4.4.0-104-generic, and vmlinuz-4.4.0-104-generic. I regenerated initrd.img-4.4.0-104-generic, rebooted, then everything was ok.

---

### Post by okkie2 on 2018-01-25
ok gentlemen and ladies, I do not know what I have done other than downloaded the latest LTS and tried to boot it various times and suddenly it worked. Thanks.

---

### Post by okkie2 on 2018-01-25
thread closed

---

