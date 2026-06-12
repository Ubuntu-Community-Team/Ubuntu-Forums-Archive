---
title: "Azureus cron script?"
date: 2007-11-02
forum: General Help
---

### Post by db9s on 2007-11-02
I am having problems when Gutsy upgraded. Normally I ran Azureus through a cron (kcron, the kde app that makes setting up cron tasks a lot easier). The command that I used was:
```
export DISPLAY=:1 && azureus
```

which does not work with Gutsy (but worked with Edgy).

Does anyone know what command I should be using?

---

### Post by db9s on 2007-11-04
bump

---

### Post by db9s on 2007-11-11
bump
please help

---

### Post by db9s on 2007-11-18
still nothing? doesn't anyone know? bump again

---

### Post by geirha on 2007-11-18
cron should mail you (locally) with any error message the command outputs. You can read this mail by running ```
mail
``` (a very primitive mail client) in a terminal.

---

### Post by db9s on 2007-11-19
its not that cron does not work. I am just not getting the correct command. Please help!

---

### Post by geirha on 2007-11-20
Exactly. The command cron tries to run obviously fails though, and when a command fails, cron mails the output of the command to the user. So, finding and reading those mails should help figure out why the command won't run.

---

### Post by db9s on 2007-11-20
I know my command fails. Everything else on cron runs correctly. I am looking for the right command.

---

### Post by stunner on 2007-11-21
I think what geirha is trying to say is that the error output would be useful in figuring out what the proper command would be.

However, I don't think ubuntu comes with an MTA by default.  If you can run **mail**, then this is not a problem.  If you try to run it but it's not on your system, then this is moot.

Have you tried running azureus from the command line?  What's the output if you do?

---

