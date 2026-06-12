---
title: "Xorg shoots cpu to 100%"
date: 2008-04-20
forum: General Help
---

### Post by TimPy on 2008-04-20
Although I've seen several threads like this one, none of them seem to answer my question well enough. They said to restart the desktop, or to change the desktop background, but it didn't work.

I have suffecient ram and cpu... (512 meg. ram and 1300 mhz cpu) but when I run top, Xorg takes up a majority of the cpu power.  My computer is currently not usable from Xorg eating up all my cpu power.  I have the latest (not beta release) of ubuntu. I'm running gnome, and when I tried to run xfce, gnome somehow decided it was going to run my desktop anyway.  

This is a really frustrating problem, as windows works, and linux doesn't.  Also, videos play fine in Xp, while they skip too much to enjoy in ubuntu.

Any help would be apreciated. I didn't see a more specific place to post this, but if there is I would like to know.

Thanks!

---

### Post by overdrank on 2008-04-20
> **TimPy said:**
> Although I've seen several threads like this one, none of them seem to answer my question well enough. They said to restart the desktop, or to change the desktop background, but it didn't work.

I have suffecient ram and cpu... (512 meg. ram and 1300 mhz cpu) but when I run top, Xorg takes up a majority of the cpu power.  My computer is currently not usable from Xorg eating up all my cpu power.  I have the latest (not beta release) of ubuntu. I'm running gnome, and when I tried to run xfce, gnome somehow decided it was going to run my desktop anyway.  

This is a really frustrating problem, as windows works, and linux doesn't.  Also, videos play fine in Xp, while they skip too much to enjoy in ubuntu.

Any help would be apreciated. I didn't see a more specific place to post this, but if there is I would like to know.

Thanks!

HI and what is the model of the graphics card and have you installed the drivers?

---

### Post by TimPy on 2008-04-20
I did not manually install my graphics card.  I had not been having previous trouble with Xorg. Right now, I can't even run top in ubuntu. I could possibly boot it with just the kernel, but I don't know how I can do that.  

So, to answer your question, I don't know what the model of my graphics card is, but I will look it up when I figure out how to boot without a desktop environment. Currently, I'm running this pc  (the one I'm having problems with) on XP.

---

### Post by TimPy on 2008-04-20
After searching a bit on windows, I've determined I have an 'Intel 82815 Graphics Controller'.

---

### Post by overdrank on 2008-04-20
> **TimPy said:**
> After searching a bit on windows, I've determined I have an 'Intel 82815 Graphics Controller'.

Ok I will assume that you are using gusty and the intel graphics will share the memory. You may search synaptic manager for the 915 resolution as it has helped me in the past. Also you may check your bios to adjust the amount of memory shared with the intel graphics.

---

### Post by TimPy on 2008-04-21
> **overdrank said:**
> Ok I will assume that you are using gusty and the intel graphics will share the memory. You may search synaptic manager for the 915 resolution as it has helped me in the past. Also you may check your bios to adjust the amount of memory shared with the intel graphics.

I managed to download 915resolution from synaptic, but I can't seem to figure out how to use it.  It seems odd that Xorg just *seemingly* randomly decided to take up 100% of my cpu whenever I do Anything. 915 resolution said that it was worthless with the latest Xorg. Thanks for the help though overdrank- any other help would be appreciated.

---

### Post by overdrank on 2008-04-21
> **TimPy said:**
> I managed to download 915resolution from synaptic, but I can't seem to figure out how to use it.  It seems odd that Xorg just *seemingly* randomly decided to take up 100% of my cpu whenever I do Anything. 915 resolution said that it was worthless with the latest Xorg. Thanks for the help though overdrank- any other help would be appreciated.

Ok, what version of ubuntu are you using? You can try and reconfigure you xorg with this command in the terminal
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
the terminal is located under applications, accessories.

---

### Post by TimPy on 2008-04-21
Hello again. Thanks for your help!  I'm going to leave this thread as unanswered, as it is, but when I booted ubuntu this latest time around, Miraculously, everything was fine.  My Cpu is back to normal, and Xorg is using a reasonable amount of Cpu. I can finally use Ubuntu,and I'm glad for now....

It's also very frustrating- fixing a problem even when you didn't do anything. If I ever run into this problem again, I'm definitely going to post here again.

Oh, and as a side note, I know where the terminal is. (I figured you were just predicting any questions, and that's fine, I just figured I should tell you I know what the terminal is.)

---

### Post by overdrank on 2008-04-22
> **TimPy said:**
> Hello again. Thanks for your help!  I'm going to leave this thread as unanswered, as it is, but when I booted ubuntu this latest time around, Miraculously, everything was fine.  My Cpu is back to normal, and Xorg is using a reasonable amount of Cpu. I can finally use Ubuntu,and I'm glad for now....

It's also very frustrating- fixing a problem even when you didn't do anything. If I ever run into this problem again, I'm definitely going to post here again.

Oh, and as a side note, I know where the terminal is. (I figured you were just predicting any questions, and that's fine, I just figured I should tell you I know what the terminal is.)

Hi and I meant no offense with the directions to the terminal. Some of the answer or advice given are generic and saved. Good luck!

---

