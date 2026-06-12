---
title: "changing gnome startup order?"
date: 2008-01-05
forum: General Help
---

### Post by hanniph on 2008-01-05
I'm testing a devilspie thing right now and it doesn't  seem to work just due the program startup order. Devilspie loads later than it should. I've seen some posts about it but only solution I found was a  script. 

Is this the only way to change the startup order?

---

### Post by dcstar on 2008-01-06
> **hanniph said:**
> I'm testing a devilspie thing right now and it doesn't  seem to work just due the program startup order. Devilspie loads later than it should. I've seen some posts about it but only solution I found was a  script. 

Is this the only way to change the startup order?

If you are referring to something started up in the Gnome session, then I'm not sure, but in the /etc/rc2.d folder you can rename the links to change the order.

---

### Post by dlegend on 2008-01-06
You could try two things that I think may work:

**Method 1.**
a) Go to System > Preferences > Sessions.
b) Go to "Current Session" tab. Find "devilspie". Change the order to 40 (or anything less then gnome-terminal)
c) Co to "Session Options" tab. Click "Remember currently running applications".
d) Log out and back in to test it out.

**Method 2.**
a) Go to System > Preferences > Sessions.
b) In the "Startup Programs" tab click "Add" and type the following for the command: 
```

devilspie & gnome-terminal --window-with-profile=DesktopConsole

```
c) Log out and back in to test it out.

Otherwise, I'd just use the script idea as suggested. If it still doesn't work then you probably have a different problem.

---

### Post by hanniph on 2008-01-06
thanks, those methods are working.
It solved my issue  :guitar:

---

