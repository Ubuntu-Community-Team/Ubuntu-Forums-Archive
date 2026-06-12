---
title: "keep having to re-add google keep to the side bar"
date: 2017-04-27
forum: General Help
---

### Post by juntjoo2 on 2017-04-27
Apparently it's the only app that the system doesn't like to keep there at least that I've tried to keep there.  Everything else has stayed. A bit strange and annoying. Would be nice if it would just stay.  Anyone know what I can do?  Thanks

---

### Post by RobGoss on 2017-04-27
You are referring to Google chrome correct?

What version of Ubuntu are you using?

---

### Post by juntjoo2 on 2017-04-27
well, I'm not sure what Chrome would have to do with it, but if so, yes I use Chrome. Is it like an extension of it or something?  And I'm using the latest I believe, 16.0.4.  Thanks

---

### Post by RobGoss on 2017-04-28
Are you trying to pin the Google chrome icon to the Unity launcher?

---

### Post by mc4man on 2017-04-28
How quickly does it (keep) disappear? Stays put here.

---

### Post by juntjoo2 on 2017-04-28
> **RobGoss said:**
> Are you trying to pin the Google chrome icon to the Unity launcher?



no, the google Keep app.  Ah, you probably missed that I was referring to the app.  Yes, that is what isn't sticking.

---

### Post by juntjoo2 on 2017-04-28
> **mc4man said:**
> How quickly does it (keep) disappear? Stays put here.


Like
a few days, or few boots of the computer. Probably something finicky about Keep

---

### Post by mc4man on 2017-04-29
> **juntjoo2 said:**
> Like
a few days, or few boots of the computer. Probably something finicky about Keep

It's done (and in the dock) from a .desktop in ~/.local/share/applications typically named chrome-xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx-Default.desktop.
If that name changes for any reason then it'll disappear from dock. Or maybe if 'keep's' app-id changes then the dock icon would also disappear.
(- the xxxxxxxx.. part of the .desktop name is the app-id & what's used on the Exec= line in the .desktop

---

### Post by juntjoo2 on 2017-04-29
thanks, I'll keep that in mind for next time it happens and check those files

---

### Post by mc4man on 2017-04-29
> **juntjoo2 said:**
> thanks, I'll keep that in mind for next time it happens and check those files

There's sometimes a couple or more chrome .desktops in there, none too specific. If you run this you can see by position which one is keep's.
```
gsettings get com.canonical.Unity.Launcher favorites
```

---

