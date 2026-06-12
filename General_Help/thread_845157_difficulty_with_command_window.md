---
title: "difficulty with command window"
date: 2008-06-30
forum: General Help
---

### Post by ornovscot on 2008-06-30
I'm having difficult with the command window.


I'm new to Ubuntu.  When I typed the command line for the OpenOffice word program, the program seemed to launch.  The command line I typed in was ooffice -writer %U   I made sure there was space between the $ and office -writer %U


Then a warning box appeared that read  /home/charles/%U does not exist.  To the left of this message was a red circle with a white horizontal line.

Is there anything else I needed to do?  I'm new to Ubuntu so I'm sure I needed to do something else.  Did I need to store the command somewhere else?


Please note that I'm able to fully launch OpenOffice.org Word from the deskstop icon.

Did I need to store that application or command line somewhere so that when I typed ooffice -writer %U in the command window that application would have fully launched?

Since I'm new to all this, I'm confused.

Any help would be much appreciated.  Thank you in advance.


Thank you in advance

---

### Post by Vadi on 2008-06-30
Why are you using the command window to launch OOo? You can just go to Applications - Office.

If you do "ooffice -writer <document>", the writer will launch and will attempt to open that document.

---

### Post by ornovscot on 2008-06-30
Thank you for your reply.

I want to do this only for practice for the time when I will be installing and using a Shoutcast server, which requires the use of the command line.

Even though it is much easier simply clicking onto the icon of the writer, writing the command into the command window and successfully launching it gets me used to using such procedures.


Are you saying, then, that if I type into the command window after the $ (followed by a space) ooffice -writer <document>, the writer will launch?

---

### Post by ChameleonDave on 2008-06-30
> **ornovscot said:**
> 

Are you saying, then, that if I type into the command window after the $ (followed by a space) ooffice -writer <document>, the writer will launch?
Don't worry about the space after the prompt.  It makes no difference.

Also, "*ooffice -writer*" is a long way of doing it.  Just type "*oowriter*"; it's shorter.

You don't need "%U" on the end either.

Just type "*oowriter*" by itself to open the application.  Put a filename after it if you want to start with a given document.  For example, if you have a file called "*Contract.rtf*" on your desktop, then enter "*oowriter ~/Desktop/Contract.rtf*".

---

### Post by t4ggs on 2008-06-30
enter [www.scribd.com](www.scribd.com) and look for guides using the command line..u can learn there a lot

---

