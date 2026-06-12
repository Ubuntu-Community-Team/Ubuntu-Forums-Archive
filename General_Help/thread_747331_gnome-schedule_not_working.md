---
title: "gnome-schedule not working"
date: 2008-04-06
forum: General Help
---

### Post by ajgreeny on 2008-04-06
I am having problems with gnome-schedule, which will not seem to make any new tasks whatever I do.

I have followed all the help files available but when I click "OK", after setting the time and either the path to a shell script file in my home folder or the full command, not the shell script, nothing happens and no changes are made to crontab.  Do I need to run it as superuser to get it to do anything, it does need to write to crontab, after all, though there is no reference to needing to use it as root in the help files.  I have installed kcron to try and overcome this, which I think works, and I can just use a manual edit of the crontab file, I know about that, but why am I having these problems with gnome-schedule?

I'm running 7.10 on a sempron 2400+ with 1GB ram, and ati (ouch!) graphics card, though it is one of those that seems to work well with the OS driver (9200SE).  It is very near perfect as a system, but this little problem just annoys me greatly, and I want to find out if I'm doing anything wrong.

---

### Post by Diabolis on 2008-04-29
I have the same issue with hardy heron. Tasks will not launch, but if I press the execute button to see if the command is correctly typed, it works :confused:


**edit**
Not even kcron works for me.
Ubuntu 8.04
gnome-schedule 2.0.2
kcron 3.5.9

---

### Post by simonlesorcier on 2008-04-30
Same here, my script is not running when scheduling in cron if I execute it from the CLI with "  ./script  " it does work.
any insight?
thanks

Eduardo

---

### Post by Diabolis on 2008-05-18
gnome-schedule is working again. It got fixed while I was trouble shooting [some other problems]("http://ubuntuforums.org/showthread.php?t=775862").

Apparently it was a problem of permissions with some files inside my home folder, unfortunately I do not know which are those files.

This is what I did, I went to **/home**, right click over my user folder, changed the permissions for other users to none and then applied the changes to all the files inside too.

---

