---
title: "cron rsync output to stdout ?verbose with no -v flag?"
date: 2013-06-09
forum: General Help
---

### Post by pyrokiwi on 2013-06-09
Hi Folks

I am getting confused by what rsync seems to be outputting to my stdout when run with no -v flag.

1) I have a script which detects which of two usb hard drives is present mounts that and runs rsync without the --delete flag if it has not changed since last time and with the --delete flag if it has changes (eg I have swapped my offsite backup with my local backup). This seems to be working mostly fine. (all instances of rsync are run currently with an exclude file and -a options only (and --delete where appropriate). NO -v
2) I have this script called by cron at 3am daily (and set my default root email to one at gmail so I receive the output). This seems to be working
3) However, I get an email daily from cron at the moment that looks like this: 

[FONT=arial]Drive 1: 500gb present[/FONT]
[FONT=arial]Finished checking for drives[/FONT]
[FONT=arial]Backing up with Drive 1: 500gb[/FONT]
[FONT=arial]Last backup was with Drive 1: 500gb[/FONT]
[FONT=arial]Backing up (no deletions) with Drive 1: 500gb[/FONT]
[FONT=arial]drwxr-xr-x        4096 2013/06/08 23:22:07 .[/FONT]
[FONT=arial]-rwxrwxr-x       19968 2013/06/04 19:53:30 Thumbs.db[/FONT]
[FONT=arial]drwxrwxr-x        4096 2013/05/31 21:33:28 Lightroom Catalogue[/FONT]
[FONT=arial]drwxrwxr-x        4096 2013/05/30 06:24:42 Lightroom Catalogue/2013-05-30 0624[/FONT]
[FONT=arial, sans-serif]and continues on for an enourmous number of files

I was under the impression cron should only email be the stdout which I assumed would not include details on each file if I did not run rsync with -v?

Am I wrong about this? or is the output actually some strange cryptic list of errors with no obvious explanation? Or is something odd going on here?
I have tried searching for this but all I seem to be able to get up is millions of links explaining how to get rsync to give verbose output, not ones explaining why it seems to be giving it when I dont want it.

Cheers for any ideas or help in advance.[/FONT]

---

### Post by ahallubuntu on 2013-06-09
~

---

### Post by pyrokiwi on 2013-06-09
The script is one I wrote which does the checking. I will double check again tonight but I am fairly certain it is not the script generating that output (except for the first few lines which are expected from the script; sorry should have mentioned that). 

This evening I will post the script and check again to see that the script run normally does not give that output (I am fairly sure it wasn't but I have changed a few more things since I last checked). 

The cron entry is just running my script yes.  

Cheers for the quick response

---

### Post by pyrokiwi on 2013-06-10
Ah, thanks for pointing me back there, it is the script doing something funny, it is the rsync command that is doing it, not sure why but that I know how to start finding what the problem is.

---

