---
title: "asus G60VX + 16.04 help much needed."
date: 2016-08-21
forum: General Help
---

### Post by javan-cardillo on 2016-08-21
OK i will try to give as much info as i can so this be alittle long so try and stick with me. OK i have a asus g60vx as stated and have a Intel® Core™2 Duo CPU P7350 along with the NVIDIA®  GeForce® GTX 260M with 1GB GDDR3 VRAM. Heres where im at and stuck at, i have reformatted the hard drive and re installed 16.04 two times and get the same stuff showing up, along with not being able to run the driver for the nvidia even though i have downloaded it still dosnt work, i am not able to download anything from ubuntu software center, i am not able to download anything running the command lines, and i can not install any updates. I have included some screen shots of my terminal and some other stuff to maybe give you all some idea, my question i am i going to be able to get this to run right or will i need to downgrade my os to say 15 or 14, i do not have the money to buy a new laptop at this time or within afew years so im stuck with this old lady, i time i plan to put in a 3ghz intel and 8 gigs of ram, so shes gonna stay for like i said afew years till i have no choice but to replace her.

---

### Post by banceu_sergiu_ione on 2016-08-21
Are you try to update from a installer liveCD ?

Sorry I ask, but did you put out the installer CD after you had installed the OS?

Check in system settings /  software & updates / ubuntu software that source code download from main server and not from other as DVD/CD.

Then try run updater in terminal
```
 sudo  apt update 
```
```
 sudo  apt upgrade 
```

---

### Post by gordintoronto on 2016-08-21
In the images, there were suggestions of commands to run. Have you run them?

---

### Post by javan-cardillo on 2016-08-22
Yes I have tried to run the commands they suggest and sudo apt update and the same thing comes up something about i386, also here's some news 32bit 14 and this laptop do not like each other, I was running 64 bit 16, I'm gonna try 32 bit 16 today and see what that dose then I will try 15 if it still will not work for me

---

### Post by javan-cardillo on 2016-08-22
15.10 64 bit crashed, seems 14 and 15 have a video issue with this computers hardware, however i reinstalled 16 64 bit and ran the updates as it installed and for now it seems to be working, not sure how long it will last, but i am not happy with how ubuntu has become so bad. Heres hoping that 16.10 will be better.

---

