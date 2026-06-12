---
title: "Oh Ubuntu, why do you corrupt my DVD+RWs?"
date: 2007-08-29
forum: General Help
---

### Post by renatosilva on 2007-08-29
I've noticed that after few times re-writing Sony's high-quality DVD+RW media with the standard cd recorder of Ubuntu I get the DVD lost.

When I insert the disc on the drive the led blinks a little and then stop, like trying to mount and something wrong happening, although no message is displayed. Even #mount /dev/dvd /folder doesn't return anything, it keeps running fovever...

I'm totally frustated because I use DVDs for my backups, so that I just can't trust Ubuntu anymore to save my data, because suddently it destroy the media. 

I've ran some console tools that say something like the media is corrupted, but don't remeber the exact messages...sorry...

Pleeeeeeeeeeeaaasse help me before I install Windows!! :lolflag:

---

### Post by CowzRule on 2007-08-29
Instead of using the built in burning software (part of nautilus I believe), try Gnome Baker. It should be in the repos so ```
sudo apt-get install gnomebaker
``` should install it for you. I've used it with out any problems with both data CDs and DVDs.

---

### Post by renatosilva on 2007-08-30
I had problems with it too. Don't remember now, but after media is corrupted, I tried the DVD format option from Gnome Baker which doesn't work anyway...

Maybe starting to use Gnome Baker won't corrupt my DVDs anymore, but currently the problem is:

1) Oh Ubuntu, why do you have corrupted my DVD? What happened? :(

2) How to restore it! :confused:

---

### Post by tact on 2007-08-30
I had a lot of problems with every DVD burner I tried.  I just gave up on burning DVD's for a while.

Recently I followed another thread in these forums to install the latest Gutsy kernel in Feisty (or Edgy).

I did it not thinking at all about burning DVDs.   

The result is a few very welcome pleasures!   I can now burn DVD's perfectly every time - just right click on an ISO and select "write to disk" and it does!   No need even to bring up the cd burner application, any of them!  No more burning coasters for me!

Another benefit was that suspend/hibernate/resume all works where it would not with the standard Feisty kernel.

I am running the 2.6.22-10-generic kernel now.  

the thread is [here]("http://ubuntuforums.org/showthread.php?t=511974")

---

### Post by renatosilva on 2007-08-30
Do you mean that with the new kernel Ubuntu doesn't corrupt any DVDs anymore??

Didi you get the corrupted ones restored?

---

### Post by rbmorse on 2007-08-30
First, that "high quality" Sony media may not be all that high quality, after all.  I've had some terrible Sony branded stuff, including a 100 disc spindle of which very few discs were actually usable.   Look carefully at the label...it it says "Made in Taiwan" you do not have premium quality media.  The Sony discs labeled "Made in Japan" are premium quality, and sell at a higher price. 

You will enhance your chances of success, even with sub-standard media, by burning at a slower speed. Typically 4X or 8X will give best results. There is a point of diminishing return, however,  burning at slower that 4X probably won't do anything to improve your chance of success. 

The laser diodes in you burner degrade over time. If the unit is more than  a couple of years old it is suspect. Fortunately, new burners are commodity items (circa $30 USD) and easily replaced. 

I get best results using made in Japan 8X and 16X Verbatim and Taiyo Uden +RW media burning at 4X and 8X respectively.  

The worst discs I've seen were all labeled "Made in India" without regard to brand (probably all come from the same plant).  Malaysia, Singapore and Taiwan sourced media are better, but still inferior to Japanese production.    

You'll have to shop carefully as Japanese produced media are hard to find outside of Japan and Western Europe. Most retailers sell the cheaper media because it carries a higher markup. 

Lastly, media counterfeitting is not unknown.  Criminals concentrate on "name brands" like Sony, and they can be maddeningly difficult to spot until you try and use them. It's certainly possible your problem "Sony" discs could be counterfeit, particularly if all the "bad" ones are coming off the same spindle.

And that is probably more than you want to know.  Shop carefully, buners!

---

### Post by renatosilva on 2007-08-30
I understand what you said but not very well (bad English)...

But ok...maybe my Sony media isn't so "high" as I trusted...I'll verify it thanks...

---

### Post by rbmorse on 2007-08-31
Well, the big thing is to try buring at a slower speed and see if that helps.

---

### Post by CheeseEatingBulldog on 2007-08-31
> **rbmorse said:**
> Well, the big thing is to try buring at a slower speed and see if that helps.

I have read this so many times and can't help but sort of laugh. I have burned so much stuff over the years and never burned at a lower than my drive can burn speed. I have never had burn faults that weren't my own compilation of wrong media.

Seriously, burning at a lower speed makes no difference at all.

---

### Post by wirelessmonkey on 2007-08-31
> **CheeseEatingBulldog said:**
> I have read this so many times and can't help but sort of laugh. I have burned so much stuff over the years and never burned at a lower than my drive can burn speed. I have never had burn faults that weren't my own compilation of wrong media.

Seriously, burning at a lower speed makes no difference at all.

