---
title: "Evolution reminders stay until dismissed?"
date: 2008-04-12
forum: General Help
---

### Post by nickw082 on 2008-04-12
I need to have some sort of way for reminders to pop-up in a window that wont go away until I dismiss them.

Currently in evolution a reminder will come up in the task bar and a balloon will pop up, but if I click the reminder to see what its for, the reminder will go away.  I need some way of the reminders to stay until I manually dismiss them (like how it works in outlook)

Any ideas?  I don't mind installing something to do this, I would prefer something in Evolution, but if there is no way thats ok.

---

### Post by dcstar on 2008-04-12
> **nickw082 said:**
> I need to have some sort of way for reminders to pop-up in a window that wont go away until I dismiss them.

Currently in evolution a reminder will come up in the task bar and a balloon will pop up, but if I click the reminder to see what its for, the reminder will go away.  I need some way of the reminders to stay until I manually dismiss them (like how it works in outlook)

Any ideas?  I don't mind installing something to do this, I would prefer something in Evolution, but if there is no way thats ok.

You can run external programs as an option for all Evolution alarms, just make something like this in an external executable file (I called mine "Evolution-notify") that will result in a pop-up message that will remain until you acknowledge it:

```
#!/bin/bash

zenity --warning --title="Evolution: Alarm" --text="$1" &

exit 0
```

The attached screenshots show how I tested this, you** must** put the text you want in the screen message in quotes in the "Arguments" box!


PS - I have all of my scripts like this in a directory in my /home folder - so that they are not part of the base Ubuntu system that will be lost on install/upgrade of a new distro (my /home is on a separate partition just for this sort of "insulation" from install changes).

---

