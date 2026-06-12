---
title: "running process for avg antivirus.."
date: 2008-02-13
forum: General Help
---

### Post by Mia_tech on 2008-02-13
I have just installed avg antivirus, but when I run the program and try to do an update, I get a permission error "need to be su"... how can I find the command line for doing an update and also to do a scan.. so I can schedule it,... is there any way to put it in my path or assigning the right permission so I can open ti without having to enter su password

thanks

---

### Post by em3raldxiii on 2008-02-13
Hmm, I am not entirely sure I know *exactly* what you are asking, but I *think* what you might want to do is run the application in su mode.  So lets pretend the command to run avg is *avg*.  So you would first kill any running instances of avg, and then,

```
gksu avg
```It would then open a wee window asking for your password, then the app will run with privelages.

Then you should be able to just do the update because any child processes should maintain the same privileges.

Now, that said, there may be security concerns with running an app like avg with admin privileges ... I will leave that to someone else with more knowledge to discuss.

Now, for anyone who hasn't seen "GKSU" before, it's considered safer to use (and more convenient) for graphical (non cli) applications.  Check the link in my signature. :D

Edit:  Erm ... why are you installing an antivirus application anyway?

---

