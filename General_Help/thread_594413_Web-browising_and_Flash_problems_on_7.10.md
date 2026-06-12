---
title: "Web-browising and Flash problems on 7.10"
date: 2007-10-27
forum: General Help
---

### Post by TZRick on 2007-10-27
Okay,

I am having some issues with web browing:

[B]1. Flash plugin frequently crashes in Opera (the Flash applet becomes an unusable grey box after moderate activity)
2. When listening to Flash-based audio and browsing, loading links makes the Flash audio (and video) skip.[/B]
3. Firefox crashing (with and without Flash)

I've spent much of my Saturday searching for answers, and have not made much significant progress, so I am resorting to posting a new question.

As to my progress so far:
One of the items on my agenda is to reinstall Flash.  However, this has been extremely painful.  I managed to remove the package from Synaptic (9.0.48), but when I open Firefox, 9.0.31 (!!??) still shows up and I cannot find any libflashplayer.so or flashplayer.xpt files still in existence on my system.  Is anyone aware of this type of behavior?

Thanks for any feedback.

---

### Post by TZRick on 2007-10-28
Okay.  Maybe my searching wasn't as good as I thought...

I found the plugin.expose_full_path section of Firefox's about:config page and changed that to **true**.  Then I went to the about:plugins page and found the location of the remaining .so and .xpt files, which I promptly removed.  I will try this and see how it works out.

---

### Post by TZRick on 2007-10-28
Okay.  I am now running Flash 9.0.48 across the board and still having issues with audio skipping.

---

### Post by TZRick on 2007-10-28
bump...

Has anyone had issues running Flash videos and browsing?  After I standardized the Flash installation, now Opera and Firefox use the same link, now when using different browsers I am getting the skipping.  It seems that this relates to one instance of Flash being used to run all Flash videos?  I thought that Linux didn't use multiple threads, but used multiple processes instead?  In any case, I can use Flash all day long on my Windows boxes without any distortion.

Comments, anybody?

---

### Post by peddy on 2008-04-18
same here :( 

Pidgin is also crashing (unrelated I think)

---

