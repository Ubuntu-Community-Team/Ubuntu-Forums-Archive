---
title: "start script before login ubuntu 18.04"
date: 2018-09-01
forum: General Help
---

### Post by brofjst on 2018-09-01
Hi guys.
I know this question has been made many times, but i've tried a lot of possible fixes found on the internet and none of them works, so i'd like to ask you an help.
I'd like to run the command "xset led 3" before the login of the user which turns on the leds of my keyboards.
I've tried these things:
 - Insert this command in a file called K99 in /etc/rc0.d/
 - insert the script in /etc/init.d/
 - insert the script in /etc/gdm3/Init/Default
 - Created a systemd script
 - tried with crontab
I could have tried something else but i do not remember.

---

### Post by deadflowr on 2018-09-01
I'm not sure if xset can run prior to login.
But you can set it to run when a user logs in like these methods:
[https://askubuntu.com/questions/863031/what-is-the-best-place-for-xset-commands-to-survive-reboot]("https://askubuntu.com/questions/863031/what-is-the-best-place-for-xset-commands-to-survive-reboot")

---

### Post by brofjst on 2018-09-01
I'd like to run it BEFORE the login, i'd already know how to do it after a login.
I'm almost sure it is possible, in other distros i've done it putting the script here:
[B]    Fedora: /etc/sddm/Xsetup
    Arch: /usr/share/sddm/scripts/Xsetup 
[/B]It was on KDE but it should be possible on gnome too.

---

