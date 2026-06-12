---
title: "My new Ubuntu built-in laptop keeps randomly shutting down"
date: 2017-01-31
forum: General Help
---

### Post by dontyoudare on 2017-01-31
I bought it in November to escape Windows's programmed obsolescence that had my stress levels going through the roof, and I find the new OS extremely beautiful and simple, but I'm already getting tired of all the nevereding issues that keep popping up on Ubuntu, which always have an easy solution on google where you just have to insert commands in Terminal that end up not solving anything, but I just can't ignore this one. My laptop ( [http://www.dell.com/br/p/inspiron-14-5452-laptop/pd](http://www.dell.com/br/p/inspiron-14-5452-laptop/pd) ) will randomly shut itself down (no, it's not the energy settings, they're all programmed for the computer to stay on regardless of the standby time). Sometimes it's when I Suspend it and close the lid, only to come back and realize it actually turned off (it still had plenty of battery), or other times I'm actually using it, and it will just turn off, with an audible sound that sounds like it's internal ventilators stopping, like a little turbine shutting down. Now, I googled my problem and the few cases that showed up didn''t matched my situation: a brand new computer that came with Ubuntu (not installed) and operates on Ubuntu only (no dual partition, which I guess it's something you can use to have Windows at the same time), so I created my account here to see if anyone could help me. I tried AskUbuntu once ( [http://askubuntu.com/questions/870872/volume-keys-on-dell-inspiron-are-not-working-14-04](http://askubuntu.com/questions/870872/volume-keys-on-dell-inspiron-are-not-working-14-04) ) but no one answered, so I'm not wasting my time and good faith there again.


Specs: [http://i.imgur.com/vAiEVUV.png](http://i.imgur.com/vAiEVUV.png)

---

### Post by QIII on 2017-01-31
Your description suggests a hardware thermal fault more than anything.  That would be the first place to start.  You might try buying a can of compressed air and directing a few short puffs through your fan inlet.  There are other things to try beyond that if there is no improvement.

As for your other little problems, I think you may have been trying random solutions from the web that were ill-advised from the start.  If you would care to ask for help here, you might do better.

---

### Post by dontyoudare on 2017-01-31
Thanks for your help. I actually already searched for a compressed air can once (to blow the dust off the keyboard and touchpad) but was unlucky to find anything in my town. You're saying all I should do is blow it in the sideways air exhaust? No need to disassemble some of it's components to blow the air can in it from the inside? Your help was fast and quick, so I guess I'll stick around some more for future problems, even though I've already grown used to a few of them. By the way, I've forgot to include this error report ( [http://imgur.com/a/SQtXm](http://imgur.com/a/SQtXm) ) that always shows up after turning the PC back on from a random shutdown. I hope this might help clear up what's happening.

---

### Post by QIII on 2017-01-31
Always shoot the compressed air in the normal direction of airflow.  If the side is the outlet, don't shoot air that way.  Always blow through the air intake.

Your images are interesting and may point to something else as the cause.  But first let's see if it's overheating.  If you can't find a can of compressed air (I don't know if an auto parts store in your locality might have it?), then  you can install lm-sensors to keep track of your CPU temperature as you work and watch to see if it approaches a critical level.

For lm-sensors, please take a look at [this]("https://help.ubuntu.com/community/SensorInstallHowto").  For your purposes, I don't know if running it from the terminal or adding a GUI monitor like psensor would be best.  You'll have to take a look and see what best suits your workflow.

Although random shutdowns can be caused by many things, the two most common are CPU overheating and power supply faults.  We can check the CPU temperature.  Power supply issues are devilishly tricky to work out sometimes.

---

