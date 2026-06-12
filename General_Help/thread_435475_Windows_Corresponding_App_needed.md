---
title: "Windows Corresponding App needed"
date: 2007-05-06
forum: General Help
---

### Post by rajeshgovindan on 2007-05-06
Searching for some serious Windows corresponding app
Need a :
1. Bandwidth monitor
2. Telnet Scripting tool (For DSL Modem D-Link DSL-502T)
3. Task Scheduler

Thanx

---

### Post by bukwirm on 2007-05-06
3. Look at "cron" (the man page is a good place to start).

---

### Post by joe.turion64x2 on 2007-05-06
For your #1 try System Monitor (menu System -> Administration -> System Monitor)

I don't know how to replace #2.

Try Evolution (the one next to Firefox), probably you'll need to configure it to read your mail too.

---

### Post by asipi on 2007-05-08
2. Telnet scripting

just for an example try:
```
./telnet.sh | telnet
```

where telnet.sh is
```
#!/bin/sh
host=127.0.0.1
port=23
login=myuser
passwd=mypw
cmd="ls /tmp"

echo open ${host} ${port}
sleep 1
echo ${login}
sleep 1
echo ${passwd}
sleep 1
echo ${cmd}
sleep 1
echo exit
```

based on this you can create your own
cheers

---

### Post by rajeshgovindan on 2007-05-09
Thanx. (asipi)

I have made the script......I just need a Task Scheduler for executing that in the terminal......

Rajesh
```
#!/bin/sh
host=192.168.1.1
port=23
login=login_id
passwd=password
cmd=reboot

echo open ${host} ${port}
sleep 1
echo ${login}
sleep 1
echo ${passwd}
sleep 1
echo ${cmd}
sleep 1
echo exit
```

---

### Post by asipi on 2007-05-09
you can setup a crontab entry for it use command crontab -e
the format is simple and understandable but if you never used it I recommend to read man crontab first

---

### Post by rajeshgovindan on 2007-05-13
Man, 

I really don't understand "cron" (I read the manual of cron atleast a 100 times)

I entered the first five columns in crontab correctly.....I got stuck in the command field

My script(i.e "telnet.sh" is in "/home")

So whats the command

Plz help

---

### Post by asipi on 2007-05-13
/home/telnet.sh

did you gave executable right for the script?
keep in mind that the envinroment what cron uses to run the commands a little bit differs from you own, so some envinromental variables could be not set if any used by your script you have to check it
it is wise to redirect the command's output to a logfile to examine what happened, what could be the reason of the failure
you can do that like this:
/home/telnet.sh >/home/telnet.sh.log

does it really in /home? rather than /home/yourusername/telnet.sh?

cheers

---

### Post by nickoli_02 on 2007-05-13
> **asipi said:**
> /home/telnet.sh

did you gave executable right for the script?
keep in mind that the envinroment what cron uses to run the commands a little bit differs from you own, so some envinromental variables could be not set if any used by your script you have to check it
it is wise to redirect the command's output to a logfile to examine what happened, what could be the reason of the failure
you can do that like this:
/home/telnet.sh >/home/telnet.sh.log

does it really in /home? rather than /home/yourusername/telnet.sh?

cheers

if you use &> instead of > you redirect both stdout and stderr to the log file ;)

---

