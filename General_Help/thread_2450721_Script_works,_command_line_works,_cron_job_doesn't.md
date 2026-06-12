---
title: "Script works, command line works, cron job doesn't"
date: 2020-09-19
forum: General Help
---

### Post by DigiAngel on 2020-09-19
For the life of me I have no idea why this isn't working.  I have a desktop Ubuntu 18 that I have set to sleep after idle at 2 hours.  I have a backup job once a week that I run which lasts longer than that during the night.  In my script:

```
/usr/bin/gsettings set org.gnome.settings-daemon.plugins.power sleep-inactive-ac-timeout 0
```

I can run this all day long on cli..and in a script, but this same bit fails when used in a cronjob as the same user.  I'm lost as to why....anyone else run into this before?  Thank you.

---

### Post by dinkidonk on 2020-09-19
cron jobs are run outside the shell and with a very limited environment, some variables in the environment are required for gsettings to work. You could try to put your command into a shell script and invoke the shell from cron:

```
/bin/sh /path/to/your/script.sh
```

You could also [look at this]("https://stackoverflow.com/questions/10374520/gsettings-with-cron") for a sollution.

---

### Post by norobro on 2020-09-19
From the crontab man page:> When  executing  commands,  any  output  is  mailed to the owner of the
       crontab (or to the user named in the MAILTO environment variable in the
       crontabIf you check your local mail you should see a message that contains this:```
(process:6511): dconf-WARNING **: 07:18:01.941: failed to commit changes to dconf: Cannot autolaunch D-Bus without X11 $DISPLAY
```
Try adding "export DISPLAY=:0; " to your crontab:```
m h * * * export DISPLAY=:0; /usr/bin/gsettings ...
```

---

### Post by The Cog on 2020-09-19
I think norobro is right about the problem, but I think there is a typo there. I think it should be DISPLAY=:0, not DISPLAY:=0.
```
m h * * * export DISPLAY=:0; /usr/bin/gsettings ...
```

---

### Post by norobro on 2020-09-19
Whoops! You're right, thanks. Corrected one typo but missed that  one.

---

### Post by DigiAngel on 2020-09-20
Thanks all...I will try these out and report my results.

---

### Post by DigiAngel on 2020-09-28
Exporting the display settings was just the ticket..thank you!

---

