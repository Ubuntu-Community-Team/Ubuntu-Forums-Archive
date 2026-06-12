---
title: "crontab -e didn't warn me of obscure problem"
date: 2019-08-08
forum: General Help
---

### Post by 7-webmaster on 2019-08-08
Ever since the original Unix the last line of a crontab must end in a new line.  If it does not the entire crontab is discarded.  This does not appear to be a customer friendly behavior but every succeeding implementation, including Ubuntu was retained this behavior, which means that inexplicably none of your cron jobs run.

According to my reading of the documentation, including "man crontab" the command "crontab -e" is supposed to issue diagnostics if there is a problem that means that the crontab will not be used.  But I recently ran "crontab -e" on Ubuntu 18.04 and it happily reported "crontab: installing new crontab" and then none of the tasks were run.

What am I not understanding?

---

### Post by TheFu on 2019-08-08
First, I've never noticed this specific issue.  I just checked my personal crontab and it didn't have an extra blank line at the end.  There are 3 tasks in it and they all work.  I'm on 16.04 across many systems. No 18.04 here, sorry.

So, I suspect that the issue in the crontab you have is not the end-of-file without an end-of-line first.
I have seen where other config files do have issues when an EOF is seen without an EOL first, so that is definitely a thing.
 
BTW, nobody here works for Canonical.

Feel free to open a bug, if you like.  
Perhaps posting the crontab would help?
If you add 1 extra, empty, line, everything works?  

There are lots of common issues, usually around assuming some environment configuration that isn't setup for cron, that makes many cronjobs fail. There should be cron specific errors in the syslog.

Any chance an MTA wasn't configured or that crond isn't running?

---

### Post by wildmanne39 on 2019-08-08
*Thread moved to **General Help a more appropriate sub-forum**.*

---

### Post by Impavidus on 2019-08-09
Every line in every text file on every UNIX-like operating system is supposed to end with a linefeed character, ASCII 0x0a, a.k.a. newline. In the UNIX world, this is considered a line terminator, not a line separator, and its presence is mandatory. If not, the text file is corrupt. Every text editor on Linux will automatically put this character at the end of every line of your text, unless you specifically tell it not to put one at the end of the final line. crontab isn't the only tool relying on the presence of the line terminators.

If crontab doesn't give you a clear error message, that may be considered a problem. However, the behaviour you object against is exactly as described in the manual:```
man crontab
...
       cron requires that each entry in a crontab end in a newline  character.
       If  the  last entry in a crontab is missing the newline, cron will con&#8208;
       sider the crontab (at least partially) broken and refuse to install it.
```

---

