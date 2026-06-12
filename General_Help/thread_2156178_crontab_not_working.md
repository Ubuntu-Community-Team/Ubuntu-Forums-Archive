---
title: "crontab not working"
date: 2013-06-20
forum: General Help
---

### Post by goof on 2013-06-20
hi sorry if this is in the wrong section but i am trying to automate runnin 2 bash files at specific times the commands im using are
crontab -e
50 0-23 * * * /home/username/Desktop/file1.sh
55 0-23 * * * /home/username/Desktop/file2.sh

the problem is the first command works fine but the second never executes both are in the same path so i know the path is correct and both bash files work when double clicked but when using crontab only the first works but becouse the first works surrly my syntax is correct this is a real head wreck if anyone could shed some light would be great thanks and yes permissions on files are set

sorry found another post of simular problem but no solution however it mentioned how to outut a log file which i done and an internal error is generated. the first 2 methods in code launch selenium webdrivers and then looks for an element on page this is wht throws an error cos no webdrivers execute it cant find elements but this code works fine in ide or when run from bash file any ideaas?

i found a post on other forum suggesting to use system profile
55 0-23 * * * $HOME/.profile;/home/username/Desktop/file2.sh

but the webdrivers still failed to open? this has my head wrecked anyone know a solution

---

### Post by ahallubuntu on 2013-06-20
~

---

### Post by goof on 2013-06-20
tryed that but still cant load firefox webdrivers iv been reading that cron aint in your user acount but has its own and it might not have permission to run firefox which would seem to be my problem there seems to be a way to give it permission either in cron or in bash file but thus far all attempts have failed:( stiil googleing but if anyone knows how to do this and could give me the answer or point me to the answer that would be great thanks

---

### Post by goof on 2013-07-06
i herad you can specify in the bash file the location of firefox with 
#!/bin/bash 
PATH=/opt/firefox/bin:/usr/bin/firefox /etc/firefox /usr/lib/firefox /usr/bin/X11/firefox /usr/share/man/man1/firefox.1.gz

at the start of the file but this still doesint work does anyone know how i can fix this i have allso tryed giveing sudo privliges in bash and in crontab but still cant get it to wrok anyone have any ideas thasnk

---

### Post by steeldriver on 2013-07-06
it's going to be very difficult to help unless you post the contents of the script file - or at least the command that's failing - and the actual error message

---

### Post by goof on 2013-07-06
k sorry will do however just an update i found the gui for crontab which i didiint relize i had and if i run the task one time only for test it works but if i leave it recurring on schedual then it fails the java app im running prints time at start and this is printed to log file however nothing happens after that however like i say if i use the run once for test option it works aaaaaaaaaargh :) 
but before it runs it displays a message :

Note about working directory of executed tasks:
Recurrent tasks will be run from the home directory, one-time tasks from the directory where Gnome schedule was run from at the time of task creation (normally the home directory).

however im running several crontab jobs and only this one fails and its the only one that uses firefox webdrivers from selenium.
but it does work when just run once so could it be running from differnt directory? and if so how do you set it to allways use home or other directory ? thanks for replys

---

### Post by goof on 2013-07-06
hi the bash script is
#!/bin/bash 
java -jar "/home/user/NetBeans/project/dist/project.jar"

this works when run manually
it works when executed from crontab
it FAILS when schedualed to run at specific tme in crontab   it does start cos the log file records data but webdrivers never kick off

---

### Post by Cheesehead on 2013-07-06
You have a java problem, not a crontab problem.

Cronjobs run in a limited environment, not your user environment.

For example, you -sitting at a display- have a whole host of environment variables helping to define your display, your desktop, your preferred applications, etc. Use the 'printenv' command to see them. Cron jobs don't know anything about your environment - the system deliberately does not pass any of those variables to the cron environment. Most cron jobs don't need them.

Your problem is that your java application needs one or more of those environment variables. Passing the right variable in your crontab or script is easy to do...once you have dug through all that java code to figure out what it needs.

In the past, when this has come up, the Java application is usually looking for a screen (the DISPLAY variable, which gets assigned when you login). Of course, cron is headless - it doesn't use a screen, nor does it log you in. This example case is not a shortcoming of cron - it's an application that cannot be used unattended or headless; the wrong tool for the job.

---

### Post by goof on 2013-07-06
any sugestions on the right tool cos leaving the programme running in java in for loop is obiously not a great idea and if that is the case how come it runs when run directly in crontab for test in gui version thanks for reply

---

### Post by Cheesehead on 2013-07-06
> **goof said:**
> any sugestions on the right tool
Since you have not told us what your Java program does, we have no way to suggest a cron-compatible alternative.


> **goof said:**
>  how come it runs when run directly in crontab for test in gui version
I do not understand what you are trying to say. Please show us how you run the script directly in a crontab, and what you mean by testing 'in a gui version'.

Perhaps you mean that the scripts work properly in a terminal window, but do not work when run by cron? Of course: The terminal has all your environment variables, cron does not have those variables. Cron does not know how to use a GUI.

---

### Post by goof on 2013-07-07
SOLVED WOOPEE
i wasint importing the $display settings thingamebob updated my bash file to the ollowing and now it works perfect thanks for help not sure how i mark thread as solved the following is the bash file that works and launches firefox through crontab

#!/bin/bash 
 export DISPLAY=:0
java -jar "/home/user/NetBeans/project/dist/project.jar"

---

