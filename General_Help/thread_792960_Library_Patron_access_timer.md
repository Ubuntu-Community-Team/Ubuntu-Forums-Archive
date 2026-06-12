---
title: "Library Patron access timer"
date: 2008-05-13
forum: General Help
---

### Post by burdsjm on 2008-05-13
I was wondering if there was a timer out there that would log out a  user and reboot the machine to allow for the next patron to log on.

Currently we are using a special paid program on a Windows workstation. I would really like to look at the possibilities of trashing Microsoft and moving to an ubuntu based system.

---

### Post by pytheas22 on 2008-05-13
This should be extremely simple; all you need is a very basic bash script.  If you wanted to reboot the machine every 15 minutes, for example, it would look like this:

```
#!/bin/bash
sleep 900;
init 6;
```

I'm sure there's also a way to make the script only run if the computer is idle, which I assume is what you want (the script above would reboot the machine every 15 minutes regardless of whether it was being used or not).  I'm not sure how to tell if it's idle but it's probably just a matter of adding a third line to the script; maybe someone else knows the utility to use.

It's sad that people actually make money off of programs to do such simple stuff as this in the Windows world.

---

### Post by pytheas22 on 2008-05-13
Or, for an even better solution, take a look at timeoutd, available in the repositories. It should allow you to do exactly what you want very easily; just specify in /etc/timeouts how long a patron's account can be idle before it gets logged out.

---

### Post by Rhubarb on 2008-05-13
This sounds to be quite easy to do.
If you want a timer displayed somewhere on the desktop,and half an hour before logging out, and you can't find any software that does this for you, then why not post in the programming section here?  You might find a generous volunteer to code a simple app up for you.

Unfortunately I'm still learning python here, so I can't be of much assistance.

---

