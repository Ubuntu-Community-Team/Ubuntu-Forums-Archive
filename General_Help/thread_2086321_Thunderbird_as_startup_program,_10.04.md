---
title: "Thunderbird as startup program, 10.04"
date: 2012-11-20
forum: General Help
---

### Post by ffixcollector on 2012-11-20
I have thunderbird as a startup program, but its not selected in the "startup aplications" its not even part of a startup script that I know of. 

The only way I can disable it is by renaming /usr/bin/thunderbird to /usr/bin/thunderbird1, and then changing the menus accordingly. This of course breaks whenever it updates.

What other methods could I have used to select thunderbird as a startup program? I'm kinda at a lost here, its been a while since I set it up. :confused:

---

### Post by ajgreeny on 2012-11-20
Have a look at the folder /etc/xdg/autostart to see if the .desktop file for thunderbird is in there, and if so remove it (as root, so using sudo).

You may also find where it is if the above does not help by running```
locate /autostart/thunderbird
``` in terminal.

---

### Post by ibjsb4 on 2012-11-20
Take a look in home .config/autostart

Im thinking thats where it was in 10o4

If you find it there, change true to false

---

### Post by ffixcollector on 2012-11-20
Not in < /etc/xdg/autostart >

< locate /autostart/thunderbird > gave me nothing

< .config/autostart > has a file called thunderbird.desktop, everything is that file is set to false.

---

### Post by ibjsb4 on 2012-11-20
Maybe

[http://ubuntuforums.org/showthread.php?t=2071854](http://ubuntuforums.org/showthread.php?t=2071854)

---

### Post by ffixcollector on 2012-11-20
I wish it was that easy, but 10.04 doesn't even have a a session manager as far as I can tell.

---

### Post by ajgreeny on 2012-11-20
> **ffixcollector said:**
> Not in < /etc/xdg/autostart >

< locate /autostart/thunderbird > gave me nothing

< .config/autostart > has a file called thunderbird.desktop, [COLOR=Red]everything is that file is set to false.[/COLOR]
What do you mean by that statement shown in red above?  What does the file actually contain if you open it with ```
gedit .config/autostart/thunderbird.desktop
``` in terminal?

---

### Post by ffixcollector on 2012-11-20
```

[Desktop Entry]
Type=Application
Exec=thunderbird %u
Hidden=false
NoDisplay=false
X-GNOME-Autostart-enabled=false
Name[en_US]=Thunderbird
Name=Thunderbird
Comment[en_US]=thunderbird %u

```

---

### Post by ajgreeny on 2012-11-21
Just try removing that thunderbird.desktop file from the ~/.config/autostart folder and thunderbird should no longer start at session startup.

I presume you must have put it there at some time in the past by adding it to the startup applications list, though I agree that the line ```
X-GNOME-Autostart-enabled=false
```would seem to suggest that autostart is disabled, as you say above.

---

### Post by ffixcollector on 2012-11-22
It was some tome ago, reading an FAQ somewhere with some sort of guide. 

Is there a services equivalent for Ubuntu that could have the thunderbird command enabled? Cron job?

---

### Post by ffixcollector on 2012-11-23
I did find this in .xsession-errors

```
gnome-session[2129]: WARNING: Could not launch application '1074ce9da1c063fcd7133920070575590300000031600048.desktop': Unable to start application: Failed to execute child process "/usr/bin/thunderbird" (No such file or directory)
```

---

