---
title: "request for help with rkhunter warnings"
date: 2018-08-16
forum: General Help
---

### Post by Old Jimma on 2018-08-16
Hi Community:

I've done what I can to secure my ubuntu computers and learned about rkhunter. 

This morning I ran rkunter -c from a terminal and got a few warnings, and don't know what to do with them.

Here they are:

#1:
Info: Using syslog for some logging - facility/priority level is 'authpriv.warning'.

#2
[10:08:08]   /usr/bin/lwp-request                            [ Warning ]
[10:08:08] Warning: The command '/usr/bin/lwp-request' has been replaced by a script: /usr/bin/lwp-request: Perl script text executable

#3
[10:09:20]   Checking for suspicious (large) shared memory segments [ Warning ]
[10:09:20] Warning: The following suspicious (large) shared memory segments have been found:
[10:09:20]          Process: /usr/lib/firefox/firefox (deleted)    PID: 29779    Owner: camillesmi    Size: 4.9MB (configured size allowed: 1.0MB)
[10:09:20]          Process: /usr/lib/firefox/firefox (deleted)    PID: 29779    Owner: camillesmi    Size: 4.9MB (configured size allowed: 1.0MB)

#4
[10:09:47]   Checking for passwd file changes                [ Warning ]
[10:09:47] Warning: User 'postfix' has been added to the passwd file.


#5
[10:09:47] Info: Starting test name 'group_changes'
[10:09:47]   Checking for group file changes                 [ Warning ]
[10:09:47] Warning: Group 'postfix' has been added to the group file.
[10:09:47] Warning: Group 'postdrop' has been added to the group file.

#6
Info: No mail-on-warning address configured

#7
[10:08:08]   /usr/bin/lwp-request                            [ Warning ]
[10:08:08] Warning: The command '/usr/bin/lwp-request' has been replaced by a script: /usr/bin/lwp-request: Perl script text executable

#8
[10:09:20]   Checking for suspicious (large) shared memory segments [ Warning ]
[10:09:20] Warning: The following suspicious (large) shared memory segments have been found:
[10:09:20]          Process: /usr/lib/firefox/firefox (deleted)    PID: 29779    Owner: camillesmi    Size: 4.9MB (configured size allowed: 1.0MB)
[10:09:20]          Process: /usr/lib/firefox/firefox (deleted)    PID: 29779    Owner: camillesmi    Size: 4.9MB (configured size allowed: 1.0MB)

#9
 Warning: Group 'postdrop' has been added to the group file.

[COLOR="#FF0000"]**How to I remediate these security issues??**[/COLOR]
[COLOR="#008000"][B]
Thanks,
Old Iimma from the Old Country[/B][/COLOR]

---

### Post by Yellow Pasque on 2018-08-16
> How to I remediate these security issues??
I don't see any security issues. rkhunter is a very paranoid program aimed at sysadmins with good knowledge of the inner workings of Linux. It spits out a lot of warnings for things that are no problem at all. Example:
[https://unix.stackexchange.com/questions/373718/rkhunter-gives-me-a-warning-for-usr-bin-lwp-request-what-should-i-do-debi#385904](https://unix.stackexchange.com/questions/373718/rkhunter-gives-me-a-warning-for-usr-bin-lwp-request-what-should-i-do-debi#385904)

So, if you are going to use rkhunter as an end user, you better be prepared to do a lot of googling/learning and not get too disturbed by the warnings, because 99.9% of the time, they're "false positives" and nothing to be concerned about.

---

