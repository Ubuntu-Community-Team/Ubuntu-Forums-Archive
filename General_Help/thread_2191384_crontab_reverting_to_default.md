---
title: "crontab reverting to default"
date: 2013-12-02
forum: General Help
---

### Post by mbermel7 on 2013-12-02
Hey everyone. So I'm trying to create a cronjob with by running crontab -e and editing that file. However, every time I reboot, the terminal shows that I'm editing crontab.xxx1 or crontab.xxx2 and the file extension keeps changing and none of my changes are sticking because cron seems to revert to the default config file every time.

Is there any reason for this? How can I make my crontab changes stick and function?

Regards

Marcus

---

### Post by jonobr on 2013-12-02
Hello

When you commit changes in crontab it should give you a message
like saving changes to a temporary file /tmp/crontab.xHuvyc/crontab
 
Thats all part of it and Im guessing its what your seeing.

I am wondering if you are using wubi? or maybe your modifying roots crontab and not the users or vice versa

---

### Post by mbermel7 on 2013-12-06
Sorry for delayed response, studying for finals!

Yes that's what's happening. How can I get around that? Because I really want this cronjob haha.

> **jonobr said:**
> Hello

When you commit changes in crontab it should give you a message
like saving changes to a temporary file /tmp/crontab.xHuvyc/crontab
 
Thats all part of it and Im guessing its what your seeing.

I am wondering if you are using wubi? or maybe your modifying roots crontab and not the users or vice versa

---

### Post by jonobr on 2013-12-06
Hello


Just curious whats happening? Wubi or using the wrong user?

If your using wubi, you will have trouble as wubi shouldnt really be used as a full time os

cheers

---

### Post by r-senior on 2013-12-07
When you use crontab -e it creates a temporary file. Don't worry about the name of that file. When you save the temporary file, crontab saves your jobs. It actually saves it in /var/spool/cron/crontabs/<username> but you never edit that file directly. 

If you want to see what's in your crontab, use crontab -l.

Note that for your own jobs, you should use crontab -e. If you use sudo crontab -e, that edits the crontab for root.

---

### Post by ian-weisser on 2013-12-07
> **mbermel7 said:**
> none of my changes are sticking because cron seems to revert to the default config file every time.

Crontab only saves your work if you crafted a syntactically correct file - one that cron will be able to read and understand.

If you really crafted a good file, the system should respond with:
```
crontab: installing new crontab
```

If you are getting error messages at boot, please show us the entire exact error message. Context helps a lot - it tells us which process is triggering the message, and when.

---

