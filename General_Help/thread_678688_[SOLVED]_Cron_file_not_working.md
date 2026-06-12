---
title: "[SOLVED] Cron file not working"
date: 2008-01-26
forum: General Help
---

### Post by CTenorman on 2008-01-26
Hi guys,

I'm trying to get cron to open up Miro to download videos and audio when download restrictions don't apply. On my satellite internet connection, that's 3-6am. So I wrote this script:

```
MAILTO=tenorman@frontierproductions.org
00 3 * * * miro


```

in a file called crontab.txt. I then typed 

```
crontab crontab.txt
```

Crontab gave no error when I typed the previous line. Unfortunately the program didn't load. Does anyone know what I need to do in order to get Miro loading at 3am? Thanks,

Scott

---

### Post by ayoli on 2008-01-26
> **CTenorman said:**
> Hi guys,

I'm trying to get cron to open up Miro to download videos and audio when download restrictions don't apply. On my satellite internet connection, that's 3-6am. So I wrote this script:

```
MAILTO=tenorman@frontierproductions.org
00 3 * * * miro


```

in a file called crontab.txt. I then typed 

```
crontab crontab.txt
```

Crontab gave no error when I typed the previous line. Unfortunately the program didn't load. Does anyone know what I need to do in order to get Miro loading at 3am? Thanks,

Scott

to edit your crontab, run :
```
export EDITOR="gedit" && crontab -e
```
put your line, and save. to check that your cron lines type :
```
crontab -l
```
that all, you don't have to submit any file to cron, cron will read your crontab and exec lines.

---

### Post by heindsight on 2008-01-26
Actually, ```
crontab crontab.txt
``` should work as well.
replacing ```
miro
``` with the full path to the miro executable, eg. ```
/usr/bin/miro
```

Does your machine have an MTA that can deliver messages to @frontierproductions.org adresses? If not, then replace
```
MAILTO=tenorman@frontierproductions.org
``` with
```
MAILTO=yourusername
``` or just remove the mailto line (the default behaviour is to send mail to your local user account). You might want to install something like mailx to check your local system mail.

---

### Post by CTenorman on 2008-01-28
Thanks for your help,

Unfortunately that doesn't seem to have solved the problem. My System Log reports:

```
Jan 28 03:07:01 lappie /USR/SBIN/CRON[14697]: (scott) CMD (/usr/bin/treeline)
```

So Cron is getting the job and running it, but the program doesn't seem to load. I tried treeline as I use it regularly, and know it runs without any flaw. Typing the exact code into the terminal brought the program right up, so I'm a little confused as to the problem. 

Just so you know, I also hit enter after the command in the txt file, in accord with several guides I saw online. If anyone has any further thoughts I'd appreciate them! Thanks,

Scott

---

### Post by ayoli on 2008-01-28
> **CTenorman said:**
> Thanks for your help,

Unfortunately that doesn't seem to have solved the problem. My System Log reports:

```
Jan 28 03:07:01 lappie /USR/SBIN/CRON[14697]: (scott) CMD (/usr/bin/treeline)
```

So Cron is getting the job and running it, but the program doesn't seem to load. I tried treeline as I use it regularly, and know it runs without any flaw. Typing the exact code into the terminal brought the program right up, so I'm a little confused as to the problem. 

Just so you know, I also hit enter after the command in the txt file, in accord with several guides I saw online. If anyone has any further thoughts I'd appreciate them! Thanks,

Scott

Ah just figure out that you trying to run a graphical app with cron so you need something like that at the top of your script : 
```
DISPLAY=0:0
```

---

### Post by njparton on 2008-01-28
Maybe try running it as root? Add it to root's crontab instead:

```
sudo crontab -e
```

---

### Post by ayoli on 2008-01-28
I don't think it's a matter of privileges. As I said above it is required to specify a display to let cron know where to launch a grphical app.

---

### Post by CTenorman on 2008-01-28
Unfortunately the Display=0:0 at the top of the file doesn't seem to be working. Here's how the new cronfile looks:

```
DISPLAY=0:0
51 14 * * * /usr/bin/treeline

```

My system log viewer tells me the code is still executing at the right time, but it's not showing up anywhere. I also tried running in the terminal

```
DISPLAY=0:0 /usr/bin/treeline
```

and received *treeline.py: cannot connect to X server 0:0*. I also tried running the operation as root, and received the same feedback except it said *(root)* instead of *(scott)* in the log.

Thank you for all your help so far, this is a tricky one! All the best,

Scott

---

### Post by ayoli on 2008-01-28
> **CTenorman said:**
> Unfortunately the Display=0:0 at the top of the file doesn't seem to be working. Here's how the new cronfile looks:

```
DISPLAY=0:0
51 14 * * * /usr/bin/treeline

```

My system log viewer tells me the code is still executing at the right time, but it's not showing up anywhere. I also tried running in the terminal

```
DISPLAY=0:0 /usr/bin/treeline
```

and received *treeline.py: cannot connect to X server 0:0*. I also tried running the operation as root, and received the same feedback except it said *(root)* instead of *(scott)* in the log.

Thank you for all your help so far, this is a tricky one! All the best,

Scott

try it like this:
```
51 14 * * * DISPLAY=:0 /usr/bin/treeline
```

---

### Post by CTenorman on 2008-01-28
Fantastic, it worked!! Thank you so much!!

Just one more question - how do I end the program at 6am? I know I'll have to add a new line below the existing one set for 6am, but I'm not sure what command to send.

Thank you once again, this will be immensely helpful!

Scott

---

### Post by ayoli on 2008-01-29
> **CTenorman said:**
> Fantastic, it worked!! Thank you so much!!

Just one more question - how do I end the program at 6am? I know I'll have to add a new line below the existing one set for 6am, but I'm not sure what command to send.

Thank you once again, this will be immensely helpful!

Scott
maybe just a cron line with :
```
pkill <name_of_program_to_kill>
```
you can test thjis by running your prog from the command line and the run the pkill command, if it orks it should also work with cron.

---

### Post by CTenorman on 2008-02-02
Sorry for the delay, a new computer just arrived, it took a bit of time to get it up and running. The command works perfectly, thanks for your help!

---

### Post by ayoli on 2008-02-03
> **CTenorman said:**
> Sorry for the delay, a new computer just arrived, it took a bit of time to get it up and running. The command works perfectly, thanks for your help!

glad to help :)

---

