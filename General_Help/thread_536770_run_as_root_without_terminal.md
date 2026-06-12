---
title: "run as root without terminal"
date: 2007-08-28
forum: General Help
---

### Post by will71110 on 2007-08-28
Is there a way to do a "run as" without opening terminial and sudo? There are some scripts I like to run from time to time off my desktop that  has to run under root.  The scripts access files that normal users do not have access to run.

---

### Post by PmDematagoda on 2007-08-28
Have you tried through recovery mode?

---

### Post by will71110 on 2007-08-28
Recovery mode?

Not sure why that would help me in this instance?

I dont want to log in as root.  Just want to run some programs right off the desktop by clicking on them.

---

### Post by Lord Illidan on 2007-08-28
> **will71110 said:**
> Is there a way to do a "run as" without opening terminial and sudo? There are some scripts I like to run from time to time off my desktop that  has to run under root.  The scripts access files that normal users do not have access to run.

You can't use sudo for that? As in prefix the script command with sudo?

---

### Post by will71110 on 2007-08-28
Ok that works too.....Just have to put in the password everytime.

---

### Post by wormser on 2007-08-28
You can right click on the desktop and Create Launcher.  If the program requires root access I do not think there is any way around not using sudo if you need root privileges.  You can use gksudo in the command and you will get the authentication screen pop up for your password.

---

### Post by will71110 on 2007-08-28
Well it's not a program. Just scripts.  One of them connects my bluetooth mouse.  My mouse has a power save mode and will disconnect from the bluetooth and I have to maually reconnect it.


I have found that I can only sudo hidd -scan and that is what my script is doing now.

---

### Post by Lord Illidan on 2007-08-28
Perhaps the command would be gnome-terminal --comand sudo hidd -scan ?

---

### Post by will71110 on 2007-08-28
> **Lord Illidan said:**
> Perhaps the command would be gnome-terminal --comand sudo hidd -scan ?

That didnt do anything,  just came up with a blank terminal.  

The command I have in the script does work, just was wondering if there was a different way to run it with out doing a password every time.  But using sudo, there is no way around that.

---

### Post by YoG%*@ on 2007-08-28
hi

maybe this thread can help:
[http://ubuntuforums.org/showthread.php?t=19236](http://ubuntuforums.org/showthread.php?t=19236)

mux

---

### Post by tmahmood on 2007-08-28
gksudo <your_command>

this will ask your password in a Graphical Dialog box and without the terminal, you _have_to_ provide the password manually, as far as I remember.

---

### Post by will71110 on 2007-08-28
I tried that.  It popped up a screen then it went away...Nothing happened :(

THey other way works, ask for pass in terminal.  Thats ok...I can live with that for now :)

---

