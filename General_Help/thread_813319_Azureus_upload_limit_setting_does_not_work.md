---
title: "Azureus upload limit setting does not work"
date: 2008-05-30
forum: General Help
---

### Post by daehenoc on 2008-05-30
Hi all,

I am having a weird problem with Azureus, the upload limit setting just does not work :(  I can set it to anything, and that limit will stay in place for a minute or so, then Azureus will drop that setting and choke the uplink to my ISP.  This makes it very hard to do anything else while Azureus is running, and also slows down anything I'm downloading with Azureus!

I've tried playing with the Autospeed and LAN settings (in Azureus options) but nothing seems to make the upload limit stick!  Does anyone have any tips?

Thanks,
G

---

### Post by bwhite82 on 2008-05-30
I can remember having this problem, I had to completely remove the Auto-share? (I can't remember what its called) plugin before I could finally set it. Look in your plugins for something called Auto-???

EDIT: Autospeed

---

### Post by daehenoc on 2008-06-01
As it turns out, it was Speedscheduler that was doing the damage!  Turned it off and voila, the upload limit stays at what it is set to, woot!

Azureus did crash when I installed SS, so I'm going to remove it and reinstall, see what happens.

---

### Post by Jive Turkey on 2008-06-01
I prefer to run the most current azureus-vuse from my home directory rather than the packaged one.  Transmission has started to grow on me lateley.  Is thare any extra security risk running apps in this way? (meaning in /home/username, instead of /)

---

### Post by daehenoc on 2008-06-01
Not any more security risk that I can think - do you know of a way of limiting the download speed in Transmission?  Disclaimer, I haven't investigated Transmission at all :P

---

### Post by latna on 2008-06-01
> **Jive Turkey said:**
> I prefer to run the most current azureus-vuse from my home directory rather than the packaged one.  Transmission has started to grow on me lateley.  Is thare any extra security risk running apps in this way? (meaning in /home/username, instead of /)

That's how I run azureus as well. I hadn't thought about it before, but I guess it does pose a risk. The reason is that your user has write permission to the program directory and executables this way. That would add an avenue for bad-ware to enter your system. This is why it's bad to run as root.

Practically speaking though, as long is this sort of thing is kept to a minimum, it's prolly a very difficult target for the bad guys IMHO. The risk is there though.

---

### Post by daehenoc on 2008-06-02
Hah, true to form, RTFM saves the day!

In SpeedScheduler, when you configure a schedule, you specify the maximum upload speed for that schedule.  It overrides any other upload speed limit you set, so I set that upload speed to 10kb/s and I'm good :D

---

