---
title: "Cron problem"
date: 2013-09-11
forum: General Help
---

### Post by t0p on 2013-09-11
I want my computer to play a mp3, Alarum.mp3, at 9 o'clock each morning.  So I ran **crontab -e** and added the line:

```

0 9 * * * /usr/bin/totem ~/Music/Alarum.mp3

```

But at the appointed time nothing happens.

If I type into the terminal
```
 
/usr/bin/totem ~/Music/Alarum.mp3

```
totem plays the track.  Where am I going wrong entering it as a cronjob?

Cheers.

---

### Post by ajgreeny on 2013-09-11
Two problems with your command.
[LIST=1]
[*]You are truying to use a GUI application to carry out the timed job which requires you to export the command to a display so you will need ```
export DISPLAY=:0 && <command>
```
[*]I think you will need the full pathways to files you want to play with totem; I don't think cron will accept the **~/** shortcut for your home, so change that to ```
/usr/bin/totem /home/username/Music/Alarum.mp3
```
[/LIST]
Cron has only a limited range of shell actions and shortcuts available to it, so some things that will work using bash in terminal will unfortunately not work in cron, which confuses many new users.

---

### Post by Keeflookeem on 2013-11-12
Actually, I've been doing something similar for ages that has just stopped working in 13.10.

 My crontab has looked like this since Ubuntu 10.04

00 8 * * 0,1,2,3,4 env DISPLAY=:0 /usr/bin/totem /home/changeit/alarmfile.mp3

However, in 13.10, it simply opens an apport window.

---

