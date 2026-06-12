---
title: "Running a program at scheduled time, then stop at scheduled time?"
date: 2008-06-16
forum: General Help
---

### Post by Dr_Snapid on 2008-06-16
Hi all,

I am using motion to set my webcam up as a security camera. After much fiddling, it works.:guitar:

How can I set my computer to run the program (motion) every night at say 6pm, then stop it at say 8am? I know I can use cron to start the program, but is there a way to limit how long the program can run, or a way to stop the process using cron?

I know there is a command to kill a running process, but can i actually make it stop without 'kill'ing it?

---

### Post by steveneddy on 2008-06-16
I think **cron** is the answer.

---

### Post by Dr_Snapid on 2008-06-16
This is how i set up cron...

# m h  dom mon dow   command
0 18 * * 1,2,3,4,5 motion 
0 8 * * 1,2,3,4,5 killall motion 

should run it every weekday night, and kill it every weekday morning so it runs at night and all weekend.

---

### Post by steveneddy on 2008-06-16
[http://www.adminschoice.com/docs/crontab.htm](http://www.adminschoice.com/docs/crontab.htm)

---

