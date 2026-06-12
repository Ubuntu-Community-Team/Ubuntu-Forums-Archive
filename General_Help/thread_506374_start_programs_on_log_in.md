---
title: "start programs on log in"
date: 2007-07-21
forum: General Help
---

### Post by AJS302 on 2007-07-21
hi,
is there anyway to make a program start as soon as i log on? Similar to the windows start up folder

thanks

---

### Post by testube_babies on 2007-07-21
System -> Preferences -> Sessions  -> Startup Programs (Assuming you're on Gnome)

---

### Post by AJS302 on 2007-07-21
yes i am on gnome and thanks for the help

---

### Post by Morons on 2007-07-24
I am used to "redhat strains" such as Mandriva were I automatically started applications in /etc/rc.d/rc.local, I see that same file exist in /etc/rc.local in Ubuntu, however I always wanted to know if that is proper form?
Is there a Better place to start stuff per runlevel perhaps?
I require some background scripts to automatically run when the server get re-started. all of these are bash scripts.:confused:

---

### Post by bulldog060 on 2007-07-24
adding to /etc/rc.local will execute on any multi-user run level, the typical way ( that i have seen at least ) is to put your script in /etc/init.d/ and symlink it into the /etc/rc#.d/ directory where the # is the run level you want it to execute for 0->shut down, 1 -> single user, 2-5 -> multi-user, 6 -> restart.

~ron

---

### Post by Morons on 2007-07-25
By placing the script in /etc/init.d/, and execute **[FONT="Courier New"]/usr/sbin/update-rc.d {scriptname} defaults [/FONT]**will make the nessesary and correct symlinks.  I just have no start/stop/restart portions in my script, therefore my script is bit lacking to be integrated such way as an service module.  But as you commented i see my script is running 2x if it is placed in /etc/rc.local.
**P.S.** the correct way to to manage services is to use the **[FONT="Courier New"]/usr/sbin/invoke-rc.d {scriptname} [stop/start/restart][/FONT]**  On this point i might need some help, either to test for runlevel and exit my script or adding the stop,start,restart bits.:confused:

---

### Post by bulldog060 on 2007-08-01
The quick and dirty case for start|stop|restart and everything else displays the usage
```

[B]case $1 in
      start)
             #start stuff
       ;;
      stop)
              #stop stuff
       ;;
       restart)
               $0 stop
               $0 start
        ;;
        *)
             echo "Usage $0 {start|stop|restart}"
        ;;
esac[/B]

```

---

