---
title: "youtube keeps freezing"
date: 2007-06-25
forum: General Help
---

### Post by linux noooob on 2007-06-25
when ever i try to play a youtube video the firefox browser goes gray and it needs to be forced to quit and i have updated my flash to 9

---

### Post by Crafty Kisses on 2007-06-25
> **linux noooob said:**
> when ever i try to play a youtube video the firefox browser goes gray and it needs to be forced to quit and i have updated my flash to 9

That's weird, could be a possible resource issue, try going into terminal and type:
```
top
```
See what's running, also what are your system specs?

---

### Post by tocleora on 2007-06-25
This is (sorta) happening to me now too... I notice a big "powered by google" graphic now and none of the videos will play.  it doesn't lock up firefox but they just play for a second and stop.  They were working last time I tried (last week). Anyone else experiencing this problem?

---

### Post by Crafty Kisses on 2007-06-25
> **tocleora said:**
> This is (sorta) happening to me now too... I notice a big "powered by google" graphic now and none of the videos will play.  it doesn't lock up firefox but they just play for a second and stop.  They were working last time I tried (last week). Anyone else experiencing this problem?

Both of you guys should just install "Conky"
```
sudo apt-get install conky
```

---

### Post by tocleora on 2007-06-25
I honestly don't think my issue is with my computer, I think it's with youtube, that's why I was asking if other people were experience the problem with youtube's update.  The browser doesn't lock up for me, it just doesn't play the videos on youtube anymore...

---

### Post by linux noooob on 2007-06-25
it seems to be doing it on imeem too.  it does it on the videos and on the music i think it starts crashing once it starts to download i think the error may be in that.

---

### Post by tocleora on 2007-06-25
I just upgraded flash to the latest version on adobe's web site (9,0,31,0)  and that fixed my problem.  You might try that if you haven't.  I was using 9,0,21,78 before.

---

### Post by linux noooob on 2007-06-25
nothing happend when i installed conky and  installed the new flash.

---

### Post by rbmorse on 2007-06-25
I have 9.0.31.0 and I still get lockup on Youtube.

---

### Post by tocleora on 2007-06-26
> **rbmorse said:**
> I have 9.0.31.0 and I still get lockup on Youtube.

huh... you might try reinstalling it?  I doubt that will work since it's only a single .so file, but I also think it's odd that just moving from 9,0,21 to 9,0,31 fixed my problem...

---

### Post by testube_babies on 2007-06-26
This is a very common problem that is most often caused by the sound system's interaction with flash video.  This post solved the problem for me:
[http://ubuntuforums.org/showthread.php?p=2787287#post2787287](http://ubuntuforums.org/showthread.php?p=2787287#post2787287)

This, however, doesn't fix the buggy software coming out of Adobe...so it might not work for you :)

---

### Post by stchman on 2007-07-09
Ok, my laptop was doing this with Firefox while playing YouTube video.  This worked for me, I cannot guarantee it will work for you.

First remove the Flash 9 plugin from your Firefox plugins folder.

I believe it is in the following folder

~/.mozilla/plugins

Next install the flash-nonfree using apt or Synaptic

sudo apt-get -y install flashplugin-nonfree

This took care of the problem for me.

---