Sadly, I disagree with you.  I have had far too many disk burns that failed in one way or another due to write speed.  Typically the problem presents itself when attempting to use the burned media in another machine.  If you'd like to see this yourself, burn a disk for ubuntu-ppc at your max write speed, and try to use it in a G4 Mac.   The drives are so sensitive, any defect will prevent proper read functionality.

Admittedly, virtually every disk problem I've ever had has been noticeable only on ubuntu installs.  LiveCDs, Alternate install CDs, etc, that are burned higher than 4x (DVD) or 16x (cd), burned from ANY machine I've used (at least 10, probably many more) and attempted to install on ANY machine has these issues.

---

### Post by tszanon on 2007-08-31
RenatoSilva, try those Multilaser dvds. Here in Vitoria - ES there are plenty of them. I've been using them for a few months now and I haven't had any problems with them.

---

### Post by tact on 2007-08-31
> **renatosilva said:**
> Do you mean that with the new kernel Ubuntu doesn't corrupt any DVDs anymore??

Didi you get the corrupted ones restored?

Yes sir.  :)   Before the kernel upgrade, I burned 3 out of 4 - coasters.   Now - all good burns.

---

### Post by renatosilva on 2007-08-31
Ok guys, but does anyone know if there's a way to *recover* the lost DVDs? :)

---

### Post by tact on 2007-08-31
I could burn DVD no issue with earlier kernels.  But with the feisty kernels DVD burning was shot.  I thought my laptop internal DVD burner was going flakey but even an external USB burner would not do reliable DVD burns.   CD's no problem.  Just DVD a problem.

With the later (Gutsy) kernels - its back to the good old days.  No failed DVD burns

---

### Post by renatosilva on 2007-08-31
Ok tact, but did you use that Taiwan media? Could you read the lost DVDs again onto the new kernel? Does this mean that the new kernel can deal better with bad media? :D

Isn't true that DVD in fact is a much more sensible media than CD?

> **tszanon said:**
> RenatoSilva, try those Multilaser dvds. Here in Vitoria - ES there are plenty of them. I've been using them for a few months now and I haven't had any problems with them.

Hello capixaba! What is multilaser DVDs?

---

### Post by stchman on 2007-08-31
> **renatosilva said:**
> I've noticed that after few times re-writing Sony's high-quality DVD+RW media with the standard cd recorder of Ubuntu I get the DVD lost.

When I insert the disc on the drive the led blinks a little and then stop, like trying to mount and something wrong happening, although no message is displayed. Even #mount /dev/dvd /folder doesn't return anything, it keeps running fovever...

I'm totally frustated because I use DVDs for my backups, so that I just can't trust Ubuntu anymore to save my data, because suddently it destroy the media. 

I've ran some console tools that say something like the media is corrupted, but don't remeber the exact messages...sorry...

Pleeeeeeeeeeeaaasse help me before I install Windows!! :lolflag:

I use K3B for all my burning duties and it works great.  K3B is like the Nero for Linux.

```
sudo apt-get install k3b libk3b2-mp3
```

This will install K3B and the mp3 plugin.

---

### Post by tact on 2007-08-31
> **renatosilva said:**
> Ok tact, but did you use that Taiwan media? Could you read the lost DVDs again onto the new kernel? Does this mean that the new kernel can deal better with bad media? :D


*grin*  I doubt the new kernel can do miracles with bad media.   

Bad media wasnt the problem I had with burning DVD's using the standard Feisty kernel.  There was definitely something wrong with that kernel and my hardware (and others from some other threads).

I rarely burn DVD's but before Feisty the few times I tried DVD's just burned fine.  

With Feisty - I tried k3b and gnomebaker, and every other burning software but none would work for me, and I tried several different kinds of DVD media too.  All the tests resulted in a LOT of shiny new drink coasters!  hehehe

With Feisty (but using the Gutsy kernel) - I am back to where I was before, happily able to burn DVD's again.

---

### Post by tszanon on 2007-08-31
> **renatosilva said:**
> Hello capixaba! What is multilaser DVDs?
"Multilaser" is its brand.

Multilaser é uma marca que eu achei que fosse porcaria...mas comprei assim mesmo, não tinha mais nada disponível. Não me arrependo. Uso quase todo dia, formatando, regravando, numa boa.

---

### Post by renatosilva on 2007-08-31
> **tszanon said:**
> "Multilaser" is its brand.

Multilaser é uma marca que eu achei que fosse porcaria...mas comprei assim mesmo, não tinha mais nada disponível. Não me arrependo. Uso quase todo dia, formatando, regravando, numa boa.

Uuhauhahuauaauhah thanks...

---

### Post by renatosilva on 2007-09-03
Hey guys, last night I used a Maxwell DVD-RW (from Taiwan) to burn an APTonCD a few times and it has worked fine...

---

### Post by tszanon on 2007-09-03
> **renatosilva said:**
> Hey guys, last night I used a Maxwell DVD-RW (from Taiwan) to burn an APTonCD a few times and it has worked fine...
Good to know that the problem was caused by bad media.

---

### Post by renatosilva on 2007-09-03
And I can't believe that :???:...

---

