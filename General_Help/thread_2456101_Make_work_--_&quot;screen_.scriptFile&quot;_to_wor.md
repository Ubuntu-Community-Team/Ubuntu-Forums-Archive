---
title: "Make work -- &quot;screen ./scriptFile&quot; to work at boot (whether rc.local, systemd, cron)"
date: 2021-01-04
forum: General Help
---

### Post by grndslm2 on 2021-01-04
I'm attempting to get a certain script file to run inside the screen command as soon as the system boots.

AFTER the system boots, I can type my command, and it'll work....
```
cd /home/grndslm/script/build/; /usr/bin/screen -dm -S scriptName ./scriptFile --options --moreOpts -etcOpts
```

But if I try running that same exact command inside /etc/rc.local, it gives me an error.  If I try in a systemd service, it doesn't work -- error.  If I add it to "crontab -e" with a little "@reboot" in front of the command, that ALSO does not work..

Can somebody PLEASE give me a solution that works?  I've been rebooting my computer for days, trying different things.... and NONE of them seem to work.  I have to manually run the screen command AFTER boot.  Same thing if I use tmux in place of screen.  Please -- HELP ME!!

Thank you!  8^D

---

### Post by grndslm2 on 2021-01-04
And yes.... I have #! /bin/bash at the top of the script file!

And yes.... the script file and rc.local are both chmod +x executable!!

---

### Post by CatKiller on 2021-01-04
> **grndslm2 said:**
> If I try in a systemd service, it doesn't work -- error.
What's the error?

---

### Post by grndslm2 on 2021-01-04
> **CatKiller said:**
> What's the error?
"bad unit file setting" -->

> systemctl status screen.serviceWarning: The unit file, source configuration file or drop-ins of screen.service changed on disk. Run 'systemctl daemon-reload' to reload units.
&#9679; screen.service - Script inside Screen
     Loaded: bad-setting (Reason: Unit screen.service has a bad unit file setting.)
     Active: inactive (dead)


Jan 04 08:41:47 bananastand systemd[1]: /etc/systemd/system/screen.service:13: Executable "cd" not found in path "/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin"
Jan 04 08:41:47 bananastand systemd[1]: screen.service: Unit configuration has fatal error, unit will not be started.

cd is a BUILT-IN command.  How can it not be found??

---

### Post by CatKiller on 2021-01-04
> **grndslm2 said:**
> cd is a BUILT-IN command.  How can it not be found??
It's built into **the shell**. You aren't using a shell when you're launching processes with systemd. 

You want the path to screen, and the path to your script. Changing directory doesn't make a lot of sense.

---

### Post by grndslm2 on 2021-01-04
OK... so I moved the "cd /home/grndslm/script/build/;" portion of the command to the systemd file under "WorkingDirectory=/home/grndslm/script/build" at this point.

Made it a little further, but still getting errors....

"systemctl status screen" --->
> &#9679; screen.service - Script inside Screen     Loaded: loaded (/etc/systemd/system/screen.service; enabled; vendor preset: enabled)
     Active: failed (Result: start-limit-hit) since Mon 2021-01-04 09:25:31 CST; 4min 12s ago
    Process: 1476 ExecStart=/usr/bin/screen -d -m -S scriptName ./script --options --moreOpts --etcOpts
   Main PID: 1476 (code=exited, status=0/SUCCESS)


Jan 04 09:25:31 bananastand systemd[1]: screen.service: Scheduled restart job, restart counter is at 5.
Jan 04 09:25:31 bananastand systemd[1]: Stopped Script inside Screen.
Jan 04 09:25:31 bananastand systemd[1]: screen.service: Start request repeated too quickly.
Jan 04 09:25:31 bananastand systemd[1]: screen.service: Failed with result 'start-limit-hit'.
Jan 04 09:25:31 bananastand systemd[1]: Failed to start Script inside Screen.
Jan 04 09:25:40 bananastand systemd[1]: screen.service: Start request repeated too quickly.
Jan 04 09:25:40 bananastand systemd[1]: screen.service: Failed with result 'start-limit-hit'.
Jan 04 09:25:40 bananastand systemd[1]: Failed to start Script inside Screen.


