---
title: "scripting help notify send"
date: 2020-05-21
forum: General Help
---

### Post by rburkartjo on 2020-05-21
can this be done and if so could you give
me an example. i want to make a script using notify-send or yad put it in crontab and make the output (example time to run this) appear on the DESKTOP when it runs./tks

---

### Post by TheFu on 2020-05-21
[https://www.thegeekstuff.com/2010/12/ubuntu-notify-send/](https://www.thegeekstuff.com/2010/12/ubuntu-notify-send/) has some examples, but not using cron.

Looks like this tool is tied to a GUI session. Cron doesn't know anything about GUI sessions.  Using cron to interface directly with desktop interfaces or GUI programs is a bad idea. If there isn't a session to contact, the behavior is ... let's say ... undefined.

What could be done is to have cron modify/create a file when a specific action is desired, then have a desktop process monitor that file from time to time and take action.  The existence of the file would be the trigger. Have a tiny script check for the file existence every 5 minutes or 120 or 30 seconds. If the specific file exists, delete the file and post the notification.  I'd make the filename unique and create it in /tmp/$USER-$PID something like that. If you want to put a message to be displayed into the file, then the notify-send could display that too.

Perhaps if you describe what it is you really want to be notified about, we could suggest other alternatives to cron?  

For example, I use taskspooler to submit long-running batch tasks and limit how many can run concurrently.  If I need something to happen at a specific time and know exactly how long it will require, like recording a TV show, then I'll use 'at'.  At is part of cron, but for 1-time tasks.  Cron and at send any generated output to the user's email address on the system.  I use email for notifications of all sorts.  It isn't in my face, but still ends up in a place where I'll see it, when I have time.  I abhor those popup notifications, find them too distracting, especially when I'm in a work "zone" being highly productive.

Of course, your needs are probably completely different.

---

### Post by rburkartjo on 2020-05-21
tks fu. i have tried for years to get it to work. i know i could make a notify-send script and put in the startup folder and have it startup every time i opened ubuntu but i need it to open at certain times on the desktop.

---

### Post by TheFu on 2020-05-21
> **rburkartjo said:**
> tks fu. i have tried for years to get it to work. i know i could make a notify-send script and put in the startup folder and have it startup every time i opened ubuntu but i need it to open at certain times on the desktop.

What about using an alarm-clock-applet? It has a "start application" option on completion, which could easily call notify-send for a display if the alarm/music wasn't sufficient attention.  It supports countdown timers, specific times for alarm, and lists of each.  Point-n-click for most of the setup.

---

### Post by rburkartjo on 2020-05-22
fu thats a good idea. which one would you recommend

---

### Post by rburkartjo on 2020-05-22
fu finally  figured out to get the google calendar to work in 20.04. had to install the gnome calendar than sync it with google calendar..so can add reminders directly

---

### Post by rburkartjo on 2020-05-24
fu also got the kalarm app to work it offers option for desktop notification

---

