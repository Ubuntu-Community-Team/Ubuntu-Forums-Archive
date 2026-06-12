---
title: "How to play a windows based game in Ubuntu 16.04 64bit"
date: 2016-10-02
forum: General Help
---

### Post by RJLiberator on 2016-10-02
Hi all.

I installed Ubuntu 16.04 version with 64 bit. 
I have a new NVIDIA GTX GPU that works great now but I feel has problems that I don't know about.

I want to play an old windows based game for free download called Red Alert 2.
It is a .exe file. 

I don't really know what the first thing to do is. I've tried looking into Wine but I get constant problems, I think, due to me using 64 bit and I can't use 32 bit. 

Any help / guidance is appreciated. I understand I did not give a thorough report of the problem as I am new to this.

---

### Post by RJLiberator on 2016-10-02
Okay, I think my error is "failed to load driver swrast"

---

### Post by Bucky Ball on 2016-10-02
.exe files are for Windows. Not Linux or Ubuntu. They will not run natively so don't bother trying.

The only way you are going to get that to work is by using WINE. [Check here]("https://www.winehq.org/") and see if your game will work with WINE.

Your other option is to install Virtualbox and run Windows as a virtual machine inside Ubuntu, then run the game on Windows there.

Bottom line: Ubuntu/Linux is not a drop in replacement for Windows. Windows programs are NOT going to run natively and forget .exe files unless you are using WINE or Win in a virtual machine.

As for your GPU, do you have the correct driver installed? Hard to know as you don't say what it is, but check in Additional Drivers. Anything enabled in there?

---

