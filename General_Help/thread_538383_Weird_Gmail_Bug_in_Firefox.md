---
title: "Weird Gmail Bug in Firefox"
date: 2007-08-29
forum: General Help
---

### Post by bpont on 2007-08-29
For some reason, when I'm in Gmail, the following line of code shows up in place of what should be links to go to different google services, as well as the sign out link:

```
function (d) { return RW(N(a), b, d, c); }
```

I have more than one Gmail account and if I am using any one of two out of the three accounts, the above line of code shows up, but for one of my Gmail accounts, everything is normal.

I've tried clearing all the private data (cookies, etc.) as well as rebooting and even uninstalling and reinstalling firefox, but nothing seems to work!  I'm at a loss as to how to fix things.  As it stands now, I have to manually clear all private data and then go to Gmail to log into a different account, because there is no sign out link...just that weird code.

Any suggestions would be welcomed.

---

### Post by kerry_s on 2007-08-30
try it with firefox in safe-mode. in a terminal type> firefox -safe-mode <
if it works than there's something wrong with a extension your using or your profile is corrupt.

---

### Post by bpont on 2007-08-30
> **kerry_s said:**
> try it with firefox in safe-mode. in a terminal type> firefox -safe-mode <
if it works than there's something wrong with a extension your using or your profile is corrupt.

Great advice...I started in safe mode and it indeed removed the problem.  Now how do I determine which extension is flaky or if my profile is corrupt and how do I delete it and create a new one with the same settings?  Thanks.

---

### Post by kerry_s on 2007-08-30
> **bpont said:**
> Great advice...I started in safe mode and it indeed removed the problem.  Now how do I determine which extension is flaky or if my profile is corrupt and how do I delete it and create a new one with the same settings?  Thanks.

the long process is to disable the extensions 1 by 1 till you find the culprit, that is if it even is a extension. the settings folder is hidden in your home directory, you just open nautilus & press ctrl+h to see the hidden files, then just delete the .mozilla 1, or in terminal> rm -rf ~/.mozilla
then just start firefox and it will create a brand new 1.

**make sure you save anything you want to keep first, for example you might want to export your bookmarks, so you can import them back.  **

---

