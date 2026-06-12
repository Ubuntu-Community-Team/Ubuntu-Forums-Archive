---
title: "Cron job isn't working"
date: 2013-07-04
forum: General Help
---

### Post by BaranCODE on 2013-07-04
[SIZE=2][FONT=arial]I have an sh file called m.sh with the contents:[/FONT][/SIZE]
```

[SIZE=2][FONT=arial]echo "Cleaning memory"sync; echo 3 > /proc/sys/vm/drop_cachesecho ""free -mecho ""ps cax | grep java > /dev/nullif [ $? -eq 0 ]; then  echo "== Server is already running =="else  sh a.sh  echo "========== STARTING THE SERVER =========="fi[/FONT][/SIZE]
```[SIZE=2][FONT=arial]When I run it with ```
sh m.sh
``` it works perfectly. But I need it to run every 5 minutes, so I am using cron jobs. It needs to work as root/sudo so I did ```
sudo -s
```, then ```
crontab -e
``` and wrote this in the file:[/FONT][/SIZE]
```

[SIZE=2][FONT=arial]0,4,9,14,19,24,29,34,39,44,49,54 * * * * /bin/sh /home/<username>/m.sh[/FONT][/SIZE]
```[SIZE=2][FONT=arial]I had done some research, and I learned that the cron has different paths than the user, that is why I used those absolute paths, to make sure.[/FONT][/SIZE]
[SIZE=2][FONT=arial]The cron job wasn't running the script every 5 minutes, as it was supposed to.[/FONT][/SIZE]
[SIZE=2][FONT=arial]I also added[/FONT][/SIZE]
```

[SIZE=2][FONT=arial]* * * * * /bin/echo "Testing123"[/FONT][/SIZE]
```[SIZE=2][FONT=arial]to test if cron was working at all, and nothing came up in the console.[/FONT][/SIZE]
[SIZE=2][FONT=arial]How can I make the cron run the script every 5 minutes? I did research online, and tried the solutions, but couldn't make it to work for me. I did ```
service cron start
``` and it said it was already running. I also restarted the service. The permissions are set correctly, I gave all users read, write, and execute permissions just to make sure (I know the permissions are correct).

**Update**: Solved[/FONT][/SIZE]

---

### Post by steeldriver on 2013-07-04
AFAIK cron doesn't output to the console - in fact there may not always be a console for it to attach to

You can redirect the output to a file of your choice - or use 'logger' to send output to the system log

---

### Post by CaptainMark on 2013-07-05
the best way to tell if cron is running is to use a line like```
*/5 * * * * date > /home/[user]/cron_test
```this will stamp the current date a file named cron_test in [user]'s home folder every 5 minutes
For reference, this is the sensible way to run a cron job every 5 minutes rather than 4,9,14,19 etc, just think of */5 as "Any number that divides by 5"

---

