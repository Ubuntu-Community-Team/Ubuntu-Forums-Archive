---
title: "[SOLVED] No Window Borders. Please Help!"
date: 2008-07-07
forum: General Help
---

### Post by popupblocker on 2008-07-07
ok, so I have ubuntu gutsy 7.10 running on a Dell Latitude D600. Everything works out of the box except I cannot get compiz running properly as I did in other distros. I do not have window borders for MAXIMIZED windows but I do have them for normal windows. I am confused and am in dire need for help. Thank you and please respond!

---

### Post by Victormd on 2008-07-07
What windows decorator are you using? Metacity or emerald?
in a terminal, type
```
metacity --replace
```
and see if you get the windows decoration on maximized windows. Then type
```
emerald --replace
```
and see if it works. This will let you figure out which decorator you're using (if you don't already know) and which will work with your configuration.
(sorry, had the code inverted... :))

---

### Post by popupblocker on 2008-07-07
I am using emerald and i tried what you stated and here are the results
vignesh@vignesh-laptop:~$ replace --metacity
replace: No to-string for last from-string
vignesh@vignesh-laptop:~$ replace --emerald
replace: No to-string for last from-string


Thank you for the quick reply.

sorry didnt see what you wrote...

---

### Post by popupblocker on 2008-07-07
so I am using the emerald decorator. It still doesnt work, however, I entered gtk-window-decorator --replace and it worked but I dont get the animations to work. Still need help...

---

### Post by karasuman on 2008-07-07
Try switching to a different theme in Emerald and see if you get window decorations then.  I had this issue with one of the themes I tried out.

Do you have "Window Decoration" checked under your advanced desktop effect settings?  I don't think you'd have any borders at all if you didn't, but it's worth a look, I guess.

---

### Post by PinkFloyd102489 on 2008-07-07
To get the compiz effects without using Emerald, use:

```
compiz --replace
```

---

### Post by popupblocker on 2008-07-07
thanks guys, but I got it working. I used the gtk-window-decorator instead of emerald and added it to startup sessions. I also added fusion-icon to startup so with this combination everything works out fine. Once again, LINUX OWNS!! thank you.

---

