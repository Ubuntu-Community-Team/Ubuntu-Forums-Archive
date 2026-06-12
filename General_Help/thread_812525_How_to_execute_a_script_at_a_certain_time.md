---
title: "How to execute a script at a certain time?"
date: 2008-05-30
forum: General Help
---

### Post by jleaker01z on 2008-05-30
I have a **remote** machine, and I want it to execute a script at a certain time (2AM).  I've tried google but I run into alot on the Linux Scheduler (that doohicky that divvies out access to the CPU, so at least I learned something ;) ) and other things that dont answer the question.  I know the solution is simple, but I just havent been able to sort it out through the crud.  Any help would be appreciated.

---

### Post by HalPomeranz on 2008-05-30
This is what the cron facility is for.  Run the command "man -s 5 crontab" and "man crontab" for some documentation on how to get started.

In a nutshell, you'll use the command "sudo crontab -e" to edit the system crontab file to schedule jobs to run as the root user at times you specify.  You want to run your script at 2am, so you'd add an entry to the crontab file like:

```

0 2 * * * /path/to/your/script

```

Any output from the script will be emailed to the user the script runs as (the root user in this case).

---

