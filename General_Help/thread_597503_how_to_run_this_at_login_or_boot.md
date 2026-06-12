---
title: "how to run this at login or boot?"
date: 2007-10-30
forum: General Help
---

### Post by taisao on 2007-10-30
Hi, 

I manage to get konqueror to work with forward and backward mouse button using imwheel.

Everytime I need to type this in a terminal (konsole)
```
xmodmap /home/taisao/.Xmodmap && sudo killall /usr/bin/imwheel && imwheel
```

how do I set it so that when I login in the commands are already executed without the need to type the password?

I'm login to Kubuntu using kdm.

This is what I have tried, what didn't work.

_/etc/rc.local_
```
xmodmap /home/taisao/.Xmodmap
sudo killall /usr/bin/imwheel
imwheel

```

*or*

[U]
/etc/X11/Xsession.d/63xmodmap [/U]
```
killall imwheel
xmodmap -e "pointer = 1 2 3 6 7 4 5"
imwheel -k -p -b "67"
```

---

### Post by Thyme on 2007-10-30
What about just putting the command in an executable shell script?

#!/bin/sh
xmodmap /home/taisao/.Xmodmap && sudo killall /usr/bin/imwheel && imwheel

I think your first one was right but youm maybe needed the "#!/bin/sh" part on top of the script.

---

### Post by taisao on 2007-10-30
and where do I put that?

---

### Post by jonobr on 2007-10-30
Using the desktop you could just go to system->preferences->sessions
ON startup programs click add and select your startup script.

You could it all CLI, but I found this a nice way of kicking things off from boot

---

### Post by taisao on 2007-11-02
> **jonobr said:**
> Using the desktop you could just go to system->preferences->sessions
ON startup programs click add and select your startup script.

You could it all CLI, but I found this a nice way of kicking things off from boot

does this still work if I login using kde?

---

another problem is that imwheel is started automatic (with wrong options I guess), but I don't know from where, I have looked in:
/home/user/.kde/Autostart/
/etc/X11/Xsession.d/
/etc/rc.local
system->preferences->sessions

it appears it's login as root which I don't want
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=48797&stc=1&d=1194008074[/IMG]


- I have a folder named imwheel in the /etc/X11 folder. Removing this folder cause problem -> can't login. The folder contains 2 files, removing the 2 files doesn't cause a problem.

One of the file is _/etc/X11/imwheel/startup.conf_ having a line
> # Set this to "1" to make imwheel start along with your X session.
IMWHEEL_START=0

leaving this as default still let imwheel startup as a proces created by root

---

