---
title: "Stuck at  &quot;Setting Bluetooth Servises&quot;"
date: 2007-10-02
forum: General Help
---

### Post by Beaster on 2007-10-02
Hello guys!

I am also new at this..
I downloaded wubi and selected Kubuntu and 10 GB of free space.I defragmented my hard drive and started the instalation..All was doing well until the point when the blue screen is gone and some services were starting and giving an OK at the right of the screen.When is trying to "Set Bluettoth Services" it does not give OK or anything else..It just wait there..

Any ides for this?

Thx guys!

---

### Post by ago on 2007-10-02
Press alt+f4 for a more verbose output. Make sure you have more than 256MB

---

### Post by Beaster on 2007-10-02
Thx for the quick reply! 
I did press ALT-F4 and it asked me for user and password..I entered them and i got to a Command Line Console(i think!).. What do i do from there?

Thx.

---

### Post by ago on 2007-10-02
> **Beaster said:**
> Thx for the quick reply! 
I did press ALT-F4 and it asked me for user and password..I entered them and i got to a Command Line Console(i think!).. What do i do from there?

Thx.

So the installation finished...

Then it might be that your video driver must be installed separately.

Have a look at /var/log/Xorg.0.log for driver errors

---

### Post by Beaster on 2007-10-02
ok this is what i did..
Entered user and pass and pressed enter

Then 2 times  "cd .."
Then "cd var"
"cd log"
"ls"

But there was no xorg.0.log   .

What should i do next?

Thx again..

EDIT

Is there a way to make kububtu not to start the bluetooth services..?I dont really need them..
Tried removing my bluetooth adaptor but the problem is still there.
Thx!

---

### Post by ago on 2007-10-02
Did it finish the installation or not?

You may disable that using update-rc.d (see man update-rc.d) the service in question is probably called bluetooth.

---

### Post by JimmyBEng on 2007-10-03
I was having the same issue, for now I have disabled the bluetooth services on startup.

Check out the following for help:
[https://help.ubuntu.com/community/UbuntuBootupHowto]("https://help.ubuntu.com/community/UbuntuBootupHowto")

---

### Post by ZenWarrior on 2007-10-04
I have a suggestion which mirrors what **ago** states in the Wubi docs. That is, first install ***only*** Ubuntu and then add any additional environments. In fact, should you install Ubuntu, no Bluetooth is installed whatsoever. Bluetooth is installed by default with Kubuntu, but not with Ubuntu. 

Maybe that'll help?

---

### Post by Beaster on 2007-10-06
Hey guys, i solved the problem by shutting down Windows and then starting up and booting Kubuntu,,
When i just press restart on Win XP ,kubuntu loads veru slow and always hangs there..

Thx for the help!

---

