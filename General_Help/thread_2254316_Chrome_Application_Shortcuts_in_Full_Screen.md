---
title: "Chrome Application Shortcuts in Full Screen"
date: 2014-11-26
forum: General Help
---

### Post by trivialpackets on 2014-11-26
I wasn't able to find the solution to this in the forum, so here is the situation.  I have a few applications which I would like to appear as chrome desktop applications.  IE Netflix, forecast.io, etc.  what I would like to do is to have them open up full screen when I open them.  I haven't found any documentation regarding this yet.  I imagine there may be a flag that I can add to the .desktop launcher that is located in .local/share/applications, but I am not sure of what it is yet.

Anyone ever work on this?

---

### Post by ajgreeny on 2014-11-26
Try
```
chromium-browser --kiosk http://<url>
```
It works in 12.04; I don't have google-chrome to test.

---

### Post by trivialpackets on 2014-11-26
Unfortunately, that didn't seem to work for me, or at least it did not when using the chrome-applications.  Thanks though!  I may dig a bit deeper on this later.

---

### Post by jawilljr2 on 2014-11-26
> **trivialpackets said:**
> Unfortunately, that didn't seem to work for me, or at least it did not when using the chrome-applications.  Thanks though!  I may dig a bit deeper on this later.

Try the below command:

```
google-chrome --kiosk http://www.netflix.com
```

Works for me. Of course change "http://www.netflix.com" to whatever URL you want.

---

### Post by ajgreeny on 2014-11-26
Yes, of course, I didn't mean for you to actually type <url> in that command; I assumed, perhaps wrongly, that you would understand <url>, so I apologise if that is the cause of your problem.

---

### Post by trivialpackets on 2014-11-27
lol.  Thanks!  I haven't had time to look at it yet.  And you are ok, I didn't type in <url>  :)

---

