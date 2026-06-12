---
title: "Monitor Stops Working"
date: 2008-03-12
forum: General Help
---

### Post by 2madmax on 2008-03-12
During boot up, (fiesty fawn) most current release, my monitor shuts down and I have to restart several times before I can get to the desktop screen. What is causing this to happen?
Also, I have a second hard drive attached to my system whish the computer sees, but I can not do anything with it. I have tried using Qparted, to format this drive, but it says I am not the root user. How can this happen when I am the ONLY user on this system?

Thank you!

---

### Post by todlangweilig on 2008-03-12
I'm not sure about the first thing, but are you sure the screen saver isn't kicking in? I've had that happen on Gutsy Gibbon. Perhaps your video card resolution isn't compatible with your monitor? I'm really not sure about this. 

Have you tried this from the command line?
```
gksudo qparted
``` 

See [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo") for more information.

---

