---
title: "Doesn't shutdown completely"
date: 2008-05-21
forum: General Help
---

### Post by erik070 on 2008-05-21
I'm kinda new to Ubuntu (have tried 7.10 for a little while), but now with my "new" laptop (2de hand) i'm going 100% for Ubuntu.

There is only 1 problem, the system doesn't shutdown completely. It shows the splash screen, and then some info about networkmanager and cifs. Then nothing, I have to manually push the powerbutton for 5 seconds to shut it down.

I don't know where to begin to look for this problem because I don't know whats causing it. Maybe there's a system log with further information, but as mentioned before I'm very new with Ubuntu and don't know where to look (looked at systemlog but it's all gibberish to me).

I've attached a photo of the last thing I see when Ubuntu shuts down.

---

### Post by superyounan1 on 2008-05-21
what happens if you shut down with this command?

```
sudo shutdown -h now
```

---

### Post by erik070 on 2008-05-21
sudo shutdown -h now didn't do the trick

Only difference (dont know if this is related to this command) is that the splash screen didn't appear in the first place. It appeared at the end for a second or so and then the cifs message appears (I guess the networkmanager message was block by the splahscreen).

---

### Post by superyounan1 on 2008-05-21
this seems related
[http://ubuntuforums.org/showthread.php?t=293513](http://ubuntuforums.org/showthread.php?t=293513)

---

### Post by erik070 on 2008-05-25
Seems that the CIFS errors weren't related to the shutdown problem. CIFS errors are gone after following the instructions in the thread Superyounan1 posted. But laptop still doesn't shutdown :confused:.

---

### Post by superyounan1 on 2008-05-27
I can't really think of anything else, don't have enough experience. Maybe its some sort of motherboard compatibility issue? Browse this site and see if you can find any references 

[http://www.linux-laptop.net/](http://www.linux-laptop.net/)

---

