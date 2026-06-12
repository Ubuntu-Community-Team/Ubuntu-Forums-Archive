---
title: "Kill a Running Process After Closing It's Window?"
date: 2015-04-06
forum: General Help
---

### Post by Garchomps on 2015-04-06
I have a program that its process won't stop after I close it. How can I kill the process after the window closes. Is it feasible using something like devilspie to run a command once it closes?

---

### Post by v3.xx on 2015-04-06
```
killall **name-of-program**
```
should do it

---

### Post by Garchomps on 2015-04-06
> **v3.xx said:**
> ```
killall **name-of-program**
```
should do it
Yes, but I'd like to run this command everytime I ex out the programs window automatically. Any ideas how?

---

### Post by v3.xx on 2015-04-06
Yes, I have done this with chrome and firefox.  Chrome seems to always leave open processes.  Firefox will do this on occasion.  So I created a panel button to clean/close both firefox and chrome, using a custom apps launcher (add to panel).  One click and both are cleaned out and closed.  So instead of using the 'X' to close the window, I click on my custom button.
```
killall chrome firefox
```

---

### Post by Garchomps on 2015-04-06
Anything that doesn't require a taskbar shortcut?

---

