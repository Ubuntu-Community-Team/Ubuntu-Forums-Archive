---
title: "Advantages/Disadvantages Of Preload?"
date: 2008-02-25
forum: General Help
---

### Post by solarwind on 2008-02-25
Should I install preload? What are the advantages and disadvantages?

---

### Post by SOULRiDER on 2008-02-25
I was wondering about the disadvantages mostly. I saw an article on Digg that talked aobut the advantages (faster speeds etc) but i was wodnering aobut the downside.

---

### Post by solarwind on 2008-02-25
> **SOULRiDER said:**
> I was wondering about the disadvantages mostly. I saw an article on Digg that talked aobut the advantages (faster speeds etc) but i was wodnering aobut the downside.

Yeah, the [article]("http://digg.com/linux_unix/Drastically_Speed_up_your_Linux_System_with_Preload") on digg sparked my interest. However, after reading the second comment, I decided to post this thread.

---

### Post by AlanR8 on 2008-02-25
Have used it for a year now. Can't see any disadvantages. Minimum computer spec has been a gig of RAM

---

### Post by solarwind on 2008-02-25
> **AlanR8 said:**
> Have used it for a year now. Can't see any disadvantages. Minimum computer spec has been a gig of RAM

But do you notice a difference in performance?

---

### Post by bone2006 on 2008-02-26
I was just reading about it as well and thought I'd search here to see what others had to say about it.  Looks really intresting

---

### Post by Ariccanfly on 2008-02-26
I installed it after reading digg article as well...
:guitar: hi guys!

so my HD ticks now every 30 seconds... hmmm

i dont even know how to turn it off...  hmm
 
and many things need to be done besides geeking out..
oh well i'll see what hdparm sais... 

oh, another can or worms....

i give up for today.. on to my homework..

---

### Post by priegog on 2008-02-26
This is relevant to my interests... any knoledgable person who can answer this around here? Because really, Digg is not a place I trust for linux advice.

---

### Post by SOULRiDER on 2008-02-26
> **priegog said:**
> This is relevant to my interests... any knoledgable person who can answer this around here? Because really, Digg is not a place I trust for linux advice.

I feel the same exact way.

---

