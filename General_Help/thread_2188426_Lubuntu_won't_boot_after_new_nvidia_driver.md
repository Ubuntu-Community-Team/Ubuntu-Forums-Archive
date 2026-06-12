---
title: "Lubuntu won't boot after new nvidia driver"
date: 2013-11-17
forum: General Help
---

### Post by wouter.inspired on 2013-11-17
Hi guys,
I am terribly new to linux based systems, but as a die hard XP user not willing to upgrade his gear yesterday I chose to give Lubuntu a try and I must say: I really love it!
With my 512 mbs of ram everything went smoothly (whereas in XP I spent most my time behind the pc waiting..)  but this morning suddenly a software updater popped up and gave me the choice between 2 nVidia drivers  (I have a Geforce 5200 FX)  one that just said Nvidia and xOrg something, and another one coming from  x.org or something called Nouveau.   Pardon if the names are a bit wrong, I can't see them anymore, that's why I'm writing you :)

So after installing I kept on browsing a bit till I shut down and 5 minutes later wanted to check 1 more thing. But now Lubuntu doesn't boot anymore!  Or well, it gets stuck on a black screen with just a tiny blue bar at the top (it seems its the exact blue colour of the login screen where you have the 5 dots)

Via this forum I found out how to access the safe mode, by holding shift when booting, and I've tried a few of the solutions posted here, but they seem to be for other problems so didn't work for me..  
Can someone help out a noobie? :D

Thanks a lot, I appreciate it.

---

### Post by fooman on 2013-11-17
hello,  i would try completely removing the nvidia drivers you installed by entering recovery mode again.  when you get there, choose the option that says "drop to a root shell prompt" (or something similar,  i may off a bit on the wording).  then type out the following:

```
 sudo apt-get remove --purge nvidia*
```

press enter and when it completes,  choose the option to continue with normal boot.  hope that helps

edit:  since you will already be in a "root" shell....you may not need the "sudo" part of the command....so if the command does not work try it without the "sudo" in front!  sorry :)

---

### Post by SeijiSensei on 2013-11-17
There are a number of postings concerning problems with support for the 5200 on 32-bit systems running 12.04 or later.  I recommend reading [this thread]("http://ubuntuforums.org/showthread.php?t=1986601") which might help.

Your video card is so old that using the proprietary driver may not be worth the trouble.  Just remove the nvidia driver, and let the machine revert to using the open-source "nouveau" driver.  What problems arise with that driver?  I'd also give some serious consideration to adding more memory.

---

### Post by wouter.inspired on 2013-11-18
Hi guys, thanks a lot for thinking along! 
Finally I could not make a lot of sense of the thread you recommended me SeijiSensei, concluding that the people there were experiencing different problems.  
Completely removing the nvidia drivers also didnt work, as it said that no nvidia drivers were installed -_-'  
So... finally Ive decided to re-install lubuntu 13.04 and thats from where Im typing right now.  Trying to stay away from the nvidia drivers!!!  My display is well right now, lets see how things evolve when trying to hook up my tv to the dvi port. 

anyway thanks for the help!

---

