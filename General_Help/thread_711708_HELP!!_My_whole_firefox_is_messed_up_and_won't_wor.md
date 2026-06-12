---
title: "HELP!! My whole firefox is messed up and won't work!!!"
date: 2008-02-29
forum: General Help
---

### Post by Redrazor39 on 2008-02-29
I installed the Urethane light theme that worked perfectly on windows but on linux it totally screwed up my firefox web browser. I had to download the firefox 3 beta to type this, but none of my extensions work (which I REALLY need).

Whenever I open firefox 2, it's a tiny little dot on my screen and if I can find it, I'll try to resize it only to find it's a blank, white window with nothing in it that says "Mozilla Firefox" on top.

How can I fix this?

---

### Post by Bubba64 on 2008-02-29
I looked on google under urethane gutsy and ubuntu and found only one hit it looks like if it is a program that will run on your unmentioned computer type or distribution you need some plugins 
here is the one hit on several replies the downloads from mozilla are listed that will help your ubuntu system in general.
[http://forums.mozillazine.org/viewtopic.php?p=3083684](http://forums.mozillazine.org/viewtopic.php?p=3083684)
Here is a forum post on a lot of the same downloads, due to not finding any good hits with this system on Ubuntu and I think it is a beta release if it was me I would remove it.
[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)

---

### Post by Cybergod on 2008-02-29
You should be able to run firefox in safe-mode from the terminal. 

```
firefox -safe-mode
```

Once it opens you will be able to remove the theme you installed.

---

### Post by Redrazor39 on 2008-02-29
Thanks. I did a bunch of stuff with that and got it working (had to reinstall extensions, but idc)

Also, if you know, every time I start up my comp in ubuntu I have to do alt-f2 and then type ```
gtk-window-decorator --replace 
``` to get the titlebars right because I love the theme I have. How do I make it so gtk window decorator is the default and not emerald, without losing my compiz fusion effects?

---

### Post by Cybergod on 2008-02-29
I'm not sure if this will work but it's worth a try.  Open the Compiz Config Settings Manager under System - > Preferences - > CompizConfig Settings, click on 'Window Decoration', and then provide a decorator in the 'Command' field; use something like:
```
emerald --replace
```
or
```
gtk-window-decorator --replace
```

---

