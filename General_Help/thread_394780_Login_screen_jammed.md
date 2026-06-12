---
title: "Login screen jammed"
date: 2007-03-27
forum: General Help
---

### Post by rebelrouser9 on 2007-03-27
Hello,

I disabled the login window on the start up in order to save a bit of time but when i decided to restart the computer this one time after it jammed, ubuntu can't manage to get past the fact that it can't load the login window because I asked it not to do so in the first place...

This is what I see when the problem appears &#8230;&#8230;


(==) LogFile : "/var/log"xorg.o.log", Time sat march 24 23:50
(==) using config file "etc-/x11/xconf"

(EE)Nvidia (0) : Failed to load the nvidia kernel module
(EE) Screens found, but none have usuable configuration

Fatal server error,
no screens found.

What can i do to fix this problem?

Using the command line, is there a way to simply deactivate the command that makes ubuntu skip the login screen?


Thanks a lot,
Carlos Guerreiro

---

### Post by fanatik on 2007-03-27
Best paste the contects of the **/etc/X11/xorg.conf** file here, so we can see what's going on...

James.

---

### Post by rebelrouser9 on 2007-03-27
I'm a newbie, how do i do that?

(list the content of the etc/x11/xorg.conf file)

---

### Post by rebelrouser9 on 2007-03-27
The problem with this is that I can't even manage to make it to nautilus to open the file myself, therefore there must be a way to have access to the file with the recovery mode terminal

Isn't there a way to do so?

---

### Post by fanatik on 2007-03-28
yes, from the terminal, type

cat /etc/X11/xorg.conf

although it's quite a large file, so you won't want to be copying it out.

You pasted some errors in your 1st post, where did they come from?

---

### Post by rebelrouser9 on 2007-03-30
To answer your first question, 

I copied what appears on the error screen when i try to log on. 
from the notes that i took on a piece of paper, i type it here in the very first message

But i would like to know is what exactly should i be looking for with the 
"cat /etc/X11/xorg.conf" function.

---

