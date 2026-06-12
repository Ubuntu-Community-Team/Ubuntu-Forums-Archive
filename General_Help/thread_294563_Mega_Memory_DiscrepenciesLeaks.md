---
title: "Mega Memory Discrepencies/Leaks"
date: 2006-11-06
forum: General Help
---

### Post by hbweb500 on 2006-11-06
Whenever I first installed Edgy on my Compaq Presario laptop, everything ran very nicely. I installed all my default things, and havnt installed anything since. Over the past week or so, Ive seen performance decline. Windows arent drawn very rapidly, and I can see the flicker.

Take a look at the screenshot below. The system monitor shows that only about half of my 512 MB of RAM is being used, while "top" shows that nearly all of it is being used. Whats up?

[Screenshot]("http://img392.imageshack.us/img392/1750/screenshotrr1.png")

---

### Post by po0f on 2006-11-06
hbweb500,

[Click](http://gentoo-wiki.com/FAQ_Linux_Memory_Management).

---

### Post by hbweb500 on 2006-11-06
Wow, never knew that. Free -m shows that I have about half of my memory available as cache, so all is good I guess.

I just wish I knew why the responsiveness of GTK slowed down so much after a couple of weeks, especially since I didnt change the theme or install anything new.

---

### Post by po0f on 2006-11-06
hbweb500,

Are windows drawn slowly after a fresh reboot?

---

### Post by hbweb500 on 2006-11-06
No, not really, they are all drawn fairly quickly.

Perhaps a specific application is causing this?

---

### Post by podunk on 2006-11-06
Have you checked to see if your video drivers are still working?
```
glxinfo
```

should return (at the top of all the gibberish that will printed)
direct rendering Yes

```
glxgears -printfps
```

should return at least 400 or your windows will draw very slow

---

### Post by hbweb500 on 2006-11-06
Direct rendering reports a Yes, and glxgears shows around 566 FPS. 

NOw, I should say that this is right after a fresh reboot. I shall try it again when I notice the windows being drawn slowly again.

---

