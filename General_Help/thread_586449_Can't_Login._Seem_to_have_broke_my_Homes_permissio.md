---
title: "Can't Login. Seem to have broke my Homes permissions"
date: 2007-10-22
forum: General Help
---

### Post by Squiffy on 2007-10-22
I seem to have accidentally set my Home folders permissions so as to give me no access to it, thereby stopping me from logging in. I can log in from another account but its set as non administrative so its not super helpful.

any ideas on how i would go about setting my permissions back to something usable from here?

EDIT: I've attached a screeny to illustrate the problem.

---

### Post by GrammatonCleric on 2007-10-22
From another account that has the ability to sudo run the following against your home directory.
```

sudo chown -R luke:luke /home/luke

```

Then

```


sudo chmod -R 700 /home/luke


```-GC

---

### Post by Squiffy on 2007-10-22
Nope, no luck. All I've got to work with is a single non administrative account. I chucked that into terminal and tried logging in again but I got the same session lasted less than ten seconds error.

I'd chuck in the xsession-errors file but i cant get at it.

Thanks for giving it a go though!

---

### Post by GrammatonCleric on 2007-10-22
Ok....lets try...

Reboot your system.  When you see the "GRUB Loading"  press the ESC button.

Using the arrow keys select the newest kernel version for "recovery mode" and press enter.

Once the system boots you should be able to run the commands i supplied earlier on your home directory.

-GC

---

### Post by Squiffy on 2007-10-22
Wheeey! Worked like a charm! 

Thanks for the assist!


EDIT: On further fiddle I've now run into the problem of Amarok not starting properly because its not running dcopserver, whatever that means. A couple of minutes of googling leads me to believe its another permissions problem. I don't suppose I could impose on you once more for a little bit more help?

EDIT EDIT: I've popped a screeny of the error message in here in case anyone can help me understand it.

---

### Post by GrammatonCleric on 2007-10-22
Try running...
```

sudo chown -R luke:luke *

```
from within your home directory.   I think the issue is with your .kde directory.  Check to make sure that you own the .kde directory, subdirectories and files

-GC

---

### Post by 1337455 10534 on 2007-10-22
For a dcopserver errror (i got it every time i ran a kde app in Feisty, fixed in Gutsy), just Alt+F2 and
```

dcopserver

```

---

### Post by Squiffy on 2007-10-22
Sweet, I'd actually fixed this about 10 minutes before you posted using the exact same command but your help has been super appreciated!

I'm lovin' this community more by the day.

---

