---
title: "[SOLVED] xchat opens &amp;amp; disappears immediately"
date: 2008-01-01
forum: General Help
---

### Post by despidey on 2008-01-01
I installed xchat with synaptic and it seemed to go OK.  When I click on the program, however, it executes but immediately disappears from my workspace.  Is it hiding someplace I don't know about or have I done something wrong?

---

### Post by dlegend on 2008-01-01
> **despidey said:**
> I installed xchat with synaptic and it seemed to go OK.  When I click on the program, however, it executes but immediately disappears from my workspace.  Is it hiding someplace I don't know about or have I done something wrong?

Open up your terminal and type "xchat" and press enter to execute the command. If there is any errors / issues they should be displayed in the terminal which you can copy & paste here.

Also you can type "killall xchat" to close any existing xchat applications that are running (if it is indeed running).

---

### Post by despidey on 2008-01-01
> **dlegend said:**
> Open up your terminal and type "xchat" and press enter to execute the command. If there is any errors / issues they should be displayed in the terminal which you can copy & paste here.

Also you can type "killall xchat" to close any existing xchat applications that are running (if it is indeed running).

I get this:
*Segmentation fault (core dumped)*

---

### Post by dlegend on 2008-01-01
I found the exact problem you are having via another Ubuntu topic here: [http://ubuntuforums.org/showthread.php?t=461053](http://ubuntuforums.org/showthread.php?t=461053)

**The Solution**
To enable browsing hidden folders press ctrl + h once you are in your home folder.

Remove the .xchat folder(s) from your home directory and then try to start it again. These are your xchat settings files.

---

### Post by despidey on 2008-01-01
BINGO!!  Thanks, thanks, thanks.  Worked like a charm.  Marking solved

---

