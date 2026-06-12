---
title: "How do you set the Keep daemon to run at startup?"
date: 2007-07-24
forum: General Help
---

### Post by bcjtown on 2007-07-24
I have decided to use Keep as my primary backup program on Ubuntu Feisty Fawn.  I was wondering if there is a way to make the daemon start up when the machine boots?  Otherwise, I have to load it manually by starting the program.

---

### Post by zanglang on 2007-07-25
You can create a script that runs the program, put it in /etc/init.d/, and then enter the command
> sudo update-rc.d <file name> defaults
That will automatically set up the script to be run at start up.

---

