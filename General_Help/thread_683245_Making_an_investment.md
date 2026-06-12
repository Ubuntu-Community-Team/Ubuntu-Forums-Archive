---
title: "Making an investment"
date: 2008-01-30
forum: General Help
---

### Post by CorruptNoob on 2008-01-30
Hi, I'm going to buy a laptop with Ubuntu installed on it (or with intention of installing ubuntu on).

I'm moving from an XP based Acer Travelmate and XP based old AGP machine.

I'm from the UK, my eyes are set on the XPS M1330 on [www.dell.co.uk/ubuntu](www.dell.co.uk/ubuntu)

The reason I'm having to spend so much money is, the nice inspiron on [www.dell.com/ubuntu](www.dell.com/ubuntu) (US site) isn't on the UK site [www.dell.co.uk](www.dell.co.uk), instead, we have a much more retarded version of the inspiron laptop, and it's quite upsetting, so I'm splashing out for an XPS that seems the same on both sites.


I need to ask, am I making the right decision? It is going to replace BOTH my desktop (hooked to monitor dual screening) and my laptop, that's why I'm selling to stretch to £600 (I'm a poor student, seriously, my overdraft is paying for this) so I need to make the right decision.

Only game I want to play on it is World of Warcraft, and I've seen guides on that in the community bit I think, so I'll want some kind of decent graphics card.

Thing is, the upgrades for it using "customize" are expensive, how do you install ram on these XPS systems, does it involving unscrewing things and voiding warratny or what?


Is it wise to get a DELL laptop, or should I get a mac for same price and dual-boot ubuntu?

Does the Dell machine have decent drivers for all its hardware? Should I pay £60 more and get a certified Vista machine and download the ISO for Dell Ubuntu?

Are there any other UK available laptops with preinstalled ubuntu that beat the dells?



Really want to make the right decision, as it's an important one, and I'm not experienced enough to do it on my own.

All help appreciated.

---

### Post by Scarath on 2008-01-30
Personally  I think Dell machines suck, everyone i have come in contact with seems to have very low build quality. But thats just my opinion, many people are happy with them.

I am a student and I got a dirt cheap old IBM thinkpad (T40), gig of Ram, no graphics but then i hate compiz (if i want wobbly shiny tellytubby stuff i'd buy a mac). Works flawlessly with ubuntu and cost me a couple of hundred.

If u need to impress ur friends however I have installed ubuntu on a [Samsung R40]("http://www.notebookreview.com/default.asp?newsID=3216&review=Samsung+R40") which was fun (u need to do a txt install and get the restricted drivers before X will work because its got ATI). Compiz will work but u do have to mess around with it. The build quality is great and the screen is very high quality. Everything works on ubuntu (if u dont mind fiddling to get the graphics running), i think its about £450. 

thats all i can suggest from my limited experience of ubuntu + lappys :D

---

### Post by CorruptNoob on 2008-01-30
Nah I'm not looking to impress my friends, I want something solid and stable, I also want to be able to get a good 2 or 3 years warranty on it.

---

### Post by CorruptNoob on 2008-01-30
Help please!

---

### Post by applecookie on 2008-01-31
@Scarath

Hi. I have the same laptop (R40). How did you get your compiz work for you? I failed till now. I used the newest ati proprietary driver.

applecookie

---

### Post by Scarath on 2008-01-31
> **applecookie said:**
> @Scarath

Hi. I have the same laptop (R40). How did you get your compiz work for you? I failed till now. I used the newest ati proprietary driver.

applecookie

Ok heres what i did

1. download the drivers for your machine at the ati-driver homepage***
2. EITHER download [Envy]("http://albertomilone.com/nvidia_scripts1.html") and use it to install the ATI drivers OR uninstall proprietary drivers and shut down X (you may have to restart, if this is the case it will not restart X so just log in to the console and go to step 3.
3. Next run 

```
sudo sh ./whatever the ati drivers are called
``` 

4.restart X:

```
sudo startx
```

5. You may then have to reconfigure X to get your graphics working:

```
sudo dpkg-reconfigure xserver-xorg
```

Follow the steps and if in doubt choose 'vesa' (i think thats what its called) as the driver.

Thats how i got it running, like i said it was a bit of a trouble but not too bad, just be sure to back up xorg.conf before you do it.

I suggest using Envy but I havent tried it because it would not install on that machine (dependency trouble I didnt have time to work out) but most people on the forums say that Envy is the way to go.

***- When i upgraded the drivers to the newest ones they didnt work, could have been me, could have been the drivers, ATM i'm using the drivers from around June 2007 and they work.

---

### Post by CorruptNoob on 2008-01-31
Bump!

---

### Post by Scarath on 2008-01-31
see [this thread]("http://ubuntuforums.org/showthread.php?t=427464") for lappys that work with ubuntu

---

