---
title: "How to load .xmodmap at logon"
date: 2007-02-22
forum: General Help
---

### Post by pombe on 2007-02-22
Hi there.  

I'm sure there is an easy way to do this, but google has failed me.  

I've got my machine set up to automatically log into an account and launch mythtv.   I've configured the .xmodmap file with all the key functions I want on my remote wonder II, but I'm finding that I need to go "xmodmap .xmodmap" in the terminal to get the remote to work.  How do I launch the custom map automatically?

Thanks

Corey

---

### Post by nereid on 2007-02-22
Depends on what you use. With GNOME you just write this bash script

```

#!/bin/bash

xmodmap ~/.xmodmap

```

and add it to the session manager. With KDE you also write the bash script and put it into the ~/.kde/Autostart folder.

---

### Post by pombe on 2007-02-22
Thanks for the reply.  Here is where my noobie-ness comes out...

Can you explain "add it to the session manager"?   Is that an option through the Ubuntu desktop?  95% of the linuxy stuff that I've done has been command line, so I havent explored much within the desktop environment.   

Is this script just automatically run from a particular folder?  Which one? 

Thanks

Corey

---

### Post by nereid on 2007-02-22
Ok, the session manager is a GNOME system util which allows you to, as the name implies, manage your GNOME session. It will list all running programs and allows you to add a program to it, which will be started at the beginning of your GNOME session.

In my example the script was saved to your home folder also known in the command line as ~ (the tilde symbol). Just save the aforementioned script to your homefolder and give it to xmodmap as a command option (open up your favorite text editor and paste the code from my first post into it, then save it as .xmodmap in your home folder).

Hope I haven't forgotten anything and covered it all ;)

---

### Post by pombe on 2007-02-22
hrm.  I'm a little slow today.   do I put your two lines of script at the top of the .xmodmap file that I've got all my remote control codes in?  (which is also called .xmodmap...)

---

### Post by po0f on 2007-02-22
pombe,

Navigate to System->Preferences->Sessions.  Click on the "Startup Programs" tab.  Click "New" and add "xmodmap ~/.xmodmap" as the command to run.

---

### Post by nereid on 2007-02-23
> **pombe said:**
> hrm.  I'm a little slow today.   do I put your two lines of script at the top of the .xmodmap file that I've got all my remote control codes in?  (which is also called .xmodmap...)

No, your .xmodmap file contains all your keychanges. The script will be saved to another file, the name doesn't matter. But as *po0f* said you don't need the extra script. The session manager is capable of starting the xmodmap command with the commandline parameter without a hitch (haven't used GNOME for some years ;) ).

---

