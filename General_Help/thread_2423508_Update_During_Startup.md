---
title: "Update During Startup"
date: 2019-07-24
forum: General Help
---

### Post by fernnadolk on 2019-07-24
Hello Everyone
I wonder if it is possible for me to run a script that updates my programs DURING ubuntu startup.
Explaining better what I want:
Every Saturday the computers will turn on automatically at night (using WOL) and make the necessary updates (except the Linux version update) automatically, after a while the computer should shut down. This is all without interference from anyone.

---

### Post by TheFu on 2019-07-26
You can schedule anything that can be scripted to run at any time provided it doesn't use a GUI and the computer is on.
Whether you can cause any computer to wake up, run a job or not is highly dependent on the ability of that specific computer to be awoke.  It would be much easier to have a script that
a) runs a backup
b) runs an update/upgrade
c) shuts down the system
Then you could run that at 7pm Fridays ... or 1am Saturday and awake to a shutdown computer that has been patched.  Plus, getting that script working is required as part of your longer plan to have the system wake up and do the same thing, so it isn't any waste of effort at all.

If you don't have excellent, automatic, versioned, backups, running 100% automatic patches is a bad idea, since every once in a while the patches can do bad things.  I've been burned a few times over the years.  Thankfully, I had backups that could restore the system to a state pre-patch.

When you do patch, make certain you keep a log of the patch setting, so when something fails, and it will, that you can see what the failure was.

Ok ... so here's my nightly backup script and "standby" for a laptop.
```
$ more bin/back-suspend.sh 
#!/bin/bash

/root/bin/backup-to-rom.sh 
/usr/sbin/pm-suspend 
```
It is called from root's crontab at 00:03 am:
```
03 0 * * * /root/bin/back-suspend.sh
```

I don't want to shutdown my system, just suspend it.  I reboot that laptop weekly.

The pm-suspend call could easily be a **/sbin/shutdown now** call instead. See how I'm using the full path to the programs. That is a best practice for all scripting to prevent unwanted programs (or hacked scripts) from being used accidentally.

The backup-to-rom.sh script is specific to my laptop and my network. It uses rdiff-backup to make versioned backups.  

To do the patching stuff, something like```

/usr/bin/apt-get update 2>&1 | tee /root/logs/log.patching
/usr/bin/apt-get upgrade 2>&1 | tee -a /root/logs/log.patching
```
would be what I used in a different root-run script. You could call that in a back-suspend-patch.sh script, though I wouldn't.

But you do your machine how you like it.

---

