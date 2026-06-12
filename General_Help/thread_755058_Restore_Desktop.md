---
title: "Restore Desktop"
date: 2008-04-14
forum: General Help
---

### Post by akhost on 2008-04-14
My computer froze, and so, I started to kill processes to try to unfreeze it. Apparently I must have killed a system process because now my desktop is pretty much gone. I have the top tool bar but not the "applications" menu and cannot right click or get into any applications. I have turned the computer off and on again and tried logging in (which works fine) again with and without saving the session, and it still comes back the same way. Is there a way for me to restore this (and just as important, does anyone know what process *not* to touch so I don't make the same mistake twice?!)

Thanks so much in advance for any help!
Alex

---

### Post by lundholmj on 2008-04-14
not sure if it will help but check out this.

[http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/](http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/)

resets gnome to default ubuntu settings

---

### Post by akhost on 2008-04-14
Awesome, I'll try it now, thanks!

---

### Post by akhost on 2008-04-14
Hm, that did not work-- perhaps because I am using xubuntu and not ubuntu...? That site recommended resetting everything back to default with the following command: rm -rf .gnome .gnome2 .gconf .gconfd .metacity but this did nothing on xubuntu 7.

Thanks

---

### Post by lundholmj on 2008-04-14
oh right, that was to reset gnome.  here is a link to a thread in the forum that talks about resetting xubuntu

[http://ubuntuforums.org/showthread.php?t=593443](http://ubuntuforums.org/showthread.php?t=593443)

---

### Post by akhost on 2008-04-16
In case anyone else finds this thread and is looking to fix this problem, here's what to do to make it work on xubuntu:

- get to the login screen
- hit "CTRL + ALT + F1" and login to your account
- type "cd ~/.config" (without the quotes)
- type "rm -rf xfce4-session"
- type "rm -rf xfce4"
- type sudo reboot and enter your password

When you login the next time, it will have deleted your desktop environment and opened it back up with the default system desktop displays.

Thanks to lundholmj for helping with this-- its all working for me again!

---

### Post by bodhi.zazen on 2008-04-16
You probably do not need to reboot. Just log out, go to the log in screen (Ctrl-Alt-F7) and restart X with Ctrl-Alt-Backspace. Then log in and you should be good to go.

---

