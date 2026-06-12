---
title: "Tips for using the system logs to diagnose problems in Ubuntu?"
date: 2007-10-27
forum: General Help
---

### Post by khughitt on 2007-10-27
In an attempt to up my Ubuntu game, I want to start getting my hands dirty with diagnosing the more subtle bugs and errors I come across. 

Today I was provided with just this sort of opportunity when my system locked up out of no where are I had gone out for a couple of hours. I haven't worked with the log files for Linux much before, but I decided to start there. I went through several of the logs in the** /var/log/** directory ([COLOR="RoyalBlue"]debug, kern.log, messages, syslog and user.log[/COLOR]), however I couldn't find anything that indicated an error around the time the crash would have occurred.

Does anyone have any suggestions for diagnosing this or other similar problems? Any logs that are especially useful, or other techniques?

Any advice would be greatly appreciated.

Thanks!

---

### Post by energiya on 2007-10-27
Hi,
Watching the logs is very important (security but not only that). The things I do
 - use logwatch
 - grep is you best friend
> grep -ic "keyword" /var/log/* displays how many times keyword apears in every file (keyword=warning or error or what you want)
> grep -in "keyword" /var/log/FILE displays line number and the line where keyword appears
  - "man grep" and find more ;)
 > ls -lhSQp --color=auto /var/log check for new files/dirs and file size (huge logs = very bad - usualy)

Don't forget that all these must be done with sudo.

---

### Post by khughitt on 2007-10-27
Thanks, that is really helpful advice. grep is an amazing tool. I was even able to grep the grep output to save myself the trouble of looking for the files with >0 warnings :)

> 
hughitt1@ubuntu-desktop:~$ grep -ic "warning" /var/log/* | grep :[1-9]
/var/log/bootstrap.log:27
/var/log/daemon.log:5
/var/log/daemon.log.0:27
/var/log/syslog:3
/var/log/syslog.0:2
/var/log/Xorg.0.log:1
/var/log/Xorg.0.log.old:1
/var/log/Xorg.9.log:1


I've never heard of logwatch before-- I will check that out. what exactly does the last command do? (ls -lhSQp --color=auto /var/log). I remember reading a while back that there is a way to use the "find" command (along with possibly ls or grep), to search for files that have been modified since some time ago. Any idea how that is done? Even better would be to search for all files modified between times, then I could look for any files modified around the time of the crash.

Thanks for the advice :)

---

### Post by energiya on 2007-10-28
> **pwnedd said:**
> 
I've never heard of logwatch before-- I will check that out. what exactly does the last command do? (ls -lhSQp --color=auto /var/log). I remember reading a while back that there is a way to use the "find" command (along with possibly ls or grep), to search for files that have been modified since some time ago. Any idea how that is done? Even better would be to search for all files modified between times, then I could look for any files modified around the time of the crash.


For logwatch see [man page](http://www.linuxcommand.org/man_pages/logwatch8.html) and [web page](http://www2.logwatch.org:81/).

the "ls -lhSQp --color=auto /var/log" command (you can skip the --color part) displays the contents of the directory with a total filesize on the first line and then files on every line, sorted by file size (useful), permissions, owner, group, time and date of last modification. The "Q" option adds the quotes (security reason -- there could be " " files - thats a space char - very hard to spot with a ls command); the "p" option adds a / char after directorys. Again, you can look in ls's man page and configure the command to fit your needs. Using the find cmd to search for files modified between times? Not needed (at least not when you have a few files). The ls (with -l option) displays last modification time and date :)

---

