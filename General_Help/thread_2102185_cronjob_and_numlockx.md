---
title: "cronjob and numlockx"
date: 2013-01-06
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2013-01-06
My numlock annoyed me one too many times, so i figured i would add a cronjob so it would stop annoying me, but it does not turn my numlock on...
```
~$ crontab -l
# Edit this file to introduce tasks to be run by cron.
# 
# Each task to run has to be defined through a single line
# indicating with different fields when the task will be run
# and what command to run for the task
# 
# To define the time you can provide concrete values for
# minute (m), hour (h), day of month (dom), month (mon),
# and day of week (dow) or use '*' in these fields (for 'any').# 
# Notice that tasks will be started based on the cron's system
# daemon's notion of time and timezones.
# 
# Output of the crontab jobs (including errors) is sent through
# email to the user the crontab file belongs to (unless redirected).
# 
# For example, you can run a backup of all your user accounts
# at 5 a.m every week with:
# 0 5 * * 1 tar -zcf /var/backups/home.tgz /home/
# 
# For more information see the manual pages of crontab(5) and cron(8)
# 
# m h  dom mon dow   command
*/5 * * * * numlockx on

```
it does not turn my numlock on
```
~$ cat /var/log/syslog | tail -8
Jan  6 14:25:01 ASUS-A54C-NB91 CRON[26629]: (chad) CMD (numlockx on)
Jan  6 14:25:01 ASUS-A54C-NB91 CRON[26628]: (CRON) info (No MTA installed, discarding output)
Jan  6 14:28:41 ASUS-A54C-NB91 crontab[29704]: (chad) LIST (chad)
Jan  6 14:30:01 ASUS-A54C-NB91 CRON[30818]: (chad) CMD (numlockx on)
Jan  6 14:30:01 ASUS-A54C-NB91 CRON[30817]: (CRON) info (No MTA installed, discarding output)
Jan  6 14:31:58 ASUS-A54C-NB91 crontab[32449]: (chad) LIST (chad)
Jan  6 14:35:01 ASUS-A54C-NB91 CRON[2847]: (chad) CMD (numlockx on)
Jan  6 14:35:01 ASUS-A54C-NB91 CRON[2846]: (CRON) info (No MTA installed, discarding output)
```

---

### Post by ajgreeny on 2013-01-06
I have 5 different ubuntu family OSs running on my desktop machine and none of them has **numlockx** installed, however they all boot with numlock enabled after shutting down with numlock enabled.

That is all I have ever had to do; could it be hardware reliant?

---

### Post by pqwoerituytrueiwoq on 2013-01-06
it is not installed by default, the command works when i run it in a terminal
i am assuming i accidentally hit the key and turned it off, i am just tire of it annoying me, be it human error or not

---

### Post by Pjotr123 on 2013-01-06
On a particular machine, I had to fight quite a battle against numlockx before all was well. This is how I finally succeeded on that machine (your mileage may vary):
[https://sites.google.com/site/easylinuxtipsproject/first#TOC-Make-NumLock-turn-on-automatically](https://sites.google.com/site/easylinuxtipsproject/first#TOC-Make-NumLock-turn-on-automatically)
(item 2.6, right column)

On other machines, there was no need for the "toggle" trick at all. Computers are strange beasts. :P

---

### Post by pqwoerituytrueiwoq on 2013-01-06
i was already doing that and it works, but i think i sometimes turn it off when i miss the backspace key, which is where the cronjob comes in handy, but it does not seems to effect numlock

---

### Post by ajgreeny on 2013-01-07
This is perhaps another way to do the same thing, by either adding the command you use to /etc/rc.local, just above the "exit 0" line, or making a script with that one command and adding that to your startup applications list so it is run a session logon.

---

### Post by pqwoerituytrueiwoq on 2013-01-07
already did that system wide:
```
~$ cat /etc/xdg/autostart/numlockx.desktop 
[Desktop Entry]
Encoding=UTF-8
Version=0.9.4
Type=Application
Name=Num Lock ON
Comment=Turns NumLock on
Exec=numlockx on
OnlyShowIn=XFCE;
StartupNotify=false
Terminal=false
Hidden=false

```
i suppose i could make it run a while loop, by does it not work as a cron job?
```
sh -c 'while [ 1 -eq 1 ];do numlockx on;sleep 300;done
```'

---

### Post by steeldriver on 2013-01-07
are you doing it as a user crontab or as root? I don't know how numlockx works, but it sounds like it needs to talk to the Xserver (rather than doing stuff down at the keyboard hardware level) - usually cron doesn't have the correct environment to do that (DISPLAY, XAUTHORITY and so on not set)

---

### Post by pqwoerituytrueiwoq on 2013-01-07
> **steeldriver said:**
> are you doing it as a user crontab or as root? I don't know how numlockx works, but it sounds like it needs to talk to the Xserver (rather than doing stuff down at the keyboard hardware level) - usually cron doesn't have the correct environment to do that (DISPLAY, XAUTHORITY and so on not set)
as the regular user, note the lack of sudo in the 1st post for crontab -l

---

### Post by rnerwein on 2013-01-07
> **steeldriver said:**
> are you doing it as a user crontab or as root? I don't know how numlockx works, but it sounds like it needs to talk to the Xserver (rather than doing stuff down at the keyboard hardware level) - usually cron doesn't have the correct environment to do that (DISPLAY, XAUTHORITY and so on not set)
hi
steeldriver answer is ok - see man numlockx:
numlockx  is  a  program  to control the NumLock key [COLOR=Red]inside X11 session scripts[/COLOR].
and cron isn't running inside X !
ciao

---

### Post by pqwoerituytrueiwoq on 2013-01-07
```
*/5 * * * * sh -c 'export DISPLAY=:0.0;numlockx on'
```

---

### Post by rnerwein on 2013-01-07
> **steeldriver said:**
> are you doing it as a user crontab or as root? I don't know how numlockx works, but it sounds like it needs to talk to the Xserver (rather than doing stuff down at the keyboard hardware level) - usually cron doesn't have the correct environment to do that (DISPLAY, XAUTHORITY and so on not set)
hi
steeldriver answer is ok - see man numlockx:
numlockx  is  a  program  to control the NumLock key [COLOR=Red]inside X11 session scripts[/COLOR].
and cron isn't running inside X !
but for a hint --> if the line in your crontab looks like:
[COLOR=Lime]*/10 * * * * env DISPLAY=:0.0 /usr/bin/numlockx on
it works :-)[/COLOR]
ciao

---

