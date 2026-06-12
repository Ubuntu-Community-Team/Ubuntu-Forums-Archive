---
title: "/sbin/shutdown command not working the same after upgrade to Ubuntu 15.10"
date: 2015-12-15
forum: General Help
---

### Post by subject117 on 2015-12-15
I have this in the root user's crontab:

```
10 6 * * 1-6     /sbin/shutdown -P 10:00
10 6 * * 0       /sbin/shutdown -P 7:00
```

Before I upgraded to 15.10, this would schedule a shutdown at a specific time. Before the shutdown, I would get warning messages telling me the machine is about to be shut down.

After the upgrade to 15.10, this does nothing. The machine won't shut down.

I do not see the shutdown process running (should I? I seem to remember I used to see it):

```
jim@main:~$ ps -aef | grep shutdown                                                                                                   
jim      18318  6639  0 09:55 pts/1    00:00:00 grep --color=auto shutdown
```

The root user did get an email indicating the shutdown was scheduled:

```
Date: Tue, 15 Dec 2015 06:10:01 -0500 (EST)
From: Cron Daemon <root@main>
To: root@main
Subject: Cron <root@main> /sbin/shutdown -P 10:00

Shutdown scheduled for Tue 2015-12-15 10:00:00 EST, use 'shutdown -c' to cancel.
```

There is no later email letting me know that the shutdown was cancelled, which is what happened before when I did 'sudo shutdown -c'.

Why does the shutdown command now fail silently? I know I can put something like this in my crontab:

```
5 10 * * 1-6     /sbin/shutdown -h "now"
```

But then the machine shuts down without warning.

What can I do to get this working again?

Thanks!

---

### Post by deepakdeshp on 2015-12-15
```
man shutdown
``` should give if any flags have changed in the command. And ```
which shutdown
``` will give the path of the command

---

### Post by subject117 on 2015-12-15
Thanks, but this isn't helpful.

I know it is /sbin/shutdown because that is what is in the crontab. And I originally looked at the man pages to get the right command line arguments to do what I wanted to do; there is nothing in there that is new or any indication that something changed.

---

### Post by deepakdeshp on 2015-12-17
shutdown -v is a verbose flag. You could try it along with TIME

```
shutdown --help
Usage: shutdown [OPTION]... TIME [MESSAGE]
Bring the system down.


Options:
  -r                          reboot after shutdown
  -h                          halt or power off after shutdown
  -H                          halt after shutdown (implies -h)
  -P                          power off after shutdown (implies -h)
  -c                          cancel a running shutdown
  -k                          only send warnings, don't shutdown
  -q, --quiet                 reduce output to errors only
  -v, --verbose               increase output to include informational messages
      --help                  display this help and exit
      --version               output version information and exit


TIME may have different formats, the most common is simply the word 'now' which
will bring the system down immediately.  Other valid formats are +m, where m is
the number of minutes to wait until shutting down and hh:mm which specifies the
time on the 24hr clock.



```

