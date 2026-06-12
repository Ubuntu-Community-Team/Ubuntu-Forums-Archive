---
title: "how do I output to a log?"
date: 2006-12-06
forum: General Help
---

### Post by harty83 on 2006-12-06
I have a cron job that is running a bash script.  I have the bash script echo a bunch of stuff throughout for debugging.  When I run the script from a console, I get the output.  How do I get the cron job to write the output to a log file?

I have tried
```
* * * * * sudo -u alan /usr/bin/web-snapshot &> /home/alan/Desktop/me.txt

```
It will create the file but not log the output from the script.

Thanks!

---

### Post by wylfing on 2006-12-06
You need two fixes to that command. First, you want to be using >> rather than &>. The second is you'll want "2>&1" at the end so as to capture stderr as well as stdout.

So try this:
```
sudo -u alan /usr/bin/web-snapshot >> /home/alan/Desktop/me.txt 2>&1
```

Edit: Also, is there a good reason to be doing this sudo? Does web-snapshot require escalated privileges to run?

---

