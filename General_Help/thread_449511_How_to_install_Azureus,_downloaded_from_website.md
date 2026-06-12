---
title: "How to install Azureus, downloaded from website?"
date: 2007-05-20
forum: General Help
---

### Post by _Pieter_ on 2007-05-20
Hey!

I've had some problems with Azureus, and looking at similar threads offered a good alternative to reinstalling Azureus via the repositories: just downloading the install file from the Azureus website. So I downloaded the .tar.bz2 package, saved it to my desktop, extracted the package, but now what? When I doubleclick on the Azureus executable, I get prompted whether I want to run it in a terminal, display its contents, or just run it. When I choose 'run', it does nothing. Running in terminal does not help either.. What do I do? I know that there are other torrent clients out there, but Bittorent does not allow simultaneuous downloads and BitTornado is a CPU-hog. Any suggestions? Thanks!

---

### Post by taurus on 2007-05-20
After you unpacked filename.tar.bz2, it will unpack it in azureus so you need to change to that directory and there will be a file called azureus.  That is the one that you run.  And before you do anything, make sure you have java installed on your machine first because without java, azureus will not run.

Applications -> Accessories -> Terminal
```
java -version
```

---

### Post by _Pieter_ on 2007-05-20
Hi,

I extracted the whole package to the desktop, but you're telling me that there is another directory called azureus? Where can I find it? I do have java installed, Azureus used to work just fine but one day it just starts shutting down seconds after I start it. 

Hope you can help me out!

ps: what's with the 'first cup of ubuntu' etc:D? How does one earn more cups?

---

### Post by taurus on 2007-05-20
Applications -> Accessories -> Terminal
```
cd ~/Desktop
ls -la
```

---

### Post by _Pieter_ on 2007-05-20
Dude.. as an Ubuntu forum staff member you should know that this does not make any sense to a newb like me.. :)
When I type this code in the terminal I get a nice overview of the items on my desktop, so what? My point is that the executable just doesn't run. When I run it in a terminal the terminal displays some text before closing down. 
And I DO have Java installed, Azureus used to work just fine. 
Any suggestions?

---

### Post by seamuso on 2007-05-20
I've always installed the dl version .. I assume you grabbed 2.5.04 ..

save the file in your home dir, not the desktop.

open a terminal and ..

cd

tar jxf Azureus_2.5.0.4_linux.tar.bz2

cd azureus

./azureus


see if it gives an error when it tries to run (java not found, etc). If you're trying to run it directly, it may be giving errors but you aren't seeing them. Post any errors .. if it used to work, but has stopped, you might have hosed up your .azureus dir .. 

again in the terminal 

mv ~/.azureus ~/.azureus_old

then try running azureus again.

---

