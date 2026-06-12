---
title: "Firefox keeps freezing"
date: 2008-06-12
forum: General Help
---

### Post by javi0084 on 2008-06-12
Firefox and my whole PC would freeze every once in a while when browsing the web, even on websites that supposedly don't have flash. I tried uninstalling and reinstalling flash but now Firefox will freeze and ask me if I want to force quit every time I visit any website with flash. I also tried uninstalling flash completely but that didn't work. GNASH didn't work either.

I am running Ubuntu 7.10, Firefox 2.0.0.14, GNOME 2.20.1, Kernel Linux 2.6.22-14-rt, AMD Athlon 64.

Any help is appreciated, this is really stressing me out :(

---

### Post by elord on 2008-06-12
Don't give up we have same problem i think it's normal for firefox to freezz

---

### Post by Rhubarb on 2008-06-12
I'm running Ubuntu 8.04 here, so I've got firefox 3 (rc1 afaik).
Firefox is running much more smoothly than firefox 2.0.x (on Ubuntu 7.10) ever did.

I have also got flashblock installed, which prevents any flash from running unless I click on it.

I'm not sure about the Ubuntu 7.10 repositories, but you should atleast try it out.
```
sudo aptitude install flashblock
```
Then just restart firefox.

Or, if you have time, I recommend you upgrade to Ubuntu 8.04.

---

### Post by Metaleks on 2008-06-12
> **elord said:**
> Don't give up we have same problem i think it's normal for firefox to freezz
Not to be rude, but please try not to post unless you have an idea as to what the solution is.  It's not normal for firefox to freeze.

As for the solution, please look at this thread:

[http://ubuntuforums.org/showthread.php?t=772490](http://ubuntuforums.org/showthread.php?t=772490)

It will solve the problem for you and get flash up and running with no problems.  Hope that helped!

---

### Post by talktoari on 2008-06-12
Me too. Recommend you to use Ubuntu 8.04. mine is working fine and no problem with firefox at all.

Ubuntu 8.04 comes pre-installed with Firefox 3 and hence it is well integrated. Also it comes pre-installed with Compiz-Fusion for good graphics effects.

My xperience is awesome with this and yours will also be the same.

---

### Post by kevdog on 2008-06-12
My firefox freezes too, however I dont think FF is the problem.  I think its the Hardy kernel.  I would upgrade to the latest kernel version to see if this helps you.  A lot of people are having problems with the kernel that was released with the default Heron release --- linus is too blame!

---

### Post by javi0084 on 2008-06-12
> **Metaleks said:**
> Not to be rude, but please try not to post unless you have an idea as to what the solution is.  It's not normal for firefox to freeze.

As for the solution, please look at this thread:

[http://ubuntuforums.org/showthread.php?t=772490](http://ubuntuforums.org/showthread.php?t=772490)

It will solve the problem for you and get flash up and running with no problems.  Hope that helped!

OK, I tried that (several times actually) but this time I made progress. Flash pages finish loading but FF tells me additional plug-ins are required. When I tried install Flash 9 it tells me the newest version is already installed.

---

### Post by javi0084 on 2008-06-12
Oh and I did upgrade to 8.04 but it was a major bust for me, I had to reinstall 7.10 then the FF problem started happening, it was working fine before though.

---

### Post by id1337x on 2008-06-12
What version of Firefox are you using?

---

### Post by aysiu on 2008-06-12
Close Firefox

Press Alt-F2

Paste in ```
firefox --profilemanager
```

Create a new profile and use it. See if you still experience freezes. Then report back here.

---

### Post by javi0084 on 2008-06-12
I'm using FF 2.0.0.14 and so far, no more freezing but also no flash. I try to install it and I'm told it's already installed, websites tell me I need to install it.

---

