---
title: "Running tasks under cron/anacron"
date: 2007-02-25
forum: General Help
---

### Post by dmsynck on 2007-02-25
Hi all,

I am having trouble getting a couple of tasks to run under cron/anacron.

The two commands that I am trying to run are clamscan and chkrootkit.

When I run the following from a Bash prompt, they both run just fine.

-  clamscan -r /home -l /home/dms/Documents/clamscan_results.txt
-  sudo chkrootkit > /home/dms/Documents/rootscan_results.txt

Here are the entries in my /etc/anacrontab file

-  1  20  clamscan -r /home -l /home/dms/Documents/clamscan_results.txt

- 1  30  chkrootkit > /home/dms/Documents/rootscan_results.txt

Running clamscan from cron/anacron generates errors about illegal options, even though I know those options are valid for that command.
The chkrootkit command does not appear to run at all and does not generate any errors.

Thanks in advance.

David M. Synck

---

### Post by dcstar on 2007-02-25
> **dmsynck said:**
> Hi all,

I am having trouble getting a couple of tasks to run under cron/anacron.

The two commands that I am trying to run are clamscan and chkrootkit.

When I run the following from a Bash prompt, they both run just fine.

-  clamscan -r /home -l /home/dms/Documents/clamscan_results.txt
-  sudo chkrootkit > /home/dms/Documents/rootscan_results.txt

Here are the entries in my /etc/anacrontab file

-  1  20  clamscan -r /home -l /home/dms/Documents/clamscan_results.txt

- 1  30  chkrootkit > /home/dms/Documents/rootscan_results.txt

Running clamscan from cron/anacron generates errors about illegal options, even though I know those options are valid for that command.
The chkrootkit command does not appear to run at all and does not generate any errors.

Thanks in advance.

David M. Synck

A terminal window environment has specific paths set by the shell, cron/at knows nothing about where commands are located - use absolute paths to all command binaries/scripts.

---

### Post by bodhi.zazen on 2007-03-17
How to contact dmsynck ?

user has blocked email and PM ?

~ Beginners Team

---

### Post by bodhi.zazen on 2007-03-17
OK , I am going to deny you application for now (want to keep my list clean).

If you are interested in the Beginners team :

1. I would lilke to know a little more about you as you seem new to the forums.

2. Obviously I need some way to contact you and you have both PM and e-maiil blocked.

---

