---
title: "Xauthority not writeable?"
date: 2006-08-29
forum: General Help
---

### Post by handy on 2006-08-29
Serious mistake deleting those files with X in them.

I used synaptic to get rid of compiz/xgl.  I seem to have taken some of X too... :( 

I can't use synaptic now, I get the following error:

[B]Failed to run /usr/sbin/synaptic
Unable to copy the user's Xauthorisation file.[/B]

Any help appreciated...

---

### Post by Ramses de Norre on 2006-08-29
What are the permissions on ~/.Xauthority? And maybe you can reinstall x-window-system-core, that should pull all necessary X packages as dependency.

---

### Post by handy on 2006-08-29
> **Ramses de Norre said:**
> What are the permissions on ~/.Xauthority? And maybe you can reinstall x-window-system-core, that should pull all necessary X packages as dependency.

Thanks for the reply.

Is root both owner & group.

Owner rw 

600

I tried sudo apt-get install x-window-system-core

Was told everything is upto date?

It seems I have lost all root access inside of Gnome, but sudo still works in the terminal!?

Anything I try as root from the GUI I find I'm locked out?? :confused:

---

### Post by Ramses de Norre on 2006-08-29
Your .Xauthority file should be owned by yourself with 600 permissions, so ```
sudo chown `whoami`:`whoami` ~/.Xauthority
``` should fix it.

---

### Post by handy on 2006-08-29
Thankyou :KS **Ramses de Norre**:KS 

I really did not want to spend today reinstalling everything...

Having opened a couple of things that I was locked out of before, it's looking VERY good! :mrgreen:

I don't understand what I did to cause it, is the only thing perplexing me now? :confused:

---

### Post by handy on 2006-08-30
I still had to login from the terminal, & startx!
I reconfigured xorg & it got worse, so I've done a reinstall!

I have a separate /home drive, so it is some what quicker... :rolleyes: 

Thanks again for your valuable help though **Ramses de Norre** I learned from you. :KS

---

### Post by itsjustarumour on 2007-01-19
> **Ramses de Norre said:**
> Your .Xauthority file should be owned by yourself with 600 permissions, so ```
sudo chown `whoami`:`whoami` ~/.Xauthority
``` should fix it.

Thanks for that, I had the same problem, and this fixed it!!  :KS  :KS  :KS

---

### Post by nadamsieee on 2007-06-12
I tried the **sudo chown `whoami`:`whoami` ~/.Xauthority** trick, but it did not help. :(

```
$ gksu "update-manager -c"
$ home/nate/.Xauthority' to '/tmp/libgksu1.2-FuNcAg': Permission denied
```

Any ideas?

---

### Post by zebtonson on 2008-03-25
I received the .Xauthority not writeable error while trying to log in using putty, i had X forwarding with MIT magic cookie enabled.   After changing the permissions posted earlier, it still came up with the same error.  But i did find that if i log in with putty having disabled X forwarding it error went away and then i could re enable it and everything worked out fine.  Hope this helps.

---

