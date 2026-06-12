---
title: "Startup Application not running..."
date: 2013-10-19
forum: General Help
---

### Post by jimisalt on 2013-10-19
Hi I'm trying to get a script to run at user login without success...

   ~/craftbukkit/craftbukkit.sh

The script runs from the shell either by typing 'sh ~/craftbukkit/craftbukkit.sh' or just '~/craftbukkit/craftbukkit.sh'. I have created an entry in 'Startup Applications' as follows:

   Name: Minecraft Server
   Command: sh ~/craftbukkit/craftbukkit.sh

This has created the file ~/.config/autostart/craftbukkit.sh.desktop with contents:

[Desktop Entry]
Type=Application
Exec=sh ~/craftbukkit/craftbukkit.sh
Hidden=false
NoDisplay=false
X-GNOME-Autostart-enabled=true
Name[en_GB]=Minecraft Server
Name=Minecraft Server
Comment[en_GB]=
Comment=

What am I doing wrong? Is there an error log somewhere so I can see why it's not running the script properly? TIA for any help.

---

### Post by jimisalt on 2013-10-19
I managed to achieve my aim by adding the following to my user crontab:

@reboot sh ~/craftbukkit/craftbukkit.sh

However I'd still like to know why my entry in 'Startup Applications' was not working.

---

### Post by mc4man on 2013-10-19
Don't use ~ on an Exec= line, use full path, eg. /home/username/whatever

Or place your script in a bin directory in your path & just use Exec=scriptname

---

### Post by jimisalt on 2013-10-21
Thanks, that worked. Do you know if/where I would find a log of the startup command not working? There was nothing in syslog.

---

