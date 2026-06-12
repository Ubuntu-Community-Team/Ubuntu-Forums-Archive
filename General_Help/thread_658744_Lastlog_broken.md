---
title: "Lastlog broken"
date: 2008-01-05
forum: General Help
---

### Post by Ertai87 on 2008-01-05
OK, so it appears that my lastlog is, to quote my friend who helped me with it, "borked".  I ran chkrootkit this evening, and it came up telling me that my common user account has apparently never logged in.  I proceeded to check my lastlog, and apparently neither has any other user account.  I checked my w output, and that works fine, as well as my who output, but my lastlog appears to be broken.  I tried grep lastlog /etc/pam.d/*, and the output was /etc/pam.d/login:session    optional   pam_lastlog.so, which is apparently normal (i.e. lastlog is set up and working).  When I cat lastlog, it outputs nothing.  Anyone know how to fix this?  It hasn't worked in the past (to my knowledge), so it's not something that broke overnight (to my knowledge).  My last shutdown was a force-shutdown; could that have done something?  Thanks.

---

### Post by dcstar on 2008-01-05
> **Ertai87 said:**
> 
........
 When I **cat lastlog**, it outputs nothing.  Anyone know how to fix this?  It hasn't worked in the past (to my knowledge), so it's not something that broke overnight (to my knowledge).  My last shutdown was a force-shutdown; could that have done something?  Thanks.

That is a fairly useless command unless you have created a file called "lastlog", use the command in its own:
```
lastlog
```

---

### Post by Ertai87 on 2008-01-05
The lastlog file exists in the folder.  I did cat on it just to see if it output data or nothing, and it outputted nothing, meaning it was empty.  Of course I did cat from the folder containing the lastlog file.  Also, I did lastlog by itself, which said that nobody had ever logged into this comp (apparently).

---

