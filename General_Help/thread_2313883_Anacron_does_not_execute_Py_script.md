---
title: "Anacron does not execute Py script"
date: 2016-02-16
forum: General Help
---

### Post by Luca_Brasi on 2016-02-16
Hello! I put my Python script to /etc/cron.daily and set chmod 711. Owner of this script is root. 
If i try to execute it via manually (./ script) - everything is OK. But anacron do nothing with my script. Why?

---

### Post by ian-weisser on 2016-02-16
What does your script do, and how does your script do it?
What is your script named within /etc/cron.daily, and why did you choose different permissions from every other cron job in that dir?

---

### Post by Luca_Brasi on 2016-02-17
1. My script download files from FTP, via WGET.
2. It named remote_backup.py. I created symlink to that script within /etc/cron.daily. 
```

cd /etc/cron.daily
ls -l | grep remote
#Below is output with name of myfile
lrwxrwxrwx 1 root root    33 &#1060;&#1077;&#1074; 13 20:45 remote_backup -> /home/andrew/bin/remote_backup.py 
```
3. I chose this permission, cause this file contain private info for connection (login, pass etc.)

---

### Post by ian-weisser on 2016-02-17
Does your script set a working directory? Cron doesn't know where your '~' is.
Are you testing your script as root? Cron runs the script as root.
Does your script provide any feedback to the screen? Won't work with cron.

---

### Post by Luca_Brasi on 2016-02-17
[ATTACH]remote_backup.py[/ATTACH]
there is not feedback to the screen. All paths is absolute. I execute it under root, it works normally

---

### Post by ian-weisser on 2016-02-17
Are there any error messages in syslog when it runs?

---

### Post by Luca_Brasi on 2016-02-18
no warning messages, errors etc. I really dont understand how it can be. How can i know which else scripts executes from this folder(cron.daily)?

---

### Post by Luca_Brasi on 2016-02-21
I tried to copy this script into /etc/cron.hourly/ Cron execute it normally... Maybe do i have some troubles with anacron?

---

### Post by ian-weisser on 2016-02-21
Anacron does not normally check hourly jobs. See /etc/anacrontab

---

### Post by Luca_Brasi on 2016-02-22
i have found interesting thing. From -run-parts manual:
>  " If  neither  the --lsbsysinit option nor the --regex option is given then the names must consist entirely of ASCII upper- and lower-case letters, ASCII digits, ASCII underscores, and ASCII minus-hyphens." I delete previous file, and put new. remote_backup. This did not help. After i rename 'remote_backup -> rbackup' and it work, but why? Does "ASCII underscores" deny?

---

