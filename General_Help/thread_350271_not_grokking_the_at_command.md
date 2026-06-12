---
title: "not grokking the at command"
date: 2007-01-31
forum: General Help
---

### Post by medeski on 2007-01-31
Are there specific programs that can/can't be launched by **at**?

If I run something like...
```
$ at now + 2 minutes
warning: commands will be executed using /bin/sh
at> touch ~/attest
at> xpdf
at> touch ~/attest2
at> <EOT>
```

... the result is that both **touch** commands get executed, but **xpdf** doesn't.  Why?

I've tried things like **xpdf &** instead of **xpdf,** but it doesn't make any difference.  It's not just xpdf that's the problem: things like **mpg123** launch fine, but all of the other gui programs I've tried, as well as things like **ls** and **vim**, don't get launched (or maybe they just get killed instantly!)  I couldn't find anything in the manpage about this, and google didn't help much ("at" is really a horrible command name for searching.)

---

### Post by Nik_Doof on 2007-01-31
at runs as root doesnt it? If so then xpdf doesn't have access to the current X session to create the window, hence exiting with an error.

---

### Post by medeski on 2007-01-31
Interesting, thanks.  I've set root up to have access to the current X session, but same problem.  

If what **at** does is start a new shell to launch commands, then I can understand why commands like ls and vim wouldn't work (at first, I expected them to run in the shell I launched **at** from.)  But I still don't understand why gui programs wouldn't work.

---

### Post by medeski on 2007-01-31
Actually, it looks like daemon runs atd.  I guess that's why, then.

In which case, is there any way to launch a gui program using at?

---

### Post by kpatz on 2007-01-31
Look at your DISPLAY environment variable:```
echo $DISPLAY
```It will probably be ":0.0" or something similar.  Put that in front of the command you're trying to execute with at:```
DISPLAY=":0.0" xpdf
```or```
export DISPLAY=":0.0"
xpdf
```

Also, at runs jobs as the user id that submitted the job.  So you shouldn't need to give root or daemon access to your X server.

---

### Post by medeski on 2007-01-31
Thanks, that worked beautifully.

Out of curiousity, why is it necessary?

---

### Post by kpatz on 2007-01-31
The DISPLAY variable tells X apps where to send GUI data to... the X server.  When you log into a GUI environment that variable is set in your shell, so it works fine there.  But the at command is a daemon and doesn't know what your X display is... so you have to tell it.

---

### Post by medeski on 2007-02-01
Makes sense.  Thanks!

---