"journalctl -xe" -------->
> Jan 04 09:37:23 bananastand systemd[1]: Stopped Script inside Screen.-- Subject: A stop job for unit screen.service has finished
-- Defined-By: systemd
-- Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
-- 
-- A stop job for unit screen.service has finished.
-- 
-- The job identifier is 3650 and the job result is done.
Jan 04 09:37:23 bananastand systemd[1]: Started Script inside Screen.
-- Subject: A start job for unit screen.service has finished successfully
-- Defined-By: systemd
-- Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
-- 
-- A start job for unit screen.service has finished successfully.
-- 
-- The job identifier is 3650.
Jan 04 09:37:23 bananastand systemd[1]: screen.service: Succeeded.
-- Subject: Unit succeeded
-- Defined-By: systemd
-- Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
-- 
-- The unit screen.service has successfully entered the 'dead' state.
Jan 04 09:37:24 bananastand systemd[1]: screen.service: Scheduled restart job, restart counter is at 5.
-- Subject: Automatic restarting of a unit has been scheduled
-- Defined-By: systemd
-- Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
-- 
-- Automatic restarting of the unit screen.service has been scheduled, as the result for
-- the configured Restart= setting for the unit.
Jan 04 09:37:24 bananastand systemd[1]: Stopped Script inside Screen.
-- Subject: A stop job for unit screen.service has finished
-- Defined-By: systemd
-- Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
-- 
-- A stop job for unit screen.service has finished.
-- 
-- The job identifier is 3719 and the job result is done.
Jan 04 09:37:24 bananastand systemd[1]: screen.service: Start request repeated too quickly.
Jan 04 09:37:24 bananastand systemd[1]: screen.service: Failed with result 'start-limit-hit'.
-- Subject: Unit failed
-- Defined-By: systemd
-- Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
-- 
-- The unit screen.service has entered the 'failed' state with result 'start-limit-hit'.
Jan 04 09:37:24 bananastand systemd[1]: Failed to start Script inside Screen.
-- Subject: A start job for unit screen.service has failed
-- Defined-By: systemd
-- Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
-- 
-- A start job for unit screen.service has finished with a failure.
-- 
-- The job identifier is 3719 and the job result is failed.

---

### Post by ActionParsnip on 2021-01-04
Is this a desktop install with a GUI or is there no GUI here please?

---

### Post by CatKiller on 2021-01-04
Please use code tags rather than quote tags for your output. 

> **grndslm2 said:**
> 
```
Jan 04 09:25:31 bananastand systemd[1]: screen.service: Scheduled restart job, restart counter is at 5.
Jan 04 09:25:31 bananastand systemd[1]: Stopped Script inside Screen.
Jan 04 09:25:31 bananastand systemd[1]: screen.service: Start request repeated too quickly.
Jan 04 09:25:31 bananastand systemd[1]: screen.service: Failed with result 'start-limit-hit'.
```
You probably don't want to keep running the same script over and over, and launching more and more instances of screen. The systemd files let you choose whether it's something that just gets run once, or gets restarted if it exits.

Posting the actual file you've created would likely be more helpful to you than having people try to guess from your obfuscated error output.

---

### Post by grndslm2 on 2021-01-04
CatKiller... are you able to get ANY script file to run inside screen at boot?  This is a common problem it seems, after my hours of searching... for any script.

---

### Post by grndslm2 on 2021-01-04
> **ActionParsnip said:**
> Is this a desktop install with a GUI or is there no GUI here please?
There is no GUI.

---

### Post by grndslm2 on 2021-01-04
> **CatKiller said:**
> You probably don't want to keep running the same script over and over, and launching more and more instances of screen. The systemd files let you choose whether it's something that just gets run once, or gets restarted if it exits.
Right.. and I've chosen for systemd to restart the script if it fails.... which it's doing.  I figure that at SOME POINT, it'll start working, right??  if that same command works in a regular shell....

```
# in /etc/systemd/system/screen.service[Unit]
Description=Script inside Screen
After=network.target


[Service]
User=root
Group=root


StandardOutput=journal
StandardError=journal


WorkingDirectory=/home/grndslm/script/build
ExecStart=/usr/bin/screen -d -m -S scriptName ./scriptFile --options --moreOpts -- etcOpts


Restart=always


[Install]
WantedBy=multi-user.target
```

---

### Post by grndslm2 on 2021-01-05
Am I going crazy?  or is this a problem for everybody else??

It seems like screen should be able to handle this at boot.... but there's gotta be a bug somewhere.

I also had the same problem when trying to replace screen with tmux.  Soo... deeper than just either app??

---

### Post by grndslm2 on 2021-01-07
Do I need to offer a bounty for someone to make this work?  
:-D

---

### Post by wildmanne39 on 2021-01-07
No, please don't all support here is free and paying for support is not allowed, even in jest.

---

### Post by GhX6GZMB on 2021-01-08
If you want a script to invoke a shell command, you'll need it to start the shell first. For instance with:

sh -c <command>

This is transient, the shell will disappear again after executing the script line.

---

### Post by grndslm2 on 2021-01-12
I have spent entirely far too much time on this, but I finally got it to work.  Setting logfiles and checking those pinpointed to the biggest error, which was the -S switch in screen.....

For some reason, the -S switch is ignored and screen attempts to run "scriptName" as the actual script itself, instead of naming the screen "ScriptName".

I ended up just using systemd to run /usr/bin/screen by itself.... and then edited /etc/screenrc to include my command above with --options --moreOpts --etcOpts and the like.  Also interesting is that I could not run the script without the options, by pointing to default config file, or even selecting a different config file.  For whatever reason, the script wouldn't work with its own built-in config file options.  Lots of problems.... but the "screen -S" switch was the biggest one, for sure!!

EDIT:  Forgot to mention that I did end up adding "bash -c" somewhere in the screen command.  Not sure if it was necessary.... but it's working now, so I'm not testing it anymore!

---

