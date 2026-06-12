---
title: "&quot;setsid unity&quot; BROKE Unity entirely"
date: 2015-03-27
forum: General Help
---

### Post by ArgentWarrior on 2015-03-27
I was told that running "setsid unity" from a terminal would restart Unity without the need to reboot. What it did instead is make Unity useless. When I log in, I get my wallpaper.That's it. No launcher, no panel -- nothing. And no, this is not a duplicate. I have tried the instructions for every thread pertaining to this issue and it didn't work. Is there anything I can do besides reinstalling Ubuntu? 

I've tried purging and reinstalling compz, unity, and everything else that makes Ubuntu what it is. I've run "dconf -f reset /org/compiz" more times than I can count.

I'm seriously about to sh*t-can Ubuntu altogether and just reinstall Windows. It's possibly the least efficient thing on the planet but I'm not putting hours on end into setting up Ubuntu all over again.

PS: Whoever said trying to restart Unity this way was a good idea, I hope you blow a PSU.

Ubuntu 14.04 x64, Intel HD3000 if it's relevant.

---

### Post by pmi2 on 2015-03-27
If you have not come across it, maybe this (?):

[http://www.techsupportforum.com/forums/f64/setsid-unity-command-errors-876177.html](http://www.techsupportforum.com/forums/f64/setsid-unity-command-errors-876177.html)

(scroll down to post #4 in that thread)

---

### Post by ArgentWarrior on 2015-03-27
> **pmi2 said:**
> If you have not come across it, maybe this (?):

[http://www.techsupportforum.com/forums/f64/setsid-unity-command-errors-876177.html](http://www.techsupportforum.com/forums/f64/setsid-unity-command-errors-876177.html)

(scroll down to post #4 in that thread)

Saw that one too. Didn't do anything. Thanks for the response though.
Now that my fit of rage is over, I'm just gonna reinstall Ubuntu and count this as a leaning experience. There's a few hours taken out of my day.
I still hope the person who suggested this blows an expensive PSU though.

---

### Post by pmi2 on 2015-03-27
Seems like that should not have "broken" Unity so completely.  
I got pretty lost just looking over some of the old posts on the subject...
:frown:

---

### Post by ian-weisser on 2015-03-27
What was the original problem you were trying to solve?

Are you saying that the original problem persisted across a reboot? Or that setsid persisted across a reboot? The latter seems quite unusual.

---

### Post by mc4man on 2015-03-27
setsid unity would not have broken anything & by itself doesn't fix anything. It'll just start the named program in a new session
Most likely you had/have  disabled the unity plugin or were using the wrong profile in compiz.  If you are in a session using the Default profile then you can run dconf reset -f  /org/compiz till the cows come home, it won't restore the unity profile.

---

### Post by CantankRus on 2015-03-27
Compiz is a bit flakey and I've had occasions where the setsid unity command fails to reload unity properly.
Running it does not mess anything up though and usually running the command again works. 
If all else is OK unity will load on next login anyway.
Why were you running setsid unity in the first place?

PS I try not to get angry at things I have a minimal knowledge of, because 
I may look like a fool down the track. ;)

---

