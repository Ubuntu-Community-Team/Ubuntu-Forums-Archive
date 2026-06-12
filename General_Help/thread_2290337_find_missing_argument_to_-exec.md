---
title: "find: missing argument to -exec"
date: 2015-08-11
forum: General Help
---

### Post by beat5 on 2015-08-11
Hi,


i try to ad a cronjob do delete files after x days on a readynas duo from netgear. 

root permission are open.


when i try a test command for example:
find /home/ftp/cam/ -type f -maxdepth 1 -exec cp {} /home/ftp/cam/trash \;
**it works perfect at the console.**




but if i try that **as script** it says "find: missing argument to `-exec' "

#!/bin/bash
find /home/ftp/cam/ -type f -maxdepth 1 -exec cp {} /home/ftp/cam/trash \;


[B]chmod +x /bin/cam.sh
bash cam.sh
find: missing argument to `-exec[/B]


***Linux version 2.6.17.14ReadyNAS (root@calzone) (gcc version 3.3.5 (Infrant 3.3.5-1)) #1 Wed Jun 20 20:08:20 PDT 2012***


can someone help me please.

---

### Post by aromo2 on 2015-08-11
I couldn't reproduce your problem.  Try this:
1) Run [SIZE=3][FONT=courier new]**./cam.sh**[/FONT][/SIZE] instead of [SIZE=3][FONT=courier new]**bash cam.sh**[/FONT][/SIZE]
2) Try changing the exec part from [SIZE=3][FONT=courier new]**cp {} /home/ftp/cam/trash \;**[/FONT][/SIZE] to [SIZE=3][FONT=courier new]**echo {} \;**[/FONT][/SIZE]

---

### Post by beat5 on 2015-08-14
Hi aromo2,

the problem was, i saved the script under windows with vim, so it couldn't running under linux.
i use notepad++ now and made sure, that is save for unix and its working now.

thank you

---

