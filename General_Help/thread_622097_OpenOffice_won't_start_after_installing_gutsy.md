---
title: "OpenOffice won't start after installing gutsy"
date: 2007-11-24
forum: General Help
---

### Post by d3dtn01 on 2007-11-24
I recently did a fresh install (not an upgrade) on my laptop of ubuntu 7.04. Since then, I've tried multiple time to start openoffice, but it doesn't work. The splash screen appears for a few seconds, then an error message pops up saying "Can't start application". I used aptitude to reinstall openoffice, but I still get the same message. I've searched the forum and the web and haven't found any good advice. Ideas?

---

### Post by skyjacker on 2007-11-24
1) Try completely removing the program with this code:
```
sudo apt-get remove --purge program_name
```
Then re-install and check
2) If that doesn't work, try the "koffice" suite

---

### Post by d3dtn01 on 2007-11-24
Thanks for the advice. I did remove it then reinstall it, as you suggested, but I still get the same message when trying to load the app:

"The application cannot be started."

---

### Post by FuturePilot on 2007-11-24
Are you using Feisty 7.04 or Gutsy 7.10? Your first post and thread title are a bit confusing.

---

### Post by d3dtn01 on 2007-11-25
Sorry for the confusion. I meant gutsy 7.10. I got the version number wrong, not the code name.

---

### Post by FuturePilot on 2007-11-25
Try using the Human theme and see if it starts.

---

### Post by d3dtn01 on 2007-11-25
I tried your suggestion (change to human theme), but it still didn't work. Thanks for the idea, though.

---

### Post by FuturePilot on 2007-11-26
Hmmm. Not was I was originally thinking then. 
Could you try starting it from the terminal and post anything that shows up in the terminal?
```
oowriter
```

---

### Post by d3dtn01 on 2007-11-26
Great idea! Here's my terminal session:

```
xxx:~$ oowriter
[Java framework] Error in function createSettingsDocument (elements.cxx).javaldx failed! 
[Java framework] Error in function createSettingsDocument (elements.cxx).
** (process:5932): WARNING **: Unknown error forking main binary / abnormal early exit ...

```

One thing to note, after doing the fresh install of Gutsy, I did install the following package: j2re1.4 (1.4.2.02-1ubuntu3). Could this have messed up openoffice?

---

### Post by d3dtn01 on 2007-12-07
I removed the j2re1.4, but that didn't do anything. Am I the only person who can't launch openoffice in gutsy?

---

