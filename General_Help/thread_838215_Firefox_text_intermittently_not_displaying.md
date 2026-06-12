---
title: "Firefox: text intermittently not displaying"
date: 2008-06-23
forum: General Help
---

### Post by Phil Airtime on 2008-06-23
Hello,

I've recently installed Hardy cleanly (no upgrade). Everything's working fine, except for an intermittent problem with Firefox not displaying much of the text on a page. 

A picture speaks a thousand words, so rather than trying to describe it, here it is: [http://i29.tinypic.com/qytjpk.png](http://i29.tinypic.com/qytjpk.png)

Refreshing and force-refreshing the page does nothing to alleviate it. If a page is affected, it's affected permanently. Has anyone experienced anything similar?

---

### Post by dracayr on 2008-06-23
have you tried clearing the cache? And, even though it sounds stupid, have you tried marking the area where the text should be? maybe it's just white, as is the Background

dracayr

---

### Post by Phil Airtime on 2008-06-23
With the cache cleared and browser restarted, there's no difference. Selecting the text brings up the highlighting, but nothing inside the highlighting. The screenshot is of the Ubuntu default home page which is affected, which I think is black-on-white.

---

### Post by nikgare on 2008-06-23
You could try moving you firefox preferences - ie when firefox is *not* running:

mv  .mozilla/firefox .mozilla/firefoxold

and seeeing if that makes firefox work better

---

### Post by Phil Airtime on 2008-06-24
> **nikgare said:**
> You could try moving you firefox preferences - ie when firefox is *not* running:

mv  .mozilla/firefox .mozilla/firefoxold

and seeeing if that makes firefox work better

That hasn't done anything. I also tried clearing the font cache -- sudo fc-cache -f -v -- and then reopening Firefox, still blank. It's looking like a reinstall situation, but I've got things set up how I like them, and I really can't afford the bandwidth to download all those updates again.

---

### Post by nikgare on 2008-06-24
YOu could try changing the font in firefox's prefences, and see if that makes a difference

---

### Post by Phil Airtime on 2008-06-24
> **nikgare said:**
> YOu could try changing the font in firefox's prefences, and see if that makes a difference

That doesn't make a difference, either. There just doesn't seem to be any way of fixing this broken Firefox. I wouldn't mind if it was just the Ubuntu home page that was blank, but it's affecting a web site I'm busy building!

---

### Post by dodle on 2008-07-03
[http://ubuntuforums.org/showthread.php?t=830110]("http://ubuntuforums.org/showthread.php?t=830110")

---

