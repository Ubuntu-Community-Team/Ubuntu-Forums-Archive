---
title: "Some weird visual effects problem"
date: 2007-11-22
forum: General Help
---

### Post by Thrashers7989 on 2007-11-22
I couldn't find anyone else who had this problem...

I did a fresh install of 7.10. I had a problem with the window title bar fonts being GIGANTIC...like at least 170pt font...huge.

I was told to disable visual effects and it worked. Now I have normal title bars on my main user.

Problem is, my login screen still shows these huge gigantic fonts in the text boxes for username and password, the buttons (theme depending), and menus. When I click on a menu, it takes up the entire screen and I have to hit escape to leave the menu.

Is there a way to disable the visual effects for the login screen or is there any other way to get rid of these gigantic fonts?

---

### Post by Milk &amp; Toast &amp; Honey on 2007-11-22
Hi, do you use Intel graphic card?

If so, there's a workaround for this issue, in [this thread]("http://ubuntuforums.org/showthread.php?t=583915"), specifically [this post]("http://ubuntuforums.org/showpost.php?p=3673907&postcount=12").

---

### Post by Thrashers7989 on 2007-11-23
Fantastic!

Thanks so much. Not only did I fix the problem, but I have wonderful visual goodies that work! :)

---

### Post by Thrashers7989 on 2007-12-19
Okay, I have a new problem in this regards. Here's what happened:

1. I did a totally fresh install of 7.10 Gutsy.
2. After enabling the options (except for source code and pre-releases) in the Software Sources, I did a full system update. I restarted.
3. I installed UbuntuStudio over my Gutsy install with [this guide]("https://help.ubuntu.com/community/UbuntuStudio/UpgradingFromGutsy") with no problems. Restarted.

What's happening now is that my gigantic fonts are back to plague me, but not even editing gdm.conf is working.

This is what is in my /etc/gdm/gdm.conf
```
[server-Standard]
name=Standard server
-command=/usr/bin/X -br -audit 0 -dpi 96 
flexible=true
```

After I restart, the giant fonts return both in my login screen and my logged-in user, but gdm.conf stays the same. I also try doing the simpler method from the "Appearance" preferences. Either way, the giant fonts return after startup.

Anybody have any ideas?

---

### Post by Milk &amp; Toast &amp; Honey on 2008-05-20
Thrashers7989, I know this is a long-ago-thread, but I just saw this post (burried in my subscribed threads), and it feels itch to see this unresolved.

I hope you've fixed your problem, but in case you haven't I know where's your problem lies.

Your gdm.conf:
```

[server-Standard]
name=Standard server
**-command**=/usr/bin/X -br -audit 0 -dpi 96 
flexible=true

```


Should be:
```

[server-Standard]
name=Standard server
**command**=/usr/bin/X -br -audit 0 -dpi 96 
flexible=true

```
without the "-" (minus) sign.

---

