---
title: "Cron poweroff issue"
date: 2007-03-29
forum: General Help
---

### Post by akudewan on 2007-03-29
I have set up a cron job to shut down my PC at 7:46am. It works allright, but occasionally, the computer reboots instead of shutting down. It happens at random, every once in a while, and I can't figure out why...

This is what I found in /var/log/messages at 7:46am, when the system rebooted:
```

Mar 29 07:45:38 ranjan404 kernel: [17213994.532000] Inbound IN=eth0 OUT= MAC=00:10:b5:12:bb:f7:00:20:a6:69:c1:dc:08:00 SRC=87.205.198.147 DST=10.10.19.152 LEN=62 TOS=0x00 PREC=0x00 TTL=42 ID=36189 DF PROTO=TCP SPT=50000 DPT=57606 WINDOW=10023 RES=0x00 ACK PSH URGP=0
[COLOR="Red"]Mar 29 07:46:17 ranjan404 exiting on signal 15[/COLOR]

```

Signal 15 seems normal, since its what I get everyday...

Here's what my crontab looks like:
```

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user  command
17 *    * * *   root    run-parts --report /etc/cron.hourly
25 6    * * *   root    test -x /usr/sbin/anacron || run-parts --report /etc/cron.daily
47 6    * * 7   root    test -x /usr/sbin/anacron || run-parts --report /etc/cron.weekly
52 6    1 * *   root    test -x /usr/sbin/anacron || run-parts --report /etc/cron.monthly
# Shut down Azureus
44 7 * * * root killall -15 java
# Kill wine
45 7 * * * root killall -9 wine-preloader
# Power off
46 7 * * * root poweroff
#

```

I'm thinking I should replace "poweroff" with "/sbin/shutdown -h now" or something of that sort, but should it really make a difference?

---

### Post by dannyboy79 on 2007-03-29
i am not familar with poweroff but I am familar with shutdown and that will send all the correct signals to all running processes so you don't need any extra stuff like you have
44 7 * * * root killall -15 java
or any of that! All you would have to have in your crontab is 
46 7 * * * root shutdown -h now
you won't need to use /sbin/ etc etc because you have your  paths at the top of your crontab. also, if this is root crontab, than you don't need to run it as root. Just first su -i which will get you to be root, then type in crontab -e, add it, then save it, then exit from being root then that's it. I never knew what the difference between root crontab and my own if I run the cron job as root?? good luck

---

### Post by akudewan on 2007-03-29
Thanks, I'll give it a try.

---

### Post by akudewan on 2007-04-03
Update:

The same problem occurred with the new shutdown command as well. So I changed the shutdown time to 7:49am instead, and I haven't seen a reboot (yet).

Maybe something was interrupting the shutdown process at that time?

---

### Post by dannyboy79 on 2007-04-03
you won;'t see a reboot!, this is just suppose to shutdown the computer and that's all. if you want a reboot, you need to do

46 7 * * * root shutdown -r now
OR, to do a complete power off.
46 7 * * * root shutdown -h -P now

also, when you post back, please post the output of your crontab and let me know if it's root's crontab or yours. thanks

OR
go here ([http://www.cyberciti.biz/tips/howto-shutdown-linux-box-automatically.html](http://www.cyberciti.biz/tips/howto-shutdown-linux-box-automatically.html)) and use this example just change the time to match your desired shutdown time.

PS (gogle is your friend)

---

### Post by akudewan on 2007-04-03
> **dannyboy79 said:**
> you won;'t see a reboot!, this is just suppose to shutdown the computer and that's all. if you want a reboot, you need to do

46 7 * * * root shutdown -r now
OR, to do a complete power off.
46 7 * * * root shutdown -h -P now

also, when you post back, please post the output of your crontab and let me know if it's root's crontab or yours. thanks

OR
go here ([http://www.cyberciti.biz/tips/howto-shutdown-linux-box-automatically.html](http://www.cyberciti.biz/tips/howto-shutdown-linux-box-automatically.html)) and use this example just change the time to match your desired shutdown time.

PS (gogle is your friend)

Hi,

It's my root crontab, and I want to shutdown my PC, not reboot it.

> 
 	I have set up a cron job to shut down my PC at 7:46am. It works allright, but **occasionally, the computer reboots instead of shutting down.** It happens at random, every once in a while, and I can't figure out why...


And here's my /etc/crontab
```

# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file.
# This file also has a username field, that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user  command
17 *    * * *   root    run-parts --report /etc/cron.hourly
25 6    * * *   root    test -x /usr/sbin/anacron || run-parts --report /etc/cron.daily
47 6    * * 7   root    test -x /usr/sbin/anacron || run-parts --report /etc/cron.weekly
52 6    1 * *   root    test -x /usr/sbin/anacron || run-parts --report /etc/cron.monthly
# Shut down Azureus
47 7 * * * root killall -15 java
# Kill wine
#45 7 * * * root killall -9 wine-preloader
# Power off
49 7 * * * root shutdown -h now
#

```

---

### Post by dannyboy79 on 2007-04-03
oh, i understand now. you're saying that your change was SUCCESSFUL? see I didn't gather that from your post. i had forgot that you were trying to make it NOT reboot! also, I had mentioned that the command shutdown send the halt command to all the running init processes to you don't need:

# Shut down Azureus
47 7 * * * root killall -15 java
# Kill wine
#45 7 * * * root killall -9 wine-preloader


but you do what you like. I am glad you got it working based on my instruction to use shutdown instead of poweroff.

---

