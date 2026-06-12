---
title: "Cron not working"
date: 2013-10-09
forum: General Help
---

### Post by Sageth on 2013-10-09
For some reason, my tiny script won't work through cron ever since I upgraded yesterday.  It worked perfectly fine in 13.04 and also works if I run it manually.... just not automated.  

Here's the full output of my cron and script.  Note that I have it running every minute for testing purposes, but is normally 30 */2 * * *:
```
* * * * *  /media/sageth/data_drive/applications/Scripts/Shell/wallpaper-changer.sh
```

And the script:
```
#!/bin/bash
DIR="/media/sageth/data_drive/media/Backgrounds"
PIC=$(ls $DIR/*.jpg | shuf -n1)
export DISPLAY=:0 && gsettings set org.gnome.desktop.background picture-uri \"file://$PIC\"

```

What I noticed is that cron sets the variable when using 'gsettings get' but dconf editor doesn't show the change.  So... something is different in how dconf is invoked? Like I said, it worked fine until the upgrade and it continues to work fine if I run it in a prompt and have been unable to determine cause.  Any help or thoughts would be appreciated.

Edit: I also tried explicit paths and no variables straight into my user crontab and that didn't work either (but continues to work when running manually).  
```
* * * * * /usr/bin/gsettings set org.gnome.desktop.background picture-uri \"file://$(/bin/ls /media/sage/data_drive/media/Backgrounds/*.* | /usr/bin/shuf -n1)\"
```

---

### Post by ian-weisser on 2013-10-10
What was upgraded?
Look in /var/log/dpkg.log to find out.

---

### Post by Sageth on 2013-10-10
Sorry, I wasn't clear.  I upgraded from 13.04 to 13.10 (which went well and was a clean update with no errors, as far as I can tell).

---

### Post by ian-weisser on 2013-10-10
Has the DISPLAY environment variable changed?

---

### Post by Sageth on 2013-10-10
No, it has not changed.  Here's my full user cron (with some stripping of irrelevant jobs):
```
sageth@desktop:~$ crontab -l
USER=sageth
HOME=/home/sageth
SHELL=/bin/bash
PATH=/sbin:/bin:/usr/sbin:/usr/bin:/home/sageth/bin
DISPLAY=:0.0
MAILTO=""
# m h  dom mon dow   command
* * * * * /usr/bin/gsettings set org.gnome.desktop.background picture-uri \"file://$(/bin/ls /media/sageth/data_drive/media/Backgrounds/*.* | /usr/bin/shuf -n1)\"
```


I've confirmed via syslog that the cron is running properly:
```
Oct 10 19:05:01 desktop CRON[20461]: (sageth) CMD (/usr/bin/gsettings set org.gnome.desktop.background picture-uri \"file://$(/bin/ls /media/sageth/data_drive/media/Backgrounds/*.* | /usr/bin/shuf -n1)\")
Oct 10 19:06:01 desktop CRON[20475]: (sageth) CMD (/usr/bin/gsettings set org.gnome.desktop.background picture-uri \"file://$(/bin/ls /media/sageth/data_drive/media/Backgrounds/*.* | /usr/bin/shuf -n1)\")
```



Last -- and I think this is key, I just don't know how to fix it -- if I run it at the command line, dconf editor and the wallpaper immediately change.
If I run it via cron, dconf editor does not reflect the change, yet running "gsettings get org.gnome.desktop.background picture-uri" does change.

I guess this means I need to ask new questions:
1.  "What is the difference between dconf editor and gsettings?"
2.  "How do I get dconf to reflect changes run via cron in 13.10 (that worked in 13.04)?"

---

### Post by wreckedred on 2013-10-30
Looking for solution also...same exact issue

---

### Post by ian-weisser on 2013-10-30
If 'get' works under cron, but 'set' does not, then I suspect you need to file a bug report.
To me it sounds like perhaps a dbus or AppArmor issue

Have you tried redirecting STDOUT and STDERR to a file for debug purposes?

Example crontab with redirection:
* * * * * command command command >/path/to/errorlog.txt 2>&1

Then you can see the errors that cron otherwise discards (the contents of errorlog.txt) and post them here.

In your case, that woulde be something like the following. You may need to tweak it a bit:
```

* * * * * /usr/bin/gsettings set org.gnome.desktop.background picture-uri \"file://$(/bin/ls /media/sageth/data_drive/media/Backgrounds/*.* | /usr/bin/shuf -n1)\" >/tmp/errorlog.txt 2>&1

```

---

### Post by wreckedred on 2013-10-30
Tried multiple solutions...this is what works for me

cron entry
```

00 6 * * * export DISPLAY=:0&& /home/drew/scripts/cron/natgeowall.sh

```

and I had to change my script to grab the DBUS_SESSION_BUS_ADDRESS environment variable

```

# export DBUS_SESSION_BUS_ADDRESS environment variable
PID=$(pgrep gnome-session)
export DBUS_SESSION_BUS_ADDRESS=$(grep -z DBUS_SESSION_BUS_ADDRESS /proc/$PID/environ|cut -d= -f2-)


/usr/bin/gsettings set org.gnome.desktop.background picture-uri file:///home/drew/Pictures/$TODAY.jpg

```

I by no means figured this out myself...I used multiple sources. Hope it helps

---

### Post by ian-weisser on 2013-10-31
That makes sense.

gsettings requires access to dbus (see man gsettings).
cron's environment does not include access to dbus.
Exporting the dbus environment to cron is necessary.

---

### Post by Sageth on 2013-11-02
This worked for me too.  Thanks wreckedred

---

