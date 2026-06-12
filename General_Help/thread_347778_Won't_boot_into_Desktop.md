---
title: "Won't boot into Desktop"
date: 2007-01-27
forum: General Help
---

### Post by ranxoren on 2007-01-27
Hi i'm a big noob when it comes to Linux
I installed ubuntu yesterday night and everything was working properly except the sound.
My soundcard would show with the aplay -l but i couldnt hear anything.
so i did the command that purges and reinstalls the packages or whatever its called (sorry lol).
On the tutorial it says after to reboot the computer so i did.
It does boot but then it just goes to a black screen like a Fullscreen terminal wich asks me for my login and password then goes into a terminal like mode.
Basically it doesnt load the user interface it stays in a fullscreen terminal mode.
I dont know what i did wrong i just followed the tutorial you can find here : 
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

And i stopped here :


Remove these packages sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils

Reinstall those same packages sudo apt-get install linux-sound-base alsa-base alsa-utils 

Reboot


Please help me ...
Thank you very much

O.T.

---

### Post by r4ik on 2007-01-27
Log in with you're username and password and do a,

sudo apt-get install gdm ubuntu-desktop

Please post back if it works.

---

### Post by ranxoren on 2007-01-27
im tryin this right now ill let you know in a sec

edit : ok so i did that now its back to terminal so i guess im going to restart my computer now and cross my fingers...

Computer restarting ...

YEEEEY WORKED THANKS SO MUCH FOR THE QUICK ANSWER/SOLVE :D

O.T.

Now lets see if my sound works ... NOP SOUND STILL NOT WORKING
ANYBODY HAS AN IDEA ABOUT THAT ?

O.T.

---

### Post by ranxoren on 2007-01-28
Nevermind i worked it out by searching on the forum and founding the "uncheck external amplifier" trick

Thanks

O.T.

---

### Post by r4ik on 2007-01-28
Had to get some sleep.
Got your sound working also ?
Perfect.
Anything else ?  :)

---

