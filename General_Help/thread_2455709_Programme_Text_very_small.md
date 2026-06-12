---
title: "Programme Text very small"
date: 2020-12-26
forum: General Help
---

### Post by cressrt2 on 2020-12-26
I have a new 20.04.1 install on a Lenovo Ideapad 3, but some programmes are loading the text very small.
I asked for help on one programme that was the smallest and was told to run the code QT_SCALE_FACTOR=2 ~/.local/share/xxx/xxx in a terminal and this worked well,  I was also  told that writing "export QT_SCALE_FACTOR=2" in an init script would enable this on start up, but I am struggling with this as I have not written one before.

I looked on line for help and based on what I could find, tried putting a the file in etc/init.d and created a symbolic link to it in etc/rcd.2, the code I used was this, but it does not work.

#! /bin/sh
export QT_SCALE_FACTOR=2 ;
esac ;;
exit 0



Can anyone suggest the appropriate code that makes up a script please and advise where it should be placed?

---

### Post by dinkidonk on 2020-12-26
You could add the line "export QT_SCALE_FACTOR=2" to your login script (~/.profile).

Files in "/etc/init.d/" are old style init scripts, they require a [specific structure]("https://unix.stackexchange.com/questions/20357/how-can-i-make-a-script-in-etc-init-d-start-at-boot") in order to work and your script does not have this structure. On modern systems you would create a [systemd service](https://man7.org/linux/man-pages/man5/systemd.service.5.html) in order to invoke the script on startup or when a specific event occurs, but I'm not sure if that is worth the trouble.

---

### Post by cressrt2 on 2020-12-26
Thanks, that seems to have worked OK

---

### Post by Holger_Gehrke on 2020-12-26
For simply setting a variable in the environment it's not necessary to write either an init script or a systemd service. There's a part of systemd (systemd-environment-d-generator) that loads and parses environment settings from files with names ending in '.conf' that can be in multiple locations. Simply creating ~/.config/environment.d/ and putting a file with a name ending in '.conf' with the variable and its value inside should be all that's needed (you'll probably need to log out and back in for new settings to get loaded). More details can be found in the manual page for environment.d ('man 5 environment.d').

Holger

---

