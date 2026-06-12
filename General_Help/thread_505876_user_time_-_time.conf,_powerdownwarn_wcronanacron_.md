---
title: "user time - time.conf, powerdown/warn w/cron/anacron - syntax?"
date: 2007-07-20
forum: General Help
---

### Post by TravMan63 on 2007-07-20
From the guide (fedora) - at [http://skindley.wordpress.com/2006/12/11/fedora-core-6-controlling-logins-by-time/](http://skindley.wordpress.com/2006/12/11/fedora-core-6-controlling-logins-by-time/)

----
I'll segment this question:

I have setup restrictive logon times with:
		vim /etc/security/time.conf edited to:
		
		(added at end of file)
		login|gdm;*;username;Al088-2200

		(note login PIPE gdm ;A LOWERCASE L (24hr time)')

and edited files:
root@user-laptop:~# vim /etc/pam.d/login
code inserted : account required pam_time.so

vim /etc/pam.d/gdm
code inserted: account required        pam_time.so

======> Q1		this works for gui login - but not terminal - why? (login syntax?)

----		
these following entries exist in both crontab and anacrontab:

root@user-laptop:~# vim /etc/anacrontab
root@user-laptop:~# vim /etc/crontab

```

# the warning (15 mins is good) 
15 19 *** user/usr/bin/zenity -text-info -title='Times Up'-width=474 -height-400-display=:0-filename=/home/user_zanity $

----------and---------

# the shutdown
30 19 **1-7 root shutdown -h now


```

verified that cron is running (ps aux |grep cron)
root      5252  0.0  0.0   2284   896 ?        Ss   19:14   0:00 /usr/sbin/cron

created /home/user_zenity file with notification text similar to:
****
power down in 15 mins
****		

=======>Q2 - nothing executes - do I have a syntax problem or something else?

Thank you
TM
---

===
edit
found syntax error in the usr anacron, still anacron did not execute zenity

change
15 19 *** user/usr/bin/zenity -text-info -title='Times Up'-width=474 -height-400-display=:0-filename=/home/user_zanity &

15 19 * * * /usr/bin/zenity --text-info --title="Times Up" --width=474 --height=400 --display=:0 --filename=/home/zach_zanity &

I could run this from bash and get the text to popup
note the spacing and the double "-" dashes, also the double quotes

>wonder if I had 'user' at the front or mis copied it<

---

### Post by TravMan63 on 2007-07-23
I was able to fix all but the logon to terminal (Q1) - I placed a space in the command - n/c. Perhaps it's slightly different for Ubuntu VS Fedora?

```
 (old is 1st)
login|gdm;*;username;Al088-2200
login |gdm;*;username;Al088-2200

```

I removed the shutdown command, and replaced that with a KILL command

(root crontab)
```

from:
30 19 **1-7 root shutdown -h now

to:
00 21 * * 1-6 /usr/bin/skill -KILL -u username #log off 9PM Mon-Sat
00 17 * * 7 /usr/bin/skill -KILL -u username   #log off 5PM Sun

```
note the spacing difference. (the *)

HOWEVER - the REAL kicker is not as much the syntax, as it is the METHOD
I initially used vim to edit the file; I did NOT use the crontab -e command (or crontab -e before)  ->**USING crontab -e is essential!**

For user crontab use (crontab -u username -e) (this posts the text warning - this works now)

As I stated in the previous post, I tested the syntax in terminal; that did display the warning message.

Lesson learned -> **For editing _crontab_ files, use crontab -e (or crontab -u *username* -u )**... this installs the file; there is no need to restart cron!
---
More sources:
[http://safari.oreilly.com/0738423769/ch14lev1sec2](http://safari.oreilly.com/0738423769/ch14lev1sec2)
[http://www.opengroup.org/onlinepubs/007908799/xcu/crontab.html](http://www.opengroup.org/onlinepubs/007908799/xcu/crontab.html)
[http://mkaz.com/ref/unix_cron.html](http://mkaz.com/ref/unix_cron.html)
[http://help.lockergnome.com/general/Cron-Job-Crontab-Setup-Putty-ftopict27058.html](http://help.lockergnome.com/general/Cron-Job-Crontab-Setup-Putty-ftopict27058.html)
(see oxomo guide to editing/archiving crontabs)
[http://aplawrence.com/Bofcusm/1281.html](http://aplawrence.com/Bofcusm/1281.html)
[http://anacron.sourceforge.net/](http://anacron.sourceforge.net/)
---
file location:

Crontabs are stored in:

/var/spool/cron/crontabs

and are stored per user name

---

### Post by TravMan63 on 2007-08-11
For reasons unknown - this (secuirty/time.conf and pam files) method does not work with elive gem.

A crude, but effective way is to set up a cron job to log the user out every minute :twisted:

in elive - the default editor is vi (and adminstering remotly gives me blue text on black - :mad: )

```

# crontab -e
crontab: installing new crontab
```

file contents:


```
# */1 00        * * * /usr/bin/skill -KILL -u user# do it ev minute - since can't prevent log on

*/1 00 * * * /usr/bin/skill -KILL -u user # kill starting @ 12 AM - 4:59 PM - ok times ->5 PM - 10PM
*/1 01 * * * /usr/bin/skill -KILL -u user
*/1 02 * * * /usr/bin/skill -KILL -u user
*/1 03 * * * /usr/bin/skill -KILL -u user
*/1 04 * * * /usr/bin/skill -KILL -u user
*/1 05 * * * /usr/bin/skill -KILL -u user
*/1 06 * * * /usr/bin/skill -KILL -u user
*/1 07 * * * /usr/bin/skill -KILL -u user
*/1 08 * * * /usr/bin/skill -KILL -u user
*/1 09 * * * /usr/bin/skill -KILL -u user
*/1 10 * * * /usr/bin/skill -KILL -u user
*/1 11 * * * /usr/bin/skill -KILL -u user
*/1 12 * * * /usr/bin/skill -KILL -u user
*/1 13 * * * /usr/bin/skill -KILL -u user
*/1 14 * * * /usr/bin/skill -KILL -u user
*/1 15 * * * /usr/bin/skill -KILL -u user
*/1 16 * * * /usr/bin/skill -KILL -u user
*/1 17 * * * /usr/bin/skill -KILL -u user
*/1 22 * * * /usr/bin/skill -KILL -u user
*/1 23 * * * /usr/bin/skill -KILL -u user

```

I tried the (1st) info at
[http://www.linuxquestions.org/questions/showthread.php?t=573944](http://www.linuxquestions.org/questions/showthread.php?t=573944)
but it didn't work.

---

