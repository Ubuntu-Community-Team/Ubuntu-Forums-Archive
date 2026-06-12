---
title: "exim paniclog has non-zero size"
date: 2020-09-28
forum: General Help
---

### Post by marchello_lippi2 on 2020-09-28
Hi all, 
Getting below message into my root mailbox:
> 
exim paniclog /var/log/exim4/paniclog on [host] has non-zero size, mail
system might be broken. The last 10 lines are quoted below.

2020-09-25 05:44:49 1kLdib-0001Qk-EK Completed
2020-09-25 05:44:49 1kLdib-0001Qk-EK Cannot open main log file
"/var/log/exim4/mainlog": Permission denied: euid=112 egid=120
How do I fix that? Please advise.

---

### Post by norobro on 2020-09-28
On my box the process runs under the Debian-exim user:```
$ ps  -p $(pgrep exim4) -o comm,euid,euser="effective_user",egid,egroup
COMMAND          EUID effective_user  EGID EGROUP
exim4             132 Debian-exim      141 Debian-exim
```Check the permissions on the directory "/var/log/exim4"```
$ ls -l /var/log/ | grep exim4
drwxr-s--- 2 Debian-exim       adm     4096 Sep 28 15:17 exim4
```
HTH

---

### Post by marchello_lippi2 on 2020-09-29
On my side it looks like this: 
> 
[FONT=monospace][COLOR=#000000]$ ps  -p $(pgrep exim4) -o comm,euid,euser="effective_user",egid,egroup[/COLOR]
COMMAND          EUID effective_user  EGID EGROUP
exim4             112 Debian-exim      120 Debian-exim
[/FONT]
> 
[FONT=monospace][COLOR=#000000]$ ls -l /var/log/ | grep exim4[/COLOR]
drwxr-s--- 2 Debian-exim adm           4096 Sep 29 05:44 [COLOR=#FF5454]**exim4**[/COLOR]
[/FONT]
> 
[FONT=monospace][COLOR=#000000]$ sudo ls -l /var/log/exim4/mainlog | grep exim4[/COLOR]
[sudo] password for user1:  
-rw-r----- 1 Debian-exim adm 10982 [/FONT][FONT=monospace]Sep[/FONT][FONT=monospace] 29 18:15 /var/log/[COLOR=#FF5454]**exim4**[/COLOR][COLOR=#000000]/mainlog[/COLOR]
[/FONT]
How do I fix that?

---

### Post by marchello_lippi2 on 2020-09-29
Upd: fixed this way: 
> [FONT=monospace][COLOR=#000000]sudo chown Debian-exim: Debian-exim /var/log/exim4/mainlog[/COLOR][/FONT] (pasted space after '[COLOR=#000000][FONT=monospace]Debian-exim:[/FONT][/COLOR]' here to avoid converting ': D' to smile symbol)
erased paniclog file content, restarted exim4. 
Will see how it will work in few days or so.

---

