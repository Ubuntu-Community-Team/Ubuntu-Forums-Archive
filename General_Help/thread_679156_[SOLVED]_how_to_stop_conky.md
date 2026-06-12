---
title: "[SOLVED] how to stop conky?"
date: 2008-01-26
forum: General Help
---

### Post by JohnnyBoy022 on 2008-01-26
i used "conky" in the terminal to start conky. How do I kill the process? I looked in system monitor and there was no conky process. I also tried typing "killall conky" in the terminal but it said no process was killed. Any help?

---

### Post by knopper67 on 2008-01-26
Press Alt-F2 and type killall conky

And if it still doesn't work add the "force quit" applet to the panel and try using that.

---

### Post by JohnnyBoy022 on 2008-01-26
No luck. I tried that in the terminal (if you read my post) and it said no process was killed.

---

### Post by knopper67 on 2008-01-26
Try finding the process in the system monitor (System >> Administration >> System Monitor) And see if you can kill it from there. If you cant find it trying putting "sudo" right before killall conky in the terminal.

---

### Post by JohnnyBoy022 on 2008-01-26
I tried it with sudo, same thing. I don't see the process in the system monitor

---

### Post by JohnnyBoy022 on 2008-01-26
OK I think i found the problem, I feel really stupid. The process was getting killed but conky was still showing up on the desktop. I guess whatever controls that isn't refreshing or something. But when I start conky again it works fine, and I only need to do this to edit my .conkyrc file, so problem is solved.

---

### Post by p_quarles on 2008-01-26
> **JohnnyBoy022 said:**
> I tried it with sudo, same thing. I don't see the process in the system monitor
What all is conky displaying? I have a little trouble believing that conky is running if the system says it isn't. If you want to post a screenshot, that might help.

EDIT:> **JohnnyBoy022 said:**
> OK I think i found the problem, I feel really stupid. The process was getting killed but conky was still showing up on the desktop. I guess whatever controls that isn't refreshing or something. But when I start conky again it works fine, and I only need to do this to edit my .conkyrc file, so problem is solved.
Okay, sounds like it was just a screen refresh problem.

---

### Post by knopper67 on 2008-01-26
Did you remember to go to "View >> All processes" in the system monitor? If it still not working you should log out, log back in and Reinstall conky. Be sure to delete your conky configuration as well to make sure that's not causing the problem.

EDIT: Ooops didn't see your last post...

---

### Post by JohnnyBoy022 on 2008-01-27
knopper67, going to system monitor and selecting view all processes allowed me to see the conky process. Thanks for the help.

---

