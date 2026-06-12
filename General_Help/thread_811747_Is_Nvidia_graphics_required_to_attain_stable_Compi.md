---
title: "Is Nvidia graphics required to attain stable Compiz effects?"
date: 2008-05-29
forum: General Help
---

### Post by motin on 2008-05-29
I am an Intel 915GM user and have yet to experience any sort of stable Compiz usage. Having tried Xgl and Aixgl from when it was not even alpha, stability has increased over time, but it's not stable enough yet. Every 3-4 days of usage, X will restart in the middle of a busy work session making me loose time and money... I always try Compiz after each Ubuntu release in hopes that 6 months of development may have increased stability, but even with Hardy the same 3-4 day rule appears to be true. (I recall that Firefox 3 Beta + Google Spreadsheet + Compiz was a sure-to-crash combination for instance). 

I have also installed Ubuntu on two other computers, both using ATI cards which up until recently required Xgl which has been stable but requires a lot of CPU and what not. 

I have only heard good things about Nvidia+Compiz combination, so now when it's time to get a new laptop I am very interested in the very question that is in this threads topic: Is Nvidia graphics required to attain stable Compiz effects?

Thanks for any info!
Cheers

---

### Post by Malac on 2008-05-29
Intel, Intel, Intel.

---

### Post by collinp on 2008-05-29
Well, Nvidia cards are the best for linux because everyone seems to have problems with ati, in windows and linux. But, i use integrated graphics i810 and they are what you would call stable, but slow because of my computers age. Try updating your drivers.

---

### Post by collinp on 2008-05-29
I just read the "Blacklisted?" thread, your card is blacklisted and for some reason ubuntu un-blacklisted it. So do not expect stable performance with your graphics, that was the main reason it was blacklisted.

---

### Post by motin on 2008-05-29
> **Malac said:**
> Intel, Intel, Intel.

Read, read, read about my experiences with intel. Then motivate, motivate, motivate your reply, thanks.

---

### Post by motin on 2008-05-29
> **Hellow said:**
> Well, Nvidia cards are the best for linux because everyone seems to have problems with ati, in windows and linux. But, i use integrated graphics i810 and they are what you would call stable, but slow because of my computers age. Try updating your drivers.

With every Ubuntu release, the drivers usually gets updated (not?), so I regularly try newer drivers - however without success...

---

### Post by dlmoak on 2008-05-29
I have Intel® Graphics Media Accelerator 3100 on my motherboard and Compiz works great as is.

---

### Post by damansandhu on 2008-05-29
nvidia is best , intel integrated graphics have poor performance in everything.

---

### Post by collinp on 2008-05-29
As i said, the intel GMA 950, X3000, and X3100 are blacklisted, meaning they may or may not work with compiz fusion. If you experience poor performance or cannot use compiz-fusion, that is your problem. You should have known that you can have issues if you un-blacklist them.
EDIT: Here is the thread: [http://ubuntuforums.org/showthread.php?t=765875](http://ubuntuforums.org/showthread.php?t=765875)

"If you do this please do not post about any issues you have with stability or video playback problems, that's why your card was blacklisted in the first place."

---

### Post by motin on 2008-05-29
> **dlmoak said:**
> I have Intel® Graphics Media Accelerator 3100 on my motherboard and Compiz works great as is.

But this card is blacklisted... see below:

> **Hellow said:**
> As i said, the intel GMA 950, X3000, and X3100 are blacklisted, meaning they may or may not work with compiz fusion. If you experience poor performance or cannot use compiz-fusion, that is your problem. You should have known that you can have issues if you un-blacklist them.
EDIT: Here is the thread: [http://ubuntuforums.org/showthread.php?t=765875](http://ubuntuforums.org/showthread.php?t=765875)

"If you do this please do not post about any issues you have with stability or video playback problems, that's why your card was blacklisted in the first place."

I have an Intel 915GM card currently and looking for a new laptop. I guess your post was aimed at dlmoak?

Cheers

---

### Post by motin on 2008-05-29
> **damansandhu said:**
> nvidia is best , intel integrated graphics have poor performance in everything.

Can you work weeks and weeks and run 15-25 windows/applications simultaneously non-stop without X ever restarting with Nvidia graphics? That is exactly what I'm looking for!

---

### Post by RAOF on 2008-05-29
> **motin said:**
> Can you work weeks and weeks and run 15-25 windows/applications simultaneously non-stop without X ever restarting with Nvidia graphics? That is exactly what I'm looking for!

This depends.  In *my* experience what you get is whole-screen 'black flashes' every now and then, and the machine will totally freeze every now and then.  Compiz has moved a bunch of things which used to be corner-cases for drivers into the regularly-used path.  As such, pretty much all drivers have *some* sort of problems associated with it.

---

### Post by _DD_ on 2008-05-30
I much prefer nvidia when running linux, but the second hand laptop I just bought has an X1600 in it and that runs Compiz fine. I certainly wouldn't go for Intel though if you are definitely going to be using Compiz.

---

### Post by motin on 2008-06-27
With 2 weeks of experience of Compiz on my new laptop with Nvidia graphics I must say that it works very well indeed! I haven't had an X restart yet and can finally enjoy amusing and productive desktop effects!

Thanks all who gave me advice in this thread!

EDIT: DISASTER. As soon as I started to get back to work I found that the same issues with Compiz still remains! Have now reported these issues, which seem NOT to be a driver issue after all, to launchpad: [https://bugs.launchpad.net/compiz/+bug/243708](https://bugs.launchpad.net/compiz/+bug/243708)

---

### Post by motin on 2008-12-19
Update for Intrepid: I have evaluated compiz again, this time with but the minimal set of plugins and using the latest (177) ubuntu-provided nvidia binary driver. If I am lucky I can work in about 3-4 minutes before the screen gets all garbled up and I have to switch to and from a tty to get back to a normal appearance, a process that for some reason takes around 1-2 minutes. So, compiz is still a nono, and has alwaya been...

---

### Post by Kareeser on 2008-12-19
I don't understand peoples' insistence that "Intel is garbage".

Such blanket statements make no sense and sound quite immature. While specific cards may be blacklisted due to driver conflicts and such, my 855GM runs compiz perfectly, and never crashes under normal usage.

Running xrandr to switch resolutions... maybe... but that's sketchy to begin with.

---

