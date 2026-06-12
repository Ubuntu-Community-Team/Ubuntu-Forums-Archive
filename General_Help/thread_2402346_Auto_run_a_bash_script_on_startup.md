---
title: "Auto run a bash script on startup"
date: 2018-09-28
forum: General Help
---

### Post by ubuntini2 on 2018-09-28
Ok so I've done some googling and tried one suggestion which hasn't worked

I've done a chmod 777 to the script.sh file

And then created a crontab with a @reboot command 
```
@reboot /home/foo/02_Scripts/script.sh
```

as mentioned in this tutorial
[https://www.youtube.com/watch?v=2ZQViUv0-zs](https://www.youtube.com/watch?v=2ZQViUv0-zs)

Anyone have a solution that does work?

---

### Post by yetimon_64 on 2018-09-28
What _*Ubuntu version*_ are you using and, in particular, _*what desktop environment*_ is in use as well ?

Normally to run a user script (bash) I store it in a "bin" folder in my home folder ($HOME/bin). After a log out and back in again any executable script in the bin folder is in the users path.

Adding the full script path/filename to a DE (desktop environment) startup entry should be enough to run the script at every startup.

IF, the script needs any root privileges it would pay to add it to the file /etc/rc.local to have it run at startup instead of using the DE start up entry method.

I have never tried to use a crontab entry to run a script at startup as an autostart entry or rc.local entry has always worked out easiest here.  Regards, yeti.

**Edit:** just noted the thread tag is ubuntu_mate, I'm not entirely sure how a start up entry is done in mate; but, iirc, the old gnome interface mate is based on had a gui application for setting start up entries under the "Settings" menu.

---

### Post by Dennis N on 2018-09-28
My procedure for MATE:

1) Put script to run on login into ~/bin, a common place for user scripts. Make it executable.
2) Put the command to run it in startup applications. (Control Center > Startup Applications > 'Add' Button). Use full path to be sure.
3) Next time you log in, it should work.

---

