---
title: "Do I need linux command line knowledge before learning bash scripting"
date: 2013-06-14
forum: General Help
---

### Post by AgentZ86 on 2013-06-14
Is bash script commands the same as learning the linux command line terminal  except you store the script or commands in a text file ?

I mean to ask:
Do I need command line knowledge before I start learning bash scripting ?

Please advise

---

### Post by JRV on 2013-06-14
I kind of learned them both at he same time.
There are commands you will only use in a script, and many that you will use stand alone.

Here are two links that will help:

Linux Commands: [http://www.ss64.com/bash/](http://www.ss64.com/bash/)

Linux Shell Scripting Tutorial: [http://freeos.com/guides/lsst/](http://freeos.com/guides/lsst/)

---

### Post by Cheesehead on 2013-06-14
> **AgentZ86 said:**
> Is bash script commands the same as learning the linux command line terminal  except you store the script or commands in a text file ?
...
Do I need command line knowledge before I start learning bash scripting ?

Yes, that describes shell scripting fairly accurately. There are caveats and exceptions, but that's a good 85% solution.
No. While a prior understanding of many commands will speed your learning, many have learned both at the same time. JRV's links are quite good.

---

### Post by AgentZ86 on 2013-06-14
thanks thats sort of what I was thinking too

---

### Post by HiImTye on 2013-06-14
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]
bash scripting helps you learn how yo use commands that you otherwise wouldn't, so i'd recommended it as a method to better learn commands

---

### Post by matt_symes on 2013-06-14
Hi

Learning bash goes hand in hand with learning terminal commands as it's the terminal commands you generally want to script.

There are only two sites i really recommend to learn bash scripting, bashisms and bash gotchas in particular.

[http://mywiki.wooledge.org/BashGuide](http://mywiki.wooledge.org/BashGuide)

[http://wiki.bash-hackers.org/start](http://wiki.bash-hackers.org/start)

Don't get me wrong, there are many other good sites out there as well, but reading both of these sites will give you an excellent grounding in bash scripting.

After that, learn the differences between other bourne family shells such as dash, ash, zsh, korn etc.

Later, sign up for the weekly news letter from sites such as  [unix.stackexchange.com]("http://unix.stackexchange.com/") when you know a bit more as there you will here information from some seasoned bash/linux/unix/solaris users.

EDIT:

BTW learn to use some of the tools that bash scripting will not be able to help you with.

Learn sed and awk to start with, and an understanding of regular expressions are a must.

These are two good sites but they may be a bit heavy going at first so look for some other sites and when you understand them, read these two.

[http://www.grymoire.com/Unix/Regular.html](http://www.grymoire.com/Unix/Regular.html)

[http://www.grymoire.com/Unix/sed.html](http://www.grymoire.com/Unix/sed.html)

Kind regards

---

### Post by jbo5112 on 2013-06-14
A simple beginners guide that takes you through much of what you will need: [http://steve-parker.org/sh/sh.shtml](http://steve-parker.org/sh/sh.shtml)

---

### Post by coldraven on 2013-06-14
It's like needing to learn the meaning of words before you can construct a sentence.
I'm happy to use the command line because I started with MSDOS and batch files, but Linux is much more powerful.
The good news is that there is lots of good information on the internet. I'm sure that you will succeed.

---

### Post by Cheesemill on 2013-06-14
> **matt_symes said:**
> BTW learn to use some of the tools that bash scripting will not be able to help you with.

Learn sed and awk to start with, and an understanding of regular expressions are a must.

These are two good sites but they may be a bit heavy going at first so look for some other sites and when you understand them, read these two.

[http://www.grymoire.com/Unix/Regular.html](http://www.grymoire.com/Unix/Regular.html)

[http://www.grymoire.com/Unix/sed.html](http://www.grymoire.com/Unix/sed.html)

+1

If you can get your hands on a copy of the O'Reilly book [*sed & awk, 2nd Edition*]("http://shop.oreilly.com/product/9781565922259.do") then I highly recommend it (for learning regex as well as sed and awk). I first came across it in my local library and after having it on loan for a couple of months I bought my own copy when I had to return it. It's always at hand on my desk and I often refer to it when creating regular expressions.

---

### Post by matt_symes on 2013-06-14
Hi

> **jbo5112 said:**
> A simple beginners guide that takes you through much of what you will need: [http://steve-parker.org/sh/sh.shtml](http://steve-parker.org/sh/sh.shtml)

This is kind of my point.

Please don't get me wrong, as steve parkers site is great and i have read it myself, however from the site...

> A Bourne Shell Programming/Scripting Tutorial for learning about using the Unix shell.

Personally i think, if you want to learn bash then learn bash and bashisms.

This would be my second step. Learn the bourne/korn family shells.

I am in no way disparaging your post. If i was teaching, I would just teach it in step 2.

Kind regards

---

### Post by AgentZ86 on 2013-06-14
all very helpful thanks

I think I'll start a comination of all of it. I do remember my old knowledge of dos way back when. 
I have since learned python and so I have some coding experience now although noobish. I have written a few scripts and apps.

Anyhow thanks I have some reading to do then.

---

### Post by HiImTye on 2013-06-14
I recommend starting with a goal. if you start there, you can use the [all-father]("http://google.com") to find what commands to use, and how.

also, the grymoire.com site was great for me when I was learning sed, and I also recommend this chart for the differences in regex syntax between different languages (scroll to the bottom) [http://www.regular-expressions.info/refflavors.html](http://www.regular-expressions.info/refflavors.html)[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]

---

### Post by matt_symes on 2013-06-14
Hi

Finally, there is a *must tell you about site* that i must tell you about :)

Useless use of cat.

It will make more sense later.

[http://partmaps.org/era/unix/award.html](http://partmaps.org/era/unix/award.html)

Kind regards

---

### Post by AgentZ86 on 2013-06-16
thanks all this is great, i'll read up on it ALL

---

### Post by BlinkinCat on 2013-06-16
Hi,

You could also look at the Links page in [NewDocs]("https://help.ubuntu.com/community/NewDocs") for more assistance of a general nature.

Cheers - :)

---

