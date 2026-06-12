---
title: "Ubuntu is more quiet than Windows."
date: 2013-02-25
forum: General Help
---

### Post by vasilenko93 on 2013-02-25
I am trying out Ubuntu 12.10 64bit and I noticed that I have to slide the volume bar very far.

I don't have speaker, just headphones (headphones don't have volume control), and in Windows I only used two volume levels. For movies and TV shows I set it to 25%, and for everything else I set it to 10%.

But now in Ubuntu its much higher, not only do I not know the volume level right now (I must guess visually), but it tends to be higher. For everyday tasks it looks to be around 30%, and while watching movies around 50%. :mad:

Any thoughts, suggestions?

---

### Post by carl4926 on 2013-02-25
First thing is
Ubuntu is not windows
So don't expect it to be the same

The sound mixer will just need some getting familiar with. But control will depend on the Master Volume setting and then the volume slider setting for (in your case) the headphones.

---

### Post by debodas on 2013-02-25
Personally I don't see what the problem is? Most likely your master volume is lower than is was in Windows

---

### Post by deadflowr on 2013-02-25
If you click on the sound icon up on the panel, there should be a sound setting button area thingy, click on it and it'll open up the sound programmy thing. (sound is part of system setting;ie, gnome-control-center-unity, but programmy thing is easier to say)
From there you should be able to tell what the sound level is at and whether or not you can set headphones (amplified or non amplified).

---

### Post by GameX2 on 2013-02-25
Some music players, such as Clementine allow you to boost the player volume even higher - boost the volume of the player, than boost the volume of the player.

You might want to try it.

---

### Post by 3rdalbum on 2013-02-25
The drivers in Ubuntu are not the same as the drivers in Windows. Don't be surprised if the volume is a bit different.

You may be able to get more volume by turning up the PCM channel in Alsamixer (type "alsamixer" into the terminal). Just don't put the PCM channel above 90% or you will probably get distortion.

---

### Post by vasilenko93 on 2013-02-25
Thanks for the feedback.

---

### Post by JiuJitsu500 on 2013-02-25
type "alsamixer" into a terminal and make sure the master volume is all the way up too :)

It's normally what you set it up as anyway, but just to be sure... had a run-in with a strange sound issue not syncing about a year ago somehow, fixed it by maxing out alsa and un-muting the microphone...

---

