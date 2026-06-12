---
title: "Cron, hourly job but as a normal user?"
date: 2007-12-14
forum: General Help
---

### Post by bazzer on 2007-12-14
Hi
I've searched, but can't see the answer.

I need to run a script hourly. The script must be run as the user currently logged in, not root. I understand I can copy a script into the cron.hourly folder and it will run as the root user, but this isn't what I need.

I don't want to have to set this up using crontab, as it means logging in and fiddling, I'm hoping to set this up as part of a script to 'install' ubuntu, so that the user has this script running right from the off, no intervention required.

Anyone got any ideas?

(BTW the script is a desktop background changer, uses gconftool-2 and hence must be run as the user logged in otherwise it's ineffective)

---

### Post by r-mo on 2007-12-14
use the command 
```
crontab -e
```
then type in a new line
```
00 * * * * /path/to/script.sh
```
press ctrl+o to save and ctrl+x to exit the text editor (assuming you haven't changed the default editor from nano)
this will execute /path/to/script.sh every hour

You can check your cron jobs with
```
crontab -l
```

If you want to run a gui app you'll need to put this before the command
```
DISPLAY=:0 && 
```

---

### Post by bazzer on 2007-12-16
> **bazzer said:**
> 
I don't want to have to set this up using crontab, as it means logging in and fiddling, 

:rolleyes:

---

### Post by r-mo on 2007-12-16
Ooops, sorry, didn't see that bit.  I still think crontab is the way to go though.  

Could you add a crontab command to there session that just read in the values from a file?

```
crontab [filename]
```

where the file contains
```

# m h  dom mon dow   command
00 * * * * /path/to/script.sh

```

It would overwrite their current settings (unless you wrote something to use the output of crontab -l)

---

### Post by bazzer on 2007-12-16
yeah I did think of trying that but crontab only likes being invoked and used in interactive mode I think - after I'd done it I did crontab -l and it was empty.

I want to be able to drop the script in the cron.hourly folder and have it run as the current user, really.

---

### Post by bazzer on 2008-01-03
ok, managed to do this by writing the script to a location then importing it as described. Thanks to all.

---

### Post by g2g591 on 2008-01-03
easy gui app for adding cron jobs- Kcron, you can even run it with gksu and add crontasks for every user, even root

---

