---
title: "Can't install anything"
date: 2014-07-24
forum: General Help
---

### Post by Kyle_Undercofler on 2014-07-24
After reinstalling Ubuntu AGAIN, I found myself unable to install anything. If I try installing Java from the USC, it pops this up:[ATTACH=CONFIG]254998[/ATTACH]
I also can't even attempt to install Freedoom. Looking at it's page, I see this:[ATTACH=CONFIG]254999[/ATTACH]Clicking "Use This Source" makes me enter my sudo password, then it does some stuff, and after that, nothing seems to happen. If anyone knows what this means and how to fix it, PLEASE tell me!

---

### Post by grumblebum2 on 2014-07-24
What release did you install?

---

### Post by Kyle_Undercofler on 2014-07-24
Ubuntu 12.04

---

### Post by nerdtron on 2014-07-24
Just passing by... have you installed all updates from the update manager and then reboot?

---

### Post by TheBigH on 2014-07-24
Another thing you might try is to open a terminal and do
```
sudo apt-get update --fix-missing
```

This occasionally works for me when I get dependency errors and things refusing to install.

---

### Post by ian-weisser on 2014-07-24
The error message is pretty clear - you seem to be trying to install a package (java) that has a dependency (libgif4) that conflicts with something you already have installed.

Generally it can't be 'fixed.' You must decide which software you want to live without. They *conflict*. It's very rare for such conflicts to occur if you install exclusively from the Ubuntu repositories. Ubuntu-supported software is compiled and tested to prevent those kinds of conflicts.

What else, exactly, did you successfully install before this error occurred?

---

### Post by Kyle_Undercofler on 2014-07-24
"Just passing by... have you installed all updates from the update manager and then reboot?"
Yes.
"Another thing you might try is to open a terminal and do
 	Code:
 	sudo apt-get update --fix-missing 
This occasionally works for me when I get dependency errors and things refusing to install."
Didn't help. :(
"The error message is pretty clear - you seem to be trying to install a  package (java) that has a dependency (libgif4) that conflicts with  something you already have installed.

Generally it can't be 'fixed.' You must decide which software you want to live without. They *conflict*.  It's very rare for such conflicts to occur if you install exclusively  from the Ubuntu repositories. Ubuntu-supported software is compiled and  tested to prevent those kinds of conflicts.

What else, exactly, did you successfully install before this error occurred?"
Only Steam, and the stuff Terminal wants me to install for it wouldn't install either. Also, this another reinstall after the one from my "Steam updates won't work!" post.

---

### Post by ian-weisser on 2014-07-25
Well, clearly reinstallation is not a useful solution for your problem.

How, exactly, did you install Steam? Software Center? terminal command? Steam Website?

If all you have installed is Steam, and then your package problems began...then uninstall Steam and see if your package problems resolve.

---

### Post by Kyle_Undercofler on 2014-07-25
Steam Website.

---

### Post by ian-weisser on 2014-07-25
Uninstall Steam.
Install everything else you want.
Then try reinstalling steam.

If there is still a conflict, then install steam from the Ubuntu Software Center (tested to work with Ubuntu systems) instead of the Steam website.

If you get an error message that you don't understand, post the entire, exact error message here. Along with exactly what you did to cause the error message.

---

