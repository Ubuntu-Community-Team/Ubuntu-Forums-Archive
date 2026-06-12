---
title: "Shutdown hang for approx 1 min."
date: 2008-01-26
forum: General Help
---

### Post by MonoBrow_063 on 2008-01-26
I've searched and can't find anything out there, new to the forums though (and Linux) so don't shout at me too much eh?

Anyways, I have a problem in that when I click the power button for the shutdown menu, the system completely hangs for about a minuite. Nothing more sinister, but it's effin annoying when you want to shut it down!

To be honest, with my limited knowledge of Ubuntu, I thought I'd come here so someone can help me diagnose it.

Many thanks

Mono

---

### Post by pointone on 2008-01-26
Try shutting down from the command line and watch for any error messages, etc. that may give an indication of what's going on.

Hit Ctrl+Alt+F1 to get to a console, log in, then run the command:

```
sudo shutdown -h now
```

---

### Post by MonoBrow_063 on 2008-01-27
Tried that one, and it worked first time every time. If I want to log out so the missus can get on her login, I've found it easier to hit Ctrl+Alt+Backspace as it ends up at the login screen. Probably not to good for the system though to do it over and over but it does appear to be something to do with the graphical interface rather than it's ability to turn off.

To give a better description, you click the button for the log off/shutdown/lock screen and it's almost like the computer sits and thinks for a full minuite before doing ANYTHING! The mouse will move, but you can't click anything. Only wait for the dialog to come up.

Cheers for the help.

---

### Post by David1965 on 2008-02-02
I had the same problem with 7.10, but I tried 8.04 today and it works ok, at least on my machine.

---

### Post by MonoBrow_063 on 2008-02-02
Looks like I got a hell of a lot of downloading to do on my 512kb connection!

Cheers!

---

### Post by MonoBrow_063 on 2008-02-02
Bugger, bugger and double drat, still the same, but it's undone all the work I put into getting my ATi card working properly.

](*,)

---

### Post by chewit on 2008-02-02
I think I can answer that. I had the exact same problem. What I did, I went to 'Sessions' under prefences. I ticked the box which said power management. 

If you have this ticked, then the power management loads up during bootup. The reason it hangs, is cause the PC has to load power management first.

---

### Post by MonoBrow_063 on 2008-02-02
LOL!

Don't I look the *** now eh?

---

### Post by David1965 on 2008-02-03
> **MonoBrow_063 said:**
> Bugger, bugger and double drat, still the same, but it's undone all the work I put into getting my ATi card working properly.

](*,)

My apologies MonoBrow. I must have had power management disabled under 7.10 and because it is enabled under 8.04 the new version seemed to cure the problem. I disabled power management in 8.04 to see what would happen and the problem comes back again, so chewit is absolutely right.

Thanks chewit.

---

