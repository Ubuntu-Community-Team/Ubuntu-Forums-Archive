---
title: "Fitness/Workout Software for Linux"
date: 2007-01-11
forum: General Help
---

### Post by EnderTheThird on 2007-01-11
I've been using Ubuntu exclusively since April '06 or so.  Recently, I've also started working out regularly, ~3 times a week.  I'm wondering if anyone knows of any fitness or workout software for Linux that I could use to keep track of my progress.  I remember finding one before ("Diary of Hercules", I believe) but I ran into dependency problems and it was a couple years old.  If anyone knows of one or could point me in the right direct, that would be great.  Thanks!

NOTE:  Sorry if this is the wrong forum category, but I didn't see one specifically for software.  If there is a better category for this post, please go ahead and move it!

---

### Post by EnderTheThird on 2007-01-12
I hate doing this, but...

**bump**

Anyone have any suggestions?  I just found something called Open Fitness ([http://www.workoutware.com/](http://www.workoutware.com/)) but the Linux installer doesn't work.  ](*,)

---

### Post by justynbutler on 2007-02-16
Hi,

What kind of thing should this software do, in it's simplest form? It sounds like a good candidate for a little python app ;-)

Justyn

---

### Post by jamesjrl on 2007-02-16
i'd also be interested to see something if it exists

i'm currently just using a spreadheet in openoffice to track progress
in my case weight and number of reps for each exercise with date.

---

### Post by bcmiller on 2007-03-06
I just found this thread when I searched for a program like this and then I decided to just use Google Calendar to keep track of everything

I entered in the exercises I intend to do and my current weight for day 1 and what I ate today... I will edit the events to write what I did that day in more detail.

This has the advantage of being online and not tied to my computer.

I wanted something more robust but I suspect I may have just been looking for an excuse to stay on my computer while appearing to do something to get in better shape.

---

### Post by jenred on 2007-03-21
I just found this link:

[http://www.linux.com/article.pl?sid=07/02/28/1450201](http://www.linux.com/article.pl?sid=07/02/28/1450201)

That references two applications:

[Sportstracker]("http://www.saring.de/sportstracker/index.html")

and

[pytrainer]("http://pytrainer.e-oss.net/")

Haven't used either -- but I too am on a quest to find some good open source tools for tracking fitness.  

Will post if I find any additional apps.

---

### Post by kperkins on 2007-05-11
Found one today called gtrainer [http://www.gnomefiles.org/app.php/gtrainer](http://www.gnomefiles.org/app.php/gtrainer)
Looks like pytrainer from the screenshots, but done in c++ and gtkmm
I had problems with pytrainer on Feisty.

---

### Post by DarKnyht on 2007-05-26
I have found a website called [www.fitday.com]("http://www.fitday.com") that I have been using.  It is not perfect, but it does track diet (calories, fat, etc.) and exercises (calories burned, distance, etc.)

---

### Post by der_joachim on 2007-05-27
> **jenred said:**
> I just found this link:

[http://www.linux.com/article.pl?sid=07/02/28/1450201](http://www.linux.com/article.pl?sid=07/02/28/1450201)

That references two applications:

[Sportstracker]("http://www.saring.de/sportstracker/index.html")

and

[pytrainer]("http://pytrainer.e-oss.net/")

Haven't used either -- but I too am on a quest to find some good open source tools for tracking fitness.  

Will post if I find any additional apps.

I never got sportstracker to work in KDE. That's a bummer, because it explicitly supports my heart rate monitor. Yoi can get a recent version of sportstracker at [http://getdeb.net/](http://getdeb.net/) .

---

### Post by kperkins on 2007-08-12
You might try [http://traineo.com](http://traineo.com)  I've been using it and you can track calories burned by exercise, diet, goals, etc.

---

### Post by drawman on 2007-11-20
EnderTheThird:


> Anyone have any suggestions? I just found something called Open Fitness ([http://www.workoutware.com/](http://www.workoutware.com/)) but the Linux installer doesn't work. 

This software seems to be the best possibility, somebody might be able to actually get it to work on Ubuntu...I'm not knowledgeable enough to get Java to execute i.t 

 I know this is an old thread, maybe somebody has been able to solve this..

---

### Post by 0micron on 2007-11-20
Did you guys try Kipinä? You can find it in Add/Remove

---

### Post by drawman on 2007-11-20
It seems that Kipina is set up for time and distance tracking.  I am looking for strength training software and that deals with exercises, weight and reps and sets. 

 It could be adapted perhaps, but it might be better to use a spreadsheet. 

It is perfect for runners  though.

---

### Post by PartisanEntity on 2007-11-22
I'm actually looking for something like this too, I work out about 3 times a week and would be interested in keeping track of my achievements. Sportstracker looks good, I shall give it a try.

---

### Post by PartisanEntity on 2007-11-22
I have just tested SportsTracker, looks good but unfortunately it is aimed at distances and so only suitable for cyclists or swimmers etc.. I have requested support for other types of sports on their project site.

p.s. if you would like to suppor this feature request you can add a comment here:
[http://sourceforge.net/tracker/index.php?func=detail&aid=1836581&group_id=133110&atid=726273](http://sourceforge.net/tracker/index.php?func=detail&aid=1836581&group_id=133110&atid=726273)

---

### Post by drawman on 2007-11-23
Is there a reason that the fitness tracking program (Linux version) from ([http://www.workoutware.com/](http://www.workoutware.com/)) won't work on Ubuntu 7.10 or is it just my starting position on the  Ubuntu learning curve?

They suggest the chmod command, but I can't even get it to recognize the downloaded file.

---

### Post by PartisanEntity on 2007-11-23
Download the .sh file

Then 

```
chmod +x openfitness_unix_2_0_0.sh
```

Finally, 

```
sh openfitness_unix_2_0_0.sh
```

---

### Post by PartisanEntity on 2007-11-23
That's a shame, OpenFitness is a trial, you have to buy it. The trial lasts 30 days.

---

### Post by rosslaird on 2007-12-05
I have tried most of the programs in this thread, and I find most of them quite lacking (buggy, awkward translations, etc.). I recognize that it's a huge project for someone to design software, so I'm not knocking the designers -- it just seems that so few linux users actually do any exercise (!), and so good exercise software is hard to come by. Think of the huge range of email applications and browsers and other goodies -- but almost nothing for exercise. That says something about the culture of Linux, I think. (What it says is: we're a bunch of sedentary loafers.)

Anyway, I run and I climb (and do various other sports depending on my mood). I like to log my activities, and I've been doing so in emacs org-mode for a while. But there are some limitations to that system (most of which have to do with emacs itself, and the fact that I don't know how, and don't really want to know how, to program in Lisp). I can't track my progress easily, and I can't view my log in the ways that I want.

So: I have investigated online offerings, and I have to say mapmyrun.com is pretty good. It allows for various sports and has all kinds of useful stuff for tracking health and fitness.

[MapMyRun]("http://www.mapmyrun.com/")

[MapMyRun new features]("http://www.mapmyrun.com/new_features")

If you don't mind the ad ribbon, mapmyrun is free and it works well.

Ross

---

### Post by malrost on 2008-01-31
Just wanted to say thanks for the discussion. These are exactly the kind of apps I've been trying to locate, and until I came across this thread had only found non-free apps.

---

### Post by malrost on 2008-02-10
Options appear limited w/ x86_64 Gutsy.

So far I've tried four of the apps recommended in this thread, and of them I'd recommend SportsTracker. PyTrainer works as well. Neither of the two appear to consider detailed tracking for strength training (sets, reps, weights, etc.)


Unfortunately I would not recommend kapina and gtrainer for an x86_64 install. I got seg faults with kapina (even from the synaptic install), and while there were i386 rpms for gtrainer that I did not try, the link to the x86_64 version seemed to be long dead.

---

### Post by Kourosism on 2008-02-10
I've been looking for something similar. To be honest, the best I've come up with has been a spreadsheet which I found someone else had been using. I modded it slightly (and it needs more adapting to cope with dates more than a few months away) but it's workable.

If anyone wants to see it, it's on Google Apps - PM me and I'll send it on to you.

---

### Post by crisnoh on 2008-03-26
So the verdict is that there is no fitness tracking software out there for weight training...

---

### Post by justynbutler on 2008-03-26
> **crisnoh said:**
> So the verdict is that there is no fitness tracking software out there for weight training...

Give me a couple of months, I've given in and started writing one.

---

### Post by denver38 on 2008-04-08
> **crisnoh said:**
> So the verdict is that there is no fitness tracking software out there for weight training...

that seems to be the case :(
I hope something useful will pop up in the near future, I'll keep an eye on this thread and in the meantime I stick to OO Spreadsheet .

---

### Post by PartisanEntity on 2008-04-09
I keep monitoring what is currently available for weight lifters, I have not found anything yet.

**justynbutler**, how are you progressing?

---

### Post by tribble222 on 2008-04-14
I am also interested in your progress, justynbutler!  Will subscribe to this thread.

---

