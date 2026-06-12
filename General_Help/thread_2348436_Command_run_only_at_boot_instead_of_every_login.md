---
title: "Command run only at boot instead of every login"
date: 2017-01-03
forum: General Help
---

### Post by SchnappiJedi on 2017-01-03
Added a command in /home/user/.profile...

It (obviously) runs ever time login. Is there a way to make a command run *only* once at boot and not every login afterwards? On Entware-ng a mount.autorun file in the root works.

---

### Post by Keith_Helms on 2017-01-03
There are multiple ways.  You can add a script to the startup commands on your system.  You can add a command or script to your crontab and use the special runtime setting of @reboot.  You can add a line to rc.local to execute a command or script.  Does it matter what user the command runs as?

---

### Post by SchnappiJedi on 2017-01-03
Yes. Is a shared drive mount. If added to root crontab will the command/script still prompt for a password?

---

### Post by Keith_Helms on 2017-01-03
No.  The root crontab will not prompt for a password.  If you're going to use that approach, keep in mind that root has a more limited path setting than your personal ID.  You might have to explicitly provide the full path to whatever you're running.  For example, you might be able to run a script out of your bin directory just by typing the name, such as foobar.sh.   In the root crontab, you would need to enter /home/yourid/bin/foobar.sh.

---

### Post by SeijiSensei on 2017-01-03
Scripts run  from /etc/rc.local are run with root privileges at the end of the boot sequence.  That's the standard method for running an arbitrary script at boot.

---

### Post by SchnappiJedi on 2017-01-04
In /home/user/.profile separated multiple commands with new lines. In /etc/rc.local do commands need to be prefaced with:

```
#!/bin/bash
```

And use 

```
command1 && command2 && command3
```

Or should just use new lines for multiple command likes in /home/user/.profile?

---

### Post by Keith_Helms on 2017-01-04
rc.local already has **#!/bin/sh -e **at the top of it.  That appears as the first line of a script to tell the OS what to execute and pass the script to.  You can add additional commands to the rc.local script without repeating that line.

EDIT: Okay, I went off on the wrong track with &&.  After thinking about it some more, the reason to use && is if you don't want command 2 to run if command 1 fails.  You can do the same thing with an if statement, but this is shorter.

---

### Post by SeijiSensei on 2017-01-05
Although if you invoke scripts from rc.local they will still need "#!/bin/bash" at the top of the file containing the script.

---

