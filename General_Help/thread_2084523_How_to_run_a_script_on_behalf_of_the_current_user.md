---
title: "How to run a script on behalf of the current user"
date: 2012-11-15
forum: General Help
---

### Post by phu004 on 2012-11-15
Hi guys,

I have built a Ubuntu system that automatically mounts afs drive as home directory. Now the problem is the afs token gets expired after 10 hours, and  the user has to manually type "aklog" on the terminal to renew their tokens. 

I wonder if there is any way to let the system automatically renew the token for the current user? I thought about adding "aklog" command in  /etc/cron.hourly, but since this script is executed as root user&#65292;it will get rejected by the authentication server.

Thanks in advance
Pan

---

### Post by Paddy Landau on 2012-11-22
If the script is meant to be run by the user, not by root, you need to put the command into the user's cron, not root's.

I do not know how to change each user's cron without logging in to each user. However, the contents of each crontab would be like this:

```
# Prevent mailing results.
MAILTO=''

# Renew the afs token.
@hourly aklog
```The crontab manual explains how to run it (say) every 9 hours instead of hourly, if you would prefer that.
```
man 5 crontab
```

---

### Post by Lars Noodén on 2012-11-22
You can also have root call aklog via "su" or "sudo -u" to run it as a particular user.  

```

su -c /usr/bin/aklog phu004

```

This might give you the user who is logged in physically at the console:

```

U=$(who | awk 'substr($2,0,3) == "tty" {print $1}')

```

It's been a while since I've used AFS.  I hope that aklog works even if not in the same tty.

---

### Post by Paddy Landau on 2012-11-22
> **Lars Noodén said:**
> You can also have root call aklog via "su" or "sudo -u" to run it as a particular user.
Good point. You would have to run the command for each user currently logged in. The crontab entry would be something like:
```
# Do not mail results.
MAILTO=''

# Run aklog for every user currently logged in.
@hourly who  | cut --delimiter=' ' --fields=1 | sort --uniq | xargs -I {} sudo -u {} aklog
```(Please test that before putting into production.)

---

