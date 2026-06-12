---
title: "Can not shutdown PC"
date: 2014-12-08
forum: General Help
---

### Post by Jonners59 on 2014-12-08
I have an odd one here.  I can not shut down my PC.  I have tried the normal shutdown and restart keys.  I have tried using a terminal and typing ```
sudo shutdown now -h
``` or ```
sudo shutdown now -r
``` (for reboot), but none work.  It starts to shut down.  Get a load of text on the screen saying it is shutting down and then it stops.  I have to press the "hard" reset button on the front of the PC and then turn it off at the back before it reboots.

Any ideas, please?
Any cmd outputs required, please advise.

It is fully up to date on software updates and running 14.10:confused:

---

### Post by pqwoerituytrueiwoq on 2014-12-08
[FONT=courier new]reboot[/FONT] command work?
how about [FONT=courier new]poweroff[/FONT]
what about [FONT=courier new]halt[/FONT]

---

### Post by Jonners59 on 2014-12-08
No, no joy...  the last bit of text says something like "aquiring org.desktp. modemmanager.....".  "Failed"

not quite sure of the wording, but something of that nature.

Any other ideas?

---

### Post by Bashing-om on 2014-12-08
Jonners59; Hello;

I too run xfce4 - but, I have no display manager.
The command I use to shut my system down:
```

sudo shutdown -h now

``` as the proper syntax.
Pay attention to the screen for a any reported errors.

One might also look in the log files, there 'might' be something there , if logging has not been terminated by the shutdown process, before the error occurs. (/var/log)

[INDENT][INDENT]we be look'n
[/INDENT][/INDENT]

---

### Post by llamabr on 2014-12-08
sudo shutdown -h now

Yes, I'd be interested to hear if putting them the other way around does solve the problem.

---

### Post by Jonners59 on 2014-12-13
> **llamabr said:**
> sudo shutdown -h now

Yes, I'd be interested to hear if putting them the other way around does solve the problem.
OK, interesting

  [COLOR=#000000][FONT=Ubuntu Mono]sudo shutdown -h now[/FONT][/COLOR]
does not work and 

 [COLOR=#000000][FONT=Ubuntu Mono]sudo shutdown -r now
[/FONT][/COLOR]
does work
I also have a bug out and have been asked to try a couple of commands...  Shall report back.

PS:  Anyone know how I make these "with sudo" launch in a launcher rather than terminal.  I want to create a panel launcher for the rest of the family to use.  I don't mind if they have to type the password, but rather they didn't.  At the moment nothing seems to happen.  I assume because it is happening in the background and awaiting the password.

---

### Post by sudodus on 2014-12-13
Test with a desktop file **filename.desktop** containing

```
[Desktop Entry]
Version=1.0
Type=Application
Name=Shutdown
Comment=move swap & grow root partition
[COLOR=#ff0000]Exec=xterm -hold -e sudo parted -l[/COLOR]
[COLOR=#ff0000]Icon=/usr/share/icons/nuoveXT2/48x48/actions/system-shutdown.png[/COLOR]
Path=/root
Terminal=false
StartupNotify=false
```

If it works you can edit the Exec line to get the command you want
 and maybe the Icon line (to get the icon you want)

```
[Desktop Entry]
Version=1.0
Type=Application
Name=Shutdown
Comment=move swap & grow root partition
**[COLOR=#800080]Exec=xterm -e sudo poweroff[/COLOR]**
[COLOR=#ff0000]Icon=/usr/share/icons/nuoveXT2/48x48/actions/system-shutdown.png[/COLOR]
Path=/root
Terminal=false
StartupNotify=false
```

Use whichever command that works

```
xterm -e sudo poweroff
xterm -e sudo reboot
xterm -e sudo shutdown -P now  # uppercase P
xterm -e sudo shutdown -h now
xterm -e sudo shutdown -r now

```

after Exec= (on the same line)

See ```
man shutdown
``` and ```
man poweroff
```

---

### Post by Jonners59 on 2015-01-01
OK, sorted...  The problem I believe was "nomodeset" and or "acpi=off" in GRUB.  After taking these out it seemed to start working...  I had already updated to latest kernel, but I do not think that that was the solution as previous shutdowns had not worked.

---

### Post by Bashing-om on 2015-01-01
> **Jonners59 said:**
> OK, sorted...  The problem I believe was "nomodeset" and or "acpi=off" in GRUB.  After taking these out it seemed to start working...  I had already updated to latest kernel, but I do not think that that was the solution as previous shutdowns had not worked.

Great !

A good service to us all in that you provided the solution. Yes, ACPI Affects many things.

[INDENT][INDENT]happy trails to you
[/INDENT][/INDENT]

---

