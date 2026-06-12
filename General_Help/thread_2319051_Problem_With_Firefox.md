---
title: "Problem With Firefox"
date: 2016-03-31
forum: General Help
---

### Post by shane_faulkinbury2 on 2016-03-31
I have Ubuntu 15.10 installed on my new laptop and I'm using Firefox 45.0.  About every 5 or 8 minutes the screen greys out and I can't do anything for about three minutes.  It's just Firefox because I'm able to go into other programs and work just fine.  Attached is a screen shot of the problem.  Do you think I should uninstall it and reinstall?  Also I have 16 GB of DDR3 so that's not the problem!

---

### Post by ajgreeny on 2016-03-31
Open a terminal next time it happens and use command top to see what is taking the resources; that may give some clue about what is going on.

---

### Post by RobGoss on 2016-03-31
Hello and welcome, I would try uninstalling it and reinstalling again it won't hurt maybe there's something wrong with that installation.

---

### Post by shane_faulkinbury2 on 2016-03-31
It seems to run fine opening it from the terminal AJ, but I will try uninstalling and reinstalling so I can just run it from my desktop.

Thanks guys

---

### Post by RobGoss on 2016-03-31
Your welcome let us know how it turns out.

---

### Post by ajgreeny on 2016-04-01
> **shane_faulkinbury2 said:**
> It seems to run fine opening it from the terminal AJ, but I will try uninstalling and reinstalling so I can just run it from my desktop.

Thanks guys
So are you saying this problem is not seen when you start FF from terminal, only when started from the menu (or dash or launchbar if using unity)?

I was not actually suggesting you start it from terminal, just open terminal when the window goes grey and then use command ```
top
``` to see what is using all your resources, which is usually the reason for a window greying out like that.

However, if FF runs OK from terminal, it gives us another piece of the jigsaw to try and figure out what's going on.

---

