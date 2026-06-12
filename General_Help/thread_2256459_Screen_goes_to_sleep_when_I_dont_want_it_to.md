---
title: "Screen goes to sleep when I dont want it to"
date: 2014-12-12
forum: General Help
---

### Post by bryan35 on 2014-12-12
Basically, my screen goes to sleep on my laptop after around 10 minutes of inactivity...sometimes. The Light Locker Settings are all on "never", but when watching a youtube video it still goes blank. After I move my mouse it wakes up.  But what makes it weirder is, last night [and this has happened before] as with most nights, I didnt put the light locker settings on 1 min as it blanks after around 10 mins anyway....but it stayed on all night. Any ideas whats going on?

xubuntu 14.04.1

---

### Post by Dennis N on 2014-12-12
See this post for a solution:

[http://ubuntuforums.org/showthread.php?t=2253791&p=13172640#post13172640](http://ubuntuforums.org/showthread.php?t=2253791&p=13172640#post13172640)

---

### Post by bryan35 on 2014-12-13
This worked, so many thanks....but does xscreensaver just display a blank screen or does it actually turn off the screen?
I still use light locker to turn off the screen after 1 min when I head to bed...but xs over-rides this.

---

### Post by Dennis N on 2014-12-14
> **bryan35 said:**
> This worked, so many thanks....but does xscreensaver just display a blank screen or does it actually turn off the screen?
I still use light locker to turn off the screen after 1 min when I head to bed...but xs over-rides this.

Thanks for the feedback. Glad to hear it worked. I'm pretty sure Xscreensaver by itself is just displaying a blank screen (as set on the display modes tab), and not turning off the screen. If you look at xscreensaver setting's advanced tab, you can apparently configure it to work with the power manager to turn the screen off as well (see right section on the advanced tab). I haven't used that option so can't say how well it works.

---

### Post by bryan35 on 2014-12-14
Awesome!

Set it to "standby after" and got exactly what I wanted.

Many thanks, again!!

---

