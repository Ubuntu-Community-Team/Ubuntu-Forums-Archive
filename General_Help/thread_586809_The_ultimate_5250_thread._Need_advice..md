---
title: "The ultimate 5250 thread. Need advice."
date: 2007-10-22
forum: General Help
---

### Post by josys36 on 2007-10-22
Hello!

I have been using Ubuntu now for about a year and a half. Great product and I have just about made a complete switch to Ubuntu at home, but I have one application left over that I can't seem to find a good Linux equivalent. I work on the IBM System i. Therefore I need a good 5250 emulation product to work from. Right now I run IBM Personal Communications inside a VMWare XP system. what I would like to do is move away from the VM system since all I need it for is 5250. Here is what I have tried and has failed.

1. Wine - Wine would not let the IBM Personal Communications product install. The install would being, but then would fail about midway though with no explanation. I tried then to copy the files from a working windows install to wine folders, but the product still would not load. The initial screen would come up, but there were no sessions to choose from, and none of the buttons worked. I tried another 5250 product that worked in wine, but the fonts were so bad you could't use the product. In fact, only one font worked, and that looked like old english.

2. Linux products - I tried the other products out there like TN5250. Frankly I was very disappointed. Some of them look just plain ugly, and others didn't have full functionality. I even tried a commerical product from Power Term. The product looked ok, but the fonts in the 5250 screens were terrible. The company contacted me to see if I wanted to purchase the product. I said no since the fonts were ugly. From what I gathered this was the first time someone had tried to install the product on Ubuntu. Might even be the case for Debian.

3. I next tried the rdesktop route, but that wasn't great either. The window would load, but if I tried to make a window full screen it would do really funny things. For starters I could not close the window. I had to use the command window and do ctrl + c. Then I had to log back in the windows box and close the window from there. 

4. I tried IBM's CA for Linux product. For a company that pushes Linux so much they sure made a god awful product! It almost like fisher price like. The other problem with this product is that it is only good for 5250. Plus, you need to have CA installed on your System i for the product to work. Since I work at customers sites that don't have CA, this offers no solution. Also, since I need to work on System z machines I need 3270.

5. I have read every single post on 5250 on the forum.

6. Googled until I could't google no more!

Anyway, I can live with using a VMWare system for PCOMM, but thought I would give it one last shot to see if anyone has come up with a working solution, or may have a good idea that I can try. Since I have been trying to fix this for a year I am up to doing just about anything.

Thanks!

Jason

---

### Post by josys36 on 2007-10-22
Might try power term again and see if anything has improved.

Jason

---

### Post by josys36 on 2007-10-24
Bump

---

### Post by josys36 on 2007-11-27
Well I tried PowerTerm again and the fonts are still ugly. So I went back to doing some research and tried to load iSeries Access for Windows using Wine. Never did get a session to come up. After moving some .dll files to my wine install, the session manager would come up, but would not let me run a session. Produced a whole bunch of weird logging messages in my terminal. 

Still on the hunt.

Jason

---

### Post by Wd2048 on 2008-01-09
Have you tried Mocha? I work for an IBM shop, so I pretty much stick with iSeries Access (I hear ya, it's painful), but I know it's at least out there.  It's not the same as tn5250 in the repositories. Mochasoft only "officially" supports Redhat, but just alien the RPM and have a go at it.

---

### Post by josys36 on 2008-01-22
I never really liked Mocha either.

Jason

---

### Post by 3rods on 2008-02-01
I'm not really a fan of tn5250 either. If you step outside of the input area it hoses up. I still can't figure out how to get the offical package to work correctly (IBM). I installed the openmotif packages and used alien for the rpm from IBM, but alas, no love.

---

### Post by lawentzel on 2008-03-18
There is a Java version of the TN5250.  My biggest complaint about the tn5250 is I can not use the Shift Function keys.  Most of the work I do, I need them.  So needless to say it is very frustrating.  The Java version is called TN5250J.

---

### Post by lawentzel on 2008-03-18
Just found this thread which I have yet to try, but it looks hopeful.

[http://ubuntuforums.org/showthread.php?t=368894&highlight=tn5250]("http://ubuntuforums.org/showthread.php?t=368894&highlight=tn5250")

---

### Post by josys36 on 2008-04-07
Frankly I think the only real solution is to run XP and then install 5250 there. The linux options out there are just not ready yet. I know people say they are using them all the time, but they just look so awful I can't use them all day.

I guess System i access for Linux will just have to improve.

Jason

---

