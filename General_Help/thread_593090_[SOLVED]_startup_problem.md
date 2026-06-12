---
title: "[SOLVED] startup problem"
date: 2007-10-26
forum: General Help
---

### Post by gishaust on 2007-10-26
hi everyone

I am having a start up problem with my Ubuntu gui what i would like to know is how do i problem shoot it.  i know looking at the logs help. but how do i know which one it is. I get a screen after boot up that there is an isssue with the gui loading. 

Any help would be great.

Gishaust

---

### Post by ceno-byte on 2007-10-26
Can u please post the error message?

---

### Post by gishaust on 2007-10-27
ceno-byte thank you for your reply,

It says that it can't load sound and will try and load it next time it startsup. I am else where right now can get exact term sorry!!!!

But maybe I am not clear in what I am wanting. I want a process so that  I can trouble shoot myself. 
For example in windows you have the event viewer, device manager and so on. From them you can see the issue, then fix it or google it. 

All i am looking for  is a few process that others use so that I can start solving things myself. 
An example  is looking into  the logs. But what logs do I look into when there is a problem?

My question is this, how do the linux world go about problem solving? Is the logs the only thing?

Gishaust

---

### Post by ceno-byte on 2007-10-27
well if it is a process you are looking for here is what i do 

1. I usually try to write down the error message i am receiving then i look it up on the ubuntu forums and if i cant find any information, i google the error message. 

2. In the case that none of those work i would recommend going to [www.linuxquestions.org](www.linuxquestions.org) in my experience i have been able to find some solutions there that i was not able to find on the ubuntu forums or through google but do remember to alway post back your solution here in the forums to help everyone else out.

3. For a windows event manager thing in ubuntu there is the system log to open that click 
System-->Administration-->System log
that will have a log of everything happening in your system then you can try a search on google for something that relates to your issue in the log.

 As for the problem you are having with the sound not starting up error are you able to play sound on your desktop?

and is the error message something like this? 

error while initializing the sound driver:
device /dev/dsp can't opened (no such file or directory)

---

### Post by gishaust on 2007-10-27
That process is exactly what I am looking for. 

Thanks

I will get back  with the error.

---

