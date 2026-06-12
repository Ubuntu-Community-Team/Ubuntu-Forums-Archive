---
title: "Killing/Removing unneeded processes?"
date: 2013-01-21
forum: General Help
---

### Post by dannyboy79 on 2013-01-21
I am running Xubuntu 12.04 on some really old hardware. A 1.8Ghz Core2Duo with only 2GB RAM (maxed out). I can't even run google chrome with only 1 tab (website being random.org) and kazam screencaster (not even recording, just open) without chrome giving me the Jim's Dead screen because my system is out of memory.

I am curious if there are any background process's I can kill, for example I killed xfce4-volumned, which is for keyboard audio controls which my keyboard doesn't even have. That fee'd up some RAM but there are a ton of other process's that I am not sure what they do. When I run kazam to capture me playing shank 2, I kill dropbox app and many other process's just wondering if there's a guide for trimming down the fat. 

I did change my swapiness to 10 which seemed to help at first BUT not it appears like I run out of memory way to fast being that I have 2GB of RAM.

Thanks for any help you can provide.

---

### Post by ibjsb4 on 2013-01-21
Dual core with 2G of ram is plenty for xubuntu.  What's eating up your memory?

```
top
```

---

### Post by ajgreeny on 2013-01-21
Xubuntu should normally only use about 150MB ram on startup, and I agree that your machine should run that OS without any problem; it should even be able to run vanilla Ubuntu with unity if you have the appropriate graphic card for 3D.

Something is obviously very wrong, so the top command suggested by lbjsb4 should show you what is using all your resources and give you some idea about what to do.

---

### Post by dannyboy79 on 2013-01-21
ok, will post the top output later after work. i am finding it very weird to run out of memory with only running kazam screencaster and google chrome with only 1 tab. it was rediculious that i couldn't even get 1 webpage to load, chrome said Jim's Dead or whatever when there's no memory for it.

I wonder if there's a memory leak within kazam cause it wasn't even recording, it was merely open that's all. I know when recording a 1280x720 window it will use a lot of resources.

thanks for the replies guys, will post up a top output later

---

### Post by dannyboy79 on 2013-01-22
here's when I rendering a video to h264 and aac audio, have chomr open with 4 or 5 tabs, skype, a terminal, some nautilus windows open and that's it. oh and dropbox running in background.[IMG]https://lh4.googleusercontent.com/-vhFiMgPooFg/UP4d0U3YB5I/AAAAAAAABbs/r1ePycsJqGk/s683/top.png[/IMG]

---

### Post by bab1 on 2013-01-22
> **dannyboy79 said:**
> here's when I rendering a video to h264 and aac audio, have chomr open with 4 or 5 tabs, skype, a terminal, some nautilus windows open and that's it. oh and dropbox running in background.[IMG]https://lh4.googleusercontent.com/-vhFiMgPooFg/UP4d0U3YB5I/AAAAAAAABbs/r1ePycsJqGk/s683/top.png[/IMG]

What's melt?  The 4th process down (eg 17157) is using 137% CPU.  Yikes!

---

### Post by omeomi on 2013-01-22
> **bab1 said:**
> What's melt?  The 4th process down (eg 17157) is using 137% CPU.  Yikes!

melt is doing the rendering in kdenlive. 

I don't understand how this output relates to your initial problem. You can run all this without any problem but not with the screencast software? 

Can you show the output of top with just the screencast software running?

---

### Post by dannyboy79 on 2013-01-22
> **omeomi said:**
> melt is doing the rendering in kdenlive. 

I don't understand how this output relates to your initial problem. You can run all this without any problem but not with the screencast software? 

Can you show the output of top with just the screencast software running?sure, sorry about that. here's with kazam running and chrome with only 3 tabs running
[IMG]https://lh3.googleusercontent.com/-3Mm2eedpY1I/UP5uvkBSIVI/AAAAAAAABcA/Xz3OFA2Pp18/s688/top1.png[/IMG]

---

### Post by vasa1 on 2013-01-22
> **dannyboy79 said:**
> sure, sorry about that. here's with kazam running and chrome with only 3 tabs running
[I M G]h t t p s : //lh3.googleusercontent.com/-3Mm2eedpY1I/UP5uvkBSIVI/AAAAAAAABcA/Xz3OFA2Pp18/s688/top1.png[/ I M G]

That image of top shows you have kde processes as well. So this isn't a "pure" Xubuntu.

---

### Post by omeomi on 2013-01-22
> **dannyboy79 said:**
> sure, sorry about that. here's with kazam running and chrome with only 3 tabs running

Do you get the same thing if you run a different browser than Chrome? 

The weird thing is that Chrome is supposed to use one process per tab, yet I count at least 11 chrome processes in your output. So it might be a problem with Chrome running wild or something.

---

### Post by vasa1 on 2013-01-22
> **omeomi said:**
> Do you get the same thing if you run a different browser than Chrome? 

The weird thing is that Chrome is supposed to use one process per tab, yet I count at least 11 chrome processes in your output. So it might be a problem with Chrome running wild or something.
True. But extensions take up processes as well. Anyway, Chrome's task manager will show what's what.

---

### Post by vasa1 on 2013-01-22
And OP may prefer to post top out as code rather than as an image:
```
top -b -n 1 > top.txt
``` where "n 1" is for just one run.

---

### Post by dannyboy79 on 2013-01-22
> **vasa1 said:**
> That image of top shows you have kde processes as well. So this isn't a "pure" Xubuntu.sorry if i wasn't clear on that. Yes, some kde dependencies were installed with kdenlive (my video editor) as well as some gnome things were installed since I like nautilus and gedit. 

BUT, is there any of these kde or gnome process's that I can kill?

---

### Post by dannyboy79 on 2013-01-22
> **omeomi said:**
> Do you get the same thing if you run a different browser than Chrome? 

The weird thing is that Chrome is supposed to use one process per tab, yet I count at least 11 chrome processes in your output. So it might be a problem with Chrome running wild or something.I agree, i often wonder if chrome has a memory leak like firefox did years ago.

---

### Post by dannyboy79 on 2013-01-22
> **vasa1 said:**
> And OP may prefer to post top out as code rather than as an image:
```
top -b -n 1 > top.txt
``` where "n 1" is for just one run.here's 1 run
[http://paste.ubuntu.com/1559008/](http://paste.ubuntu.com/1559008/)

---

