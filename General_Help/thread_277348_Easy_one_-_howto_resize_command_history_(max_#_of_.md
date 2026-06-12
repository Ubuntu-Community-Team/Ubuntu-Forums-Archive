---
title: "Easy one - howto resize command history (max # of lines)?"
date: 2006-10-14
forum: General Help
---

### Post by ebutton on 2006-10-14
Hello Fellow Humanitarians!

I'm having another memory lapse.  How do I set the number of commands remembered in history?

---

### Post by eeGhoong0ais on 2006-10-14
Edit (or create) these lines in ~/.bashrc:

```
export HISTSIZE=500 # number of lines kept in memory
export HISTFILESIZE=500 # number of lines saved in ~/.bash_history

```

---

### Post by ebutton on 2006-10-16
Thanks!  That should do it.  I was thrown off by the absence of any default values that I could have changed - so I thought there must be some other way to configure history size.

Is there a global value somewhere else?

Warm Regards,
EdB

---

### Post by eeGhoong0ais on 2006-10-16
> **ebutton said:**
> Is there a global value somewhere else?

man bash says the defaults for both are 500 - I just grepped for them in /etc/ and it seems they aren't explicitly set anywhere else. You could add them to /etc/bash.bashrc to affect all users, if that's what you want ...

---

### Post by ebutton on 2006-10-16
Thank you very much!

I've dabbled a bit with *ix systems.  It was probably /etc/bash.bashrc that I "almost remembered".  Geez, I have so very much to learn, but it's fun!

Take care.

Ed

---

### Post by ebutton on 2006-12-24
I hope that this isn't a misuse of this forum.  I just need to find out if this works:

<img src="http://www.danasoft.com/sig/edbhaiku.jpg">

I know that I can create a file with notepad that has

<html>
<img src="http://www.danasoft.com/sig/edbhaiku.jpg">
</html>

and name it with a ".html" extension and it opens fine in my browser.  But, I'm testing to see if I can use it promicuously in forum posts and whatnot.

Regards To Any Viewer,
Ed

---

