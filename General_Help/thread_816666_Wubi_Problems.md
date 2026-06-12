---
title: "Wubi Problems"
date: 2008-06-02
forum: General Help
---

### Post by infamous16 on 2008-06-02
Well, after having a bad experience with wubi (just improper installation and I think a full installation with a live cd will be better) I kinda need to get the windows boot thing back to normal. Since I tried twice there is two ubuntu things at the windows boot manager at start up, and windows vista.

How can I get rid of those two ubuntu things and make it so vista just starts up regularly again?

thanks!

---

### Post by jualin on 2008-06-02
From Windows, go to to Start, Run, and then type > msconfig. From there you should look for the "Boot" tab and just edit what you want from it. P.S. What was the bad experience about?, Maybe we can help you out.
*edit* In Vista just run a Live Search from the start menu of "msconfig" and then it will take you there.

---

### Post by infamous16 on 2008-06-02
Well, in that boot menu it didn't show ubuntu...but I could swear when I start up my computer it says windows boot manager...

and for the bad experience...i first installed the 32 bit version (i think) and second i installed the right version and such, and it installed correctly, and when I re-booted it just hangs up on the ubuntu loading screen, or it just goes black and doesnt even go to the loading screen.

edit: and I just fixed the startup thing with that easy bcd program or whatever....thanks to another thread.

So is my best bet just installing with a live disk, or should I re-install and see what happens?

and is there any other way I can install this without getting new blanks disks?

---

### Post by jualin on 2008-06-02
I would try it out first with a LiveCD, just make sure you know which version you need to download, 32 vs 64 bits. You should check if in any part of your computer you have some sticker that says 64 bits or something. Usually when it doesnt say anything is 32 bits and you should download the x86 version. 
About the installing without wasting a CD, I think there is a way but I have never tried it so I cant tell you about it. Sorry about that!. Post the question in a new thread and you will get an answer in a few minutes. 
Good luck!

---

### Post by infamous16 on 2008-06-03
Well, I am running 64bit vista right now...so I downloaded the iso of the 64 bit version, then I put it in the same folder as the wubi installer and it installed it and everything, it just wont boot into ubuntu after installation.

Maybe I'll try it again tonight.

---

### Post by jualin on 2008-06-03
When you start your computer do you have the Grub Menu (Where you can select which OS to boot,Windows or Ubuntu)? If you do you may want to try booting up with the FailSafe option which is usually the second one or the third one. Maybe that will give you an idea of the error that is keeping you from accessing Ubuntu. Maybe you can also add something to the boot line like "quiet splash" and maybe that will make the system boot.

---

### Post by infamous16 on 2008-06-03
I didn't have the grub menu, I had the windows boot manager...

I think I may get some blank disks tonight or something, then I can see if the live cd will work.

---

