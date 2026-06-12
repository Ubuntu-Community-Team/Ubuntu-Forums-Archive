---
title: "Looking for Graphic driver help"
date: 2012-12-25
forum: General Help
---

### Post by ilovepie on 2012-12-25
Hello,  im new to this forum and pretty green as far as Ubuntu goes. I loaded a 12.1 unto an old deskptop i dusted off in the basement for a little fun when i have time.  Mainly for multi media. Everything installed fine.  
However, my system was running _Really slow_.  I thought it was the memory. after checking requirements, i determined I was fine.  then i realized that my Graphics driver showed it was "unknown".  That led me to multiple web searches with no results.  
if i could get some guidance on how I can find out my specific graphics model, where to find a driver for it and how to install it I would be greatly appreciative.  
Here are my computer specs:

Dell Dimension E310-dv051
993.3 MiB
Intel Pentium 4 2.8 GH x 2
graphics-unknown


If I have missed this thread elsewhere I apologize in advance and would love a link to the solved thread.  

Thank You.

---

### Post by Cheesemill on 2012-12-25
To find the model of your graphics card open a terminal and paste the following command:
```
lspci | grep VGA
```Post the results back here.

(Don't worry about System Settings calling your graphics unknown, that happens even when the drivers are installed correctly).

---

### Post by ilovepie on 2012-12-25
nice, is there a glossary of terminal commands one could reference for these simple tasks?

00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)

So does this simply tell me the type of VGA or does this prove that it is in fact operating as normal?  I do not understand how the newest version of ubuntu can run so slow.?! it has to be something. if fixing the graphics doesnt do it im tempted to go back to 11 or 10 just so it functions at a tolerable speed.

---

### Post by Cheesemill on 2012-12-25
The correct driver for your Intel graphics is already installed and working as it should (it comes already built in to the system).

Your RAM is on the low side for running Ubuntu 12.10, you may want to consider installing Xubuntu or Lubuntu 12.04 instead as these are tailored for lower spec machines.

---

### Post by ilovepie on 2012-12-25
Or, I could throw in a new 4 gb chip in right? Would that be enuf? Or would it be better to go for 8 gb? I have 2 slots I believe. I originally threw in a new 512 gb a long time ago, plus the orig 256.  Is there a terminal command to see what type of chip i need to buy.   Ddr dimm, or just get a desktop chip? Just so I get the right kind? I honestly would rather spend $40 to upgrade the ram to prolong its life.

---

### Post by Kirk Schnable on 2012-12-25
> **ilovepie said:**
> nice, is there a glossary of terminal commands one could reference for these simple tasks?

I like the Unix Toolbox. 
[http://cb.vu/unixtoolbox.xhtml](http://cb.vu/unixtoolbox.xhtml)

---

### Post by Kirk Schnable on 2012-12-25
> **ilovepie said:**
> Or, I could throw in a new 4 gb chip in right? Would that be enuf? Or would it be better to go for 8 gb? I have 2 slots I believe. I originally threw in a new 512 gb a long time ago, plus the orig 256.  Is there a terminal command to see what type of chip i need to buy.   Ddr dimm, or just get a desktop chip? Just so I get the right kind? I honestly would rather spend $40 to upgrade the ram to prolong its life.

According to OK Memory, your computer won't support that. 

[http://www.okmemory.com/Dell-Dimension-E310_(DV051)-D13950-memory.html](http://www.okmemory.com/Dell-Dimension-E310_(DV051)-D13950-memory.html)

Maximum memory is 2GB, and each slot can only hold a 1GB stick.

---

### Post by ilovepie on 2012-12-25
OK so I have a few options.
1. Install xUbuntu, or lubuntu
2. Could I go back to 10 or 11 ?
3. Upgrade to two 1 gb sticks. Would 2 gb be enuf to run 12.1 effectively?
4.  Is there a fourth?

I don't know anything about Xubuntu  or Lubuntu. What's the diff? Benies? Downfalls?

---

### Post by seenthelite on 2012-12-25
> **ilovepie said:**
> OK so I have a few options.
1. Install xUbuntu, or lubuntu
2. Could I go back to 10 or 11 ?
3. Upgrade to two 1 gb sticks. Would 2 gb be enuf to run 12.1 effectively?
4.  Is there a fourth?

I don't know anything about Xubuntu  or Lubuntu. What's the diff? Benies? Downfalls?

I think option 3 is your best bet, I have an older Laptop with 2 GB and it runs very fast with 12.10 installed. If you upgrade the ram now you will get quite a few more years out of that computer running Ubuntu.

---

### Post by ilovepie on 2012-12-26
Thanks to everyone for their help.  im going to try upgrading the RAM first to see if that helps.  If not i can always go to a different version or just buy a new tower that is beefier.

---