[http://www.cyberciti.biz/tips/linux-shutdown-command-and-logfile.html](http://www.cyberciti.biz/tips/linux-shutdown-command-and-logfile.html)

---

### Post by subject117 on 2015-12-17
Interesting. When I type "shutdown --help" I see different options.

```

jim@main:~$ shutdown --help
shutdown [OPTIONS...] [TIME] [WALL...]

Shut down the system.

     --help      Show this help
  -H --halt      Halt the machine
  -P --poweroff  Power-off the machine
  -r --reboot    Reboot the machine
  -h             Equivalent to --poweroff, overridden by --halt
  -k             Don't halt/power-off/reboot, just send warnings
     --no-wall   Don't send wall message before halt/power-off/reboot
  -c             Cancel a pending shutdown
```

Are you using the same version of Ubuntu as me?

```
jim@main:~$ which shutdown                                                                                 
/sbin/shutdown                                                                                             
jim@main:~$ lsb_release -a                                                                                 
No LSB modules are available.                                                                              
Distributor ID: Ubuntu                                                                                     
Description:    Ubuntu 15.10                                                                               
Release:        15.10                                                                                      
Codename:       wily
```

---

### Post by deepakdeshp on 2015-12-18
No I am not using your version of Ubuntu. You can use your versions flags


The message will be flashed to all users who have logged in

To send only warnings and no power down  /sbin/shutdown -k +1 "shutting down in 1 minute"

To power down /sbin/shutdown -h +1 "shutting down in 1 minute"

---

### Post by Rooster2000 on 2016-02-16
I am having a similar problem after I changed my Lubuntu 14.04.3 LTS to 15.10. For me, shutdown command is working properly itself, but it doesn't show those countdown warning messages ("This system is shutting down in 30, 15, 10, 9, 8, ... minutes.") in LXTerminal anymore. Is there a way to toggle these warning messages on?

---

### Post by ian-weisser on 2016-02-16
/sbin/shutdown changed when Ubuntu migrated from Upstart to systemd in 15.04.

This seems like a known bug introduced by the change: [LP #1448070]("https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1448070")
If so, please click the "does this bug affect you?" link on the bug report and subscribe.
Do NOT leave 'me too' messages or otherwise pollute the bug report. It's not a forum.

---

### Post by Rooster2000 on 2016-02-18
Sounds like it could be another appearance of the bug you referred. Hopefully it will be fixed in 16.04 LTS. 

Meanwhile, is there any workaround for this?

---

### Post by ian-weisser on 2016-02-19
It is not fixed in 16.04
The only workaround I know is to script 'wall' and shutdown, and trigger the script.

---

### Post by Rooster2000 on 2016-02-22
> **ian-weisser said:**
> The only workaround I know is to script 'wall' and shutdown, and trigger the script.

I started to make such a script, but I don't seem to get wall command to work at all. I made this script that is executed as a root on every minute in cron:

```
#!/bin/bash

wall "This computer will shut down in 30 minutes."
echo "This computer will shut down in 30 minutes." | wall
wall < /home/*user*/test.txt

exit 0
```

None of these produce any messages in my LXTerminal while I am logged in. Also, these commands do not produce any wall messages back to my terminal while they are ran by sudo (from the terminal). 
I also checked that:

```
:~$ mesg
is y

```

Any idea what could be wrong? Is there an alternative for wall command?

---

### Post by Rooster2000 on 2016-02-25
Does anybody have the same problem with wall command in 15.10, or is it just me?

---

### Post by ian-weisser on 2016-02-25
Wall in Ubuntu 15.10 works as expected for me.
Perhaps you should reinstall the 'bsdutils' package.

---

### Post by Rooster2000 on 2016-02-26
I reinstalled the *bsdutils* package and rebooted, but still no luck.

```
sudo apt-get install --reinstall bsdutils
```

I also considered reinstalling the config files too

```
sudo apt-get purge bsdutils
sudo apt-get install bsdutils
```

But with purge there was a prompt that said I was doing something potentially harmful, so I aborted it. Is there any significant difference in reinstalling *bsdutils* with *install --reinstall* or *purge* & *install*?

Perhaps I should consider reinstalling my whole system, if wall command should indeed work on it.

---

### Post by ian-weisser on 2016-02-26
> **Rooster2000 said:**
> Is there any significant difference in reinstalling *bsdutils* with *install --reinstall* or *purge* & *install*?
The final state of both is identical, unless you edited settings files in /etc. Those would be lost by a purge, of course (that's the *purpose* of purge)

---

### Post by Rooster2000 on 2016-02-29
> **ian-weisser said:**
> Wall in Ubuntu 15.10 works as expected for me.

I have tried now few Lubuntu and one Ubuntu Live installers with following results:

[TABLE="class: grid, width: 500"]
[TR]
[TD]**File**[/TD]
[TD]**Wall command working**[/TD]
[/TR]
[TR]
[TD]lubuntu-14.04.3-desktop-i386.iso[/TD]
[TD]Yes[/TD]
[/TR]
[TR]
[TD]lubuntu-15.10-desktop-i386.iso[/TD]
[TD]No[/TD]
[/TR]
[TR]
[TD]lubuntu-15.10-desktop-amd64.iso[/TD]
[TD]No[/TD]
[/TR]
[TR]
[TD]ubuntu-15.10-desktop-i386.iso[/TD]
[TD]Yes[/TD]
[/TR]
[/TABLE]


The md5sum of each file was checked before extracting them with UNetbootin to USB stick, and file integrity was tested before starting Live.
The command I used to test if wall works properly:

```
sudo echo "Testing" | wall
```

And this was expected to produce a system message to terminal. For both Lubuntu 15.10 versions, this didn't cause any feedback, which is the case in my current 15.10 (Lubuntu) system too. Also, no error message is displayed when typed:

```
 sudo wall "Testing"
```

Why is wall command not working in Lubuntu 15.10? Is this a bug in installer files? Can anyone get wall command to work properly in Lubuntu 15.10?


[SIZE=2]**Edit 2016-03-11:** This post has been copied in a [new]("http://ubuntuforums.org/showthread.php?t=2316732&p=13453184#post13453184") thread.[/SIZE]

---

