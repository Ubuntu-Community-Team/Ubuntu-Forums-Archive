---
title: "DVD Burning"
date: 2005-06-28
forum: General Help
---

### Post by qalimas on 2005-06-28
In my house, we have two DVD burners, each of the machines run Windows.  It takes a lot to bypass DVD encryption to copy our DVDs (legally, we own the originals).  I was wondering, does K3B or any other K/Ubuntu program bypass this with no hassle?  In Windows we needed some extra programs, but what about for Linux?

---

### Post by emmet on 2005-06-29
Can you just go from a DVD reader to a DVD writer? Make a clone of the original DVD?

If you own the copyright of the DVDs, then do you have source data for them before it was encrypted?

Anyway, look here:

[http://www.linuxquestions.org/questions/answers.php?action=viewarticle&artid=308](http://www.linuxquestions.org/questions/answers.php?action=viewarticle&artid=308)

This might help.

---

### Post by qalimas on 2005-06-29
I meant from the reader to the writer, I needed an artical on making it bypass encryption, thanks! :D

---

### Post by Navin_Johnson on 2005-06-30
There are several ways to do this.  If you were already doing it in Windows then you may want to run DVDDecryptor and DVDShrink through wine.  Mr Bass has posted on this here (look in the HOW Tos section of the forum) and has a HOWTO w/ pictures on his website ([www.mrbass.org](www.mrbass.org)) that works very well.  Pay attention to the instructions though and be sure to have dvds in the drives when you install so that they get setup correctly.  (I didn't do this so I only have partial functionality right now until I reinstall it correctly!)

There are Linux native possibilities as well.  I'm quite interested in getting these working but I've not yet found the time.  lxdvdrip looks promising as a way to decode, rip, and "shrink" the dvd9 to dvd5.  If you want to simply decode onto your harddrive then dvd::rip may be all you need.  There are a number of other options but again, I'm not yet familiar with them.

Right now I use a hybrid solution to backup:  I use dvdshrink through wine to decode and write the iso image.  I use the "write to cd/dvd" dialogue (I just right click on the iso file on my desktop) to backup.  I've not yet come across a dvd that was encrypted in a way that dvdshrink wouldn't handle but if/when I do I will hopefully have gotten the linux native solutions working.

Navin Johnson

---

### Post by emmet on 2005-06-30
The Wine solution works very well for me. Done without any hitch at all.

Emmet

---

### Post by qalimas on 2005-06-30
I might go for the Wine solution, but my dad won't even give Linux a shot as a desktop OS.  He's too pro-Windows.  (the goal on my end is to get him to use Linux and Linux apps ;)) He only wanted a Linux box to setup and put his burner in to copy DVDs his Windows box won't do right.  I'm gonna get him to try Ubuntu on his computer sooner or later, I wish he'd just try running it for a week or so, but he won't even put in the live cd for a minute :(

---

