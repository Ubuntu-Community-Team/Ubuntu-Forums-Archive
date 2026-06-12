---
title: "Failure to make commands run on boot"
date: 2012-12-04
forum: General Help
---

### Post by TBhX£2760R8@nK7§r on 2012-12-04
So I want to disable bluetooth on boot, in a way I can re enable it at will. Found a[ lovely thread about it]("http://ubuntuforums.org/showthread.php?t=1585069").

```
sudo rfkill block bluetooth
``` Disables bluetooth
```
sudo rfkill unblock bluetooth
``` Re enables it

But when I put the command(without sudo, as the script is run as root anyway) in /etc/rc.local bluetooth is still enabled when start the laptop and log in.

What am I doing wrong here?

EDIT:

So this was solved by having the blueman applet not start on startup, as that was starting the bluetooth after it had been disabled. It's not terribly hard to start the blueman applet.

---

### Post by Toz on 2012-12-04
Can you post the contents of your /etc/rc.local file?

Also, what make/model is your computer?

---

### Post by TBhX£2760R8@nK7§r on 2012-12-04
/etc/rc.local file:
```
#!/bin/sh -e
#Default comments

rfkill block bluetooth

exit 0
```
It's a T500 thinkpad.

---

### Post by Toz on 2012-12-04
I believe that for thinkpads, you have to use:
```
echo disable > /proc/acpi/ibm/bluetooth
```
...instead.

---

### Post by TBhX£2760R8@nK7§r on 2012-12-04
Copying that code exactly, it still isn't disabled.

I am doing full restarts between modifying it and a test, by the way.

Also, running /etc/rc.local manually does disable the bluetooth. But so did the other command.

I'm thinking it's not a problem with the command, but a problem with running it. I just have no idea how to debug that, this is my first real attempt to use ubuntu as a main OS for working with, before now I've just worked with servers. (Where I didn't screw around much with the settings, learning little)

---

### Post by Toz on 2012-12-04
Go back to your first command in /etc/rc.local and in Settings Manager->Session and Startup->Application Autostart, uncheck the Blueman applet entry.

I wonder if something is starting it up again after you disable it.

---

### Post by TBhX£2760R8@nK7§r on 2012-12-05
If I disable the  Blueman applet entry, I can't (easily) re enable bluetooth when I need to(Which, admittedly is rarely, it's more of a thing I just want to be able to do.)

But I did try, and bluetooth is disabled on start.

I can't find any information on configuration for  the blueman applet, so I think I may just try to remember to enable it manually whenever I want bluetooth.


Many thanks for the help.

---