### Post by jsully1 on 2008-02-26
Slashdot has more insightful comments regarding the subject:
[http://linux.slashdot.org/article.pl?sid=08/02/26/028210](http://linux.slashdot.org/article.pl?sid=08/02/26/028210)

---

### Post by chalewa on 2008-02-26
I guess I am really not seeing what disadvantages could come of this, unless you have a bare bones system...

Or am I missing something?

---

### Post by solarwind on 2008-02-26
> **priegog said:**
> This is relevant to my interests... any knoledgable person who can answer this around here? Because really, **[COLOR="Red"]Digg is not a place I trust for linux advice[/COLOR]**.

Yeah, most diggers don't know anything of what they're talking about. They only post comments to sound smart/funny.

> **jsully1 said:**
> Slashdot has more insightful comments regarding the subject:
[http://linux.slashdot.org/article.pl?sid=08/02/26/028210](http://linux.slashdot.org/article.pl?sid=08/02/26/028210)

Thanks! Will check out!

---

### Post by knutschr on 2008-02-26
The author used a machine with just 512 MB RAM when testing his software.

[http://www.cs.toronto.edu/~behdad/preload.pdf](http://www.cs.toronto.edu/~behdad/preload.pdf)

I think it is really interresting to have 
```
sudo tail -f /var/log/preload.log
```
running in terminal after installing today.

---

### Post by chalewa on 2008-02-26
> **knutschr said:**
> The author used a machine with just 512 MB RAM when testing his software.

[http://www.cs.toronto.edu/~behdad/preload.pdf](http://www.cs.toronto.edu/~behdad/preload.pdf)

I think it is really interresting to have 
```
sudo tail -f /var/log/preload.log
```
running in terminal after installing today.
Right, and he said that it was configured to use max 87mb or something

---

### Post by solarwind on 2008-02-26
> **knutschr said:**
> The author used a machine with just 512 MB RAM when testing his software.

[http://www.cs.toronto.edu/~behdad/preload.pdf](http://www.cs.toronto.edu/~behdad/preload.pdf)

I think it is really interresting to have 
```
sudo tail -f /var/log/preload.log
```
running in terminal after installing today.

Very nice. Shows in real time what's going on...

---

### Post by bone2006 on 2008-02-26
How would I determine the amount of time an application takes to launch?  Is there a command, so I can record on my own machine and see if I see a difference.  I already installed it on one of my machines, but I'd like to actually see my own numbers, because if it takes awhile for it to actually make a difference I might forget how slow or fast something was before if it's days later.

I'd guess there's a way in the terminal to determine the time an application takes to launch?

---

### Post by solarwind on 2008-02-26
> **bone2006 said:**
> How would I determine the amount of time an application takes to launch?  Is there a command, so I can record on my own machine and see if I see a difference.  I already installed it on one of my machines, but I'd like to actually see my own numbers, because if it takes awhile for it to actually make a difference I might forget how slow or fast something was before if it's days later.

I'd guess there's a way in the terminal to determine the time an application takes to launch?

The only method off the top of my head is modifying the source code to include a timer to print out the values and recompiling and using that program to test. Other than there, no idea. However, there is such a thing as "profiling" an application but I don't know much about it.

---

### Post by shouden on 2008-02-26
You might try the following

```
time <application>
```

You should get an output such as:

```


shouden@shouden-laptop:~$ time firefox

real    0m0.222s
user    0m0.020s
sys     0m0.016s



```

Shows startup time, which if I am not mistaken is what you are looking for.

---

### Post by jacrider on 2008-02-26
I decided to try it.

I have found in general that my "utilized" memory is about 300-400MB higher than normal, but no where near capacity (4GB), nor using the swap file.

I use OO.o spreadsheets very frequently.  They now open significantly faster.  Firefox is quick to boot up as well.

All in all, pretty much what the article suggested.

I like the idea.  Adding an extra GB of ram is cheap (these days) to make the user experience better.  Please no one suggest I also use Vista :)

---

### Post by solarwind on 2008-02-26
How long did it take you to notice these improvements?

---

### Post by shouden on 2008-02-26
If you are lookin to speed up Open Office opening time, I have found that disabling Java under the Open Office options increases the speed in which it opens, and unless you utilize the Java features it has no real downside. It decreased my time to load the applications on a Core2duo laptop 2 Ghz from 14 seonds to 3, huge improvement.

---

### Post by solarwind on 2008-02-26
> **shouden said:**
> If you are lookin to speed up Open Office opening time, I have found that disabling Java under the Open Office options increases the speed in which it opens, and unless you utilize the Java features it has no real downside. It decreased my time to load the applications on a Core2duo laptop 2 Ghz from 14 seonds to 3, huge improvement.

Yep, here's how to speed it up even more: [http://www.blog.solarwind.metafy.org/2008/02/25/how-to-speed-up-openoffice-in-linux/](http://www.blog.solarwind.metafy.org/2008/02/25/how-to-speed-up-openoffice-in-linux/)

---

### Post by shouden on 2008-02-26
Excellent link, writer loads in under a second now :)

---

### Post by solarwind on 2008-02-26
> **shouden said:**
> Excellent link, writer loads in under a second now :)

Thanks, lol. First time someone got something useful out of my blog.

---

### Post by jacrider on 2008-02-26
> **solarwind said:**
> How long did it take you to notice these improvements?

Almost immediately - say within the session I installed.

Spreadsheet is now about a second to open.  VLC is about the same.

I have a lot of ram and a C2D E6850 chip, so things should be fairly fast, but this is a big improvement.

---

### Post by solarwind on 2008-02-26
> **jacrider said:**
> Almost immediately - say within the session I installed.

Spreadsheet is now about a second to open.  VLC is about the same.

I have a lot of ram and a C2D E6850 chip, so things should be fairly fast, but this is a big improvement.

Hmm, that's pretty quick to improve. I thought this thing takes time to *learn* your habits.

---

### Post by jacrider on 2008-02-26
> **solarwind said:**
> Hmm, that's pretty quick to improve. I thought this thing takes time to *learn* your habits.

My frequent usage is simple:  Firefox, OO.o, Skype.

In one session, I likely load each a couple of times.  That seemed to be enough.

---

### Post by zerix01 on 2008-02-27
Obviously people are seeing improvements with using Preload, but I came across [this link]("http://ubuntuforums.org/showthread.php?t=74197") from OSnews. Someone was talking about Prelink which would pre load commonly used Libraries to speed up aplication launches. I guess Prelink is no longer needed due to some new features starting in feisty. 

Does anyone know if these features interfere with Preload? It seems Preload loads a lot more of the program than just some libraries but could this cause enough duplicated effort to have a negative effect on system resources?

---

### Post by bone2006 on 2008-02-27
I ran time firefox and later installed preload and rebooted, ran it so many times, rebooted, so many times, ran firefox a few dozen times and when comparing the time before preload and the time after preload.

preload has improved the time

---

### Post by solarwind on 2008-02-27
> **bone2006 said:**
> I ran time firefox and later installed preload and rebooted, ran it so many times, rebooted, so many times, ran firefox a few dozen times and when comparing the time before preload and the time after preload.

preload has improved the time

Thats interesting! How much time did it improve by?

---

### Post by bone2006 on 2008-02-29
Well I only tested a text editor and the speed improvements weren't night and day, but the time was faster, so any speed improvements I"ll take.

---

### Post by noynac on 2008-03-01
I installed preload about 3 days ago and had a few thoughts:

* Installing preload was easy. It's in the repo's and on my computer only required about 175 kB of disk space.  

* The amount of memory used by preload seems to vary greatly, but I have not noticed any adverse impact from preload memory use. I have included below memory used before and after installation of preload. 

* The increase in speed is noticeable but by no means dramatic on my 4-year-old Dell Pentium 4 with 1 GB of memory. I do notice that my computer does not access my noisy hard drive near as often with preload; I like that a lot. 

* I intend to continue using preload. For other users, I suspect the best advice is to install preload and see what you think. It's easy to uninstall if you don't like it.

~~~

Before preload install*
Used: 283,128 kB
Free: 751,996 kB

Immediately after preload install*
Used: 297,916 kB 
Free: 737,208 kB

Three days after preload install*
Used: 451,344 kB
Free: 583,780 kB

* Measured using the top command immediately after reboot.

---

### Post by MadsRH on 2008-03-02
Will this "feature" be available in 8.04?

Would be great if it was installed by default and could be configured from System (Administration or Preferences) menu.

---

### Post by solarwind on 2008-03-02
> **MadsRH said:**
> Will this "feature" be available in 8.04?

Would be great if it was installed by default and could be configured from System (Administration or Preferences) menu.

Yeah, that's true, a GUI to configure it.

---

### Post by GrouchoMarx on 2008-03-06
By loading programs which have not necessarily been requested, I imagine that preload will increase (unnecessary) hard drive usage over time.

Can anyone confirm this?

---

### Post by bone2006 on 2008-03-30
GrouchoMarx what your saying or asking is the opposite of what noynac has indicated.  His noise HD was accessed a lot less.

From reading other posts it seems that people believe it works great if you have 1GB or more of Ram, but less than 1GB and the results aren't always great.

I have it on a system with 512mb of ram and I'm pretty happy with the results to be honest though.  It probably depends on which applications you run the most and the amount of applications.  If your only running say firefox then I could see that even less ram it would have benefit.  If you have 10 programs that you run them almost all the same amount of time, then I could see that it might slow down your system if you have less than 1GB of ram.
I use about 5 programs often, you'll mostly see my system up with firefox and a terminal constantly.

---

### Post by solarwind on 2008-03-31
Is there a way to *hardwire* preload so it loads the apps that only *you chose*? I mean... I don't want it to *train* itself to my habits. I'd much rather like to **tell** it what to preload explicitly. Is this possible?

---

