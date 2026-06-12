---
title: "VI, Nano not working, need to edit or can't start"
date: 2007-09-10
forum: General Help
---

### Post by bjwarshaw2 on 2007-09-10
Feisty Fawn
Dell Latitude D600 
Pentium M
512MB of RAM

I've been trying to set the good ole $PATH and I've been running into problems. I've tried it in /etc/profile, and that prevented me from logging in on restarts. No biggie -- I booted recovery mode and VIM-ed in to remove the trouble-maker. 

Most recently, I tried doing it in the bash.bashrc file, and now I've opened the can o'worms. Even in recovery mode, I can't use VI or nano. I get a "The program <% PROGRAM %> is not installed", and then all of the apt-get nonsense. Nothing seems to work. Any program I try to run generates the same message, even fsck.

Thoughts? Am I looking at a fresh install (please no)?

---

### Post by meierfra on 2007-09-10
Try this
```

/usr/bin/sudo /usr/bin/vi    bash.bashrc
```

Next time back up the file before you edit it.

---

### Post by bjwarshaw2 on 2007-09-10
Thank you so much! I will definitely back up next time, and thanks to you, I'll know how to access the files.

---

### Post by bjwarshaw2 on 2007-09-10
You don't perhaps have any suggestions for a safe way of adjusting the PATH, do you? Each way I've tried has caused similar crashes, and I'm trying to set up Adobe's Flex SDK.

Thanks again,
Brian

---

### Post by meierfra on 2007-09-10
Sorry, I never messed with PATH.  There is an easy way the add paths to  PATH,  but even that I don't   remember how to do.

---

### Post by bettlebrox on 2007-09-10
It sounded like you mucked up the PATH pretty bad! :)

Why can't you just set the PATH in you .bashrc? What have you tried to date?

If all else fails, just set the PATH from a bash shell (command line) like so:

export PATH=$PATH:/new/path/entry:/other/path/entry

If you do it this way, it will only apply to the shell you do this in.

Luck

---

### Post by avik on 2007-09-10
Try using:

[CODE]
PATH=$PATH:/whatever/you/want
export PATH
[CODE]

Notice that PATH is being appended, not replaced.

EDIT: Too late.

---

