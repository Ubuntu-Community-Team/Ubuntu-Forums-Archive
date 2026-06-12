---
title: "Horrific Installation...Seeking Help"
date: 2008-07-04
forum: General Help
---

### Post by i-Set on 2008-07-04
ok i feel like crying right now, after recieving help from my previous thread, i decided to install ubuntu. i checked the integrity of the cd twice and everything was ok. i tried full guided install meaning that windows has now gone. half way through installation there was an error regarding my cd drives lens, i pressed ok. it restarted back to live cd. then tried installation again and the process kept stopping at 15%. 

pulled plug and now the cd doesnt start, even though its okay on bios. just tries to read cd and says press key to restart. my only theory now is that my cd drive is corrupt, should i try and buy an external cd drive and try again. and will the system bios pick up the external cd drive. 

im so confused note i am now replying through my ps3. please help

---

### Post by spiderbatdad on 2008-07-04
Unplug the power cord and remove any accessible battery. Wait about 30 minutes, and try to boot the cd again.

---

### Post by Gavla on 2008-07-04
Here's a real un-technical word, others may come on soon who know more:

I think I solved a similar problem at one point by putting windows back on just for long enough to be able to start installing my Linux again. Windows is a big bully which likes to overwrite GRUB and generally try and dominate as much of the drive as possible, and it kicks and stomps all the muck out of the pipes pipes. If you've got a Windows CD around, or perhaps the bootable Gparted Linux partition editor CD I had (This might have been what fixed mine after all, I can't remember), see if that'll at least get you back to being able to do something with your computer.

As for freezing at fifteen per cent, if the installer gets a little confused as to whether it is connected to the internet or not, it might get stuck at a certain point, although I think that point is generally much later than fifteen. I can't remember how I discovered and overcame this myself, but I think I read somewhere that you can completely unplug the modem so there's no doubt that this is an off line installation.

---

### Post by rokytnji on 2008-07-04
I would go into bios 1st and make sure you are booting from cd rom 1st before anything. Sounds like when you pulled the plug you probably changed boot order in your bios settings. Also if cd has any dirt or smudges or oil from fingers you'll get this kind of problem when going through install. Also I hope you did a md5sum check of you're iso before you burned it to cd.:D

---

### Post by hellmet on 2008-07-04
It could be a bad CD Drive. I had lots of such problems with Dapper Drake on many computers. On some things worked when I used a spare CD Drive.  
How about trying to install from a PenDrive?

---

### Post by rokytnji on 2008-07-04
Another thing I forgot to mention is if you have a Laser lens cleaner Like from Philips Laser Lens cleaner which is sold at Walmart for 5 or 6 bucks you probably need to run it through also before declaring cd drive dead.:)

---

### Post by mzhb@mac.com on 2008-07-04
Similar thing happened to me before. 
If your installation stops at some point, you just eject the CD out and insert again, normally your CD drive will keep working.

---

### Post by i-Set on 2008-07-04
right okay, update is that i have succesfully installed Ubuntu after a third time lucky spell. I have a question now

Back in windows on 256mb ram my pc was slow but after giving it a 1gb boost on virtual memory, firefox opens in 3 seconds. I just feel ubuntu is a bit slow so how do i increase the memory it can access, i heard there is a swap thing for ubuntu?

---

### Post by i-Set on 2008-07-04
and also addition to the above question, how do i enable mp3 playback? i have installed VLC media player for videos, so its all good. and again ubuntu is even slower than windows for me. so please advise how i can make it faster

---

### Post by i-Set on 2008-07-05
any help

---

### Post by bluepowder7 on 2008-07-05
which ubuntu did you install?

ubuntu 6.06?  ubuntu 7.10?  ubuntu 8.04?  or did you install xubuntu 8.04?  the "x" version is lighter weight and more friendly for low-ram computers.


how big is your swap partition?  if you go to system - admin - partition editor, it should spit out a picture of how your hard drive is arranged, so from there you can see how big swap is.

---

### Post by Doji on 2008-07-05
For mp3 playback install ubuntu-restricted-extras. You can do this simply by typing the following into a terminal.

```
sudo apt-get install ubuntu-restricted-extras
```

As for the speed, Ubuntu definitely should not be slower than windows. Due to your limited amount of ram, it might be worth looking at xubuntu. You might be able to switch to xubuntu without having to reinstall by installing xubuntu-desktop, but I'm not entirely sure and it would be worth having someone more knowledgeable help with that.

Edit: It might be necessary to install gparted in order to see the partition editor bluepowder7 mentioned.

```
sudo apt-get install gparted
```

---

