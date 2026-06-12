---
title: "Alarm Clock"
date: 2007-08-29
forum: General Help
---

### Post by Nirva on 2007-08-29
Hay,

I was wondering if it were possible to turn my computer in an Alarm Clock without having to leave my computer powered on all day.  So does anyone knows if it is possible, to make that my computer boots at a given time, logs in and executes a command ( like playing music ).  
I know that it is possible to executes commands at a given time with Kalarm, but i didn't found anything about starting the computer up.

Thanks

---

### Post by kellemes on 2007-08-29
How can you instruct your pc when it's off?!

---

### Post by strider1551 on 2007-08-29
> does anyone knows if it is possible, to make that my computer boots at a given time...

If memory serves me, I think I have seen computers with a BIOS option to boot at a specific time of day.  I'm not sure how prevalent that is. (Heck, I'm not even sure that I actually saw that once).

> ...log in and executes a command

I can't think of how to automatically log in, and that wouldn't be the best idea security wise anyway.  I suppose you could place a script at the right init level.  I am certain that I have seen command line mp3 players before...

---

### Post by kellemes on 2007-08-29
Autolog is an option in your loginmanager..
Execution of a script at startup is easy too.. assuming you're on Gnome...
**System -> Preferences -> Sessions -> Startup Programs -> Add**

Autostart of PC maybe possible but you should try to get this going from hibernation maybe?
Don't know how to do this..

---

### Post by mdebusk on 2007-08-29
> **Nirva said:**
> Hay,
I was wondering if it were possible to turn my computer in an Alarm Clock without having to leave my computer powered on all day.

If you want your computer off, but you want to wake up at a given time, I really think [this method](http://www.amazon.com/Sony-ICF-CD815-Stereo-Clock-Radio/dp/B000MXYPYW/ref=pd_bbs_sr_1/105-0107426-5765215?ie=UTF8&s=electronics&qid=1188408446&sr=8-1) will get you what you're after better than anything else. It's what i use and it's very effective.

---

### Post by strabes on 2007-08-29
The only problem you'll have is turning on your computer at a certain time. You can just utilize cron (with a frontend, whatever) for your alarms. You can also login automatically, which was detailed above.

---

