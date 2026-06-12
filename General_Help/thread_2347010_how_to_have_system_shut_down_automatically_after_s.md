---
title: "how to have system shut down automatically after specified period of time"
date: 2016-12-20
forum: General Help
---

### Post by juntjoo2 on 2016-12-20
So far I've only found apps that didn't work or ones that require you to reset the command to shut down each time you want it to, which defeats the purpose of what I'm trying to do.  Any suggestions?

---

### Post by #&amp;thj^% on 2016-12-20
Depends on the Version your using weather "sudo" is needed.
16.04.1 I use
```
sudo shutdown -h 120
```
Where the "120" is equaled to Minutes
And from the man Pages
```
 NAME
       shutdown - Halt, power-off or reboot the machine

SYNOPSIS
       shutdown [OPTIONS...] [TIME] [WALL...]

DESCRIPTION
       shutdown may be used to halt, power-off or reboot the machine.

       The first argument may be a time string (which is usually "now").
       Optionally, this may be followed by a wall message to be sent to all
       logged-in users before going down.

      [COLOR=#b22222] The time string may either be in the format "hh:mm" for hour/minutes
       specifying the time to execute the shutdown at, specified in 24h clock
       format. Alternatively it may be in the syntax "+m" referring to the
       specified number of minutes m from now.  "now" is an alias for "+0",
       i.e. for triggering an immediate shutdown. If no time argument is
       specified, "+1" is implied.[/COLOR]

     [COLOR=#00ff00]  Note that to specify a wall message you must specify a time argument,


       If the time argument is used, 5 minutes before the system goes down the
       /run/nologin file is created to ensure that further logins shall not be
       allowed.
[/COLOR]
OPTIONS
       The following options are understood:

       --help
           Print a short help text and exit.

       -H, --halt
           Halt the machine.

       -P, --poweroff
           Power-off the machine (the default).

       -r, --reboot
           Reboot the machine.

       -h
           Equivalent to --poweroff, unless --halt is specified.
       -k
           Do not halt, power-off, reboot, just write wall message.

       --no-wall
           Do not send wall message before halt, power-off, reboot.

       -c
           Cancel a pending shutdown. This may be used cancel the effect of an
           invocation of shutdown with a time argument that is not "+0" or
           "now".

EXIT STATUS
       On success, 0 is returned, a non-zero failure code otherwise.

SEE ALSO
       systemd(1), systemctl(1), halt(8), wall(1)
```

```
sudo shutdown -P 1:00

```
to shutdown at 1am and

When I press** ctrl + c after executing "shutdown"**, it also aborts the scheduled shutdown

---

### Post by juntjoo2 on 2016-12-20
thanks.  so if I put in [COLOR=#000000][FONT=&amp]sudo shutdown -h[/FONT][/COLOR] x it will reset itself each time I bring the system back from falling asleep?


[COLOR=#000000][FONT=&amp]...


hmm... [/FONT][/COLOR]sudo shutdown -h 15 didn't even work. Any ideas?

---

### Post by #&amp;thj^% on 2016-12-21
> **juntjoo2 said:**
> thanks.  so if I put in [COLOR=#000000][FONT=&amp]sudo shutdown -h[/FONT][/COLOR] x it will reset itself each time I bring the system back from falling asleep?



Yes it will still be running in the background. You can check by way of the terminal Via:"shutdown" it will show you Something Like this
```
Shutdown scheduled for Wed 2016-12-21 11:23:52 MST, use 'shutdown -c' to cancel
```
But if you reboot your system you will have to enter your command again.
> [COLOR=#000000][FONT=&amp]hmm... [/FONT][/COLOR]sudo shutdown -h 15 didn't even work. Any ideas?
Are you hibernating?   And I suppose suspend could also have a negative effect on the code... I don't use suspend.
If you want this to be something that runs Daily on each an every boot..we can add that to cron.
So just let me know...I'll give you a script.;)
But you have to make a choice here:
Sorry to report this Cron is not active when the system is suspended, period.  **Thus, in suspend mode, nothing is active, but the power is still on for RAM**.
So I guess you will have a choice to make here.

---

