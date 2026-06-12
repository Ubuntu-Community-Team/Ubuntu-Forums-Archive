---
title: "Help with sound card and also"
date: 2007-02-22
forum: General Help
---

### Post by techwg on 2007-02-22
Hi, i have an m-audio revolution 5.1 sound card, and sometimes like on boot up the sound only comes from the right speaker, and what ever hapens i have no microphone ability. When i ran ubuntu in vmware i had "capture" and it actually worked, but now i am running in on my actual pc, it does not have a capture and has weird things and will not work.

I have onboard sound also that i am having trouble with, and with messing with it i have managed to freeze ubuntu totally about 5 times when running skype and connecting to someone. not all the time but 5 times at this point. I tried to install alsa, but it will not complete, i ./configure  and make and make install, but it fails on make install and also fails when i substitute make install for checkinstall.

I want to move away from microsoft as a primary OS, and move to edgy, but i need to get my card working so i can vmware my xp and chat away.

---

### Post by techwg on 2007-02-22
I take it there are people in this forum who have the answers to help lowely noobs /?

---

### Post by cronholio on 2007-02-22
Did you do "make install" or "sudo make install"?

---

### Post by renzokuken on 2007-02-22
do you have the build-essential package installed? 

if not run ```
sudo apt-get install build-essential
```

and try again

---

### Post by techwg on 2007-02-22
Hi yes i have essential, and yes i do sudo su
and i have something called checkinstall, which replaces the "make install" command so it makes a deb file and installs. But i did also try the make install.

This is the only real issue i have and i love ubuntu. My goal is to get my vmware XP to get voice so i can use my chat programs on XP and stick with ubuntu.

---

### Post by renzokuken on 2007-02-22
do you get any error messages during the make install process?

could you post them here?

---

### Post by techwg on 2007-02-22
i will do, i dual boot so i am in XP right now, but when i reboot later i will certainly find that info for you. But it was an attempt to get my linux not to crash, i swear from what people tell me i am the only guy to crash the damn thing !. Its supposed to be built like a tank , yet i have a nack of finding something and trashing it :)

---

### Post by renzokuken on 2007-02-22
i had the same problem when i started too, but fixing problems yourself and the great support from this forum made me learn loads in a short time.

with Linux, you quite literally learn from your mistakes till you indeed have a tank of an OS.

---

