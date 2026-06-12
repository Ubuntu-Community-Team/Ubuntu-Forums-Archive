---
title: "Must restart acpid for it to work"
date: 2007-07-27
forum: General Help
---

### Post by mbsullivan on 2007-07-27
Hi All,

I have a number of ACPI events set up for my hotkeys (using a Thinkpad X61).  They work fine, but upon restarting my computer, I need to call:

```
sudo /etc/init.d/acpi restart
```

In order to get them to work.  I have acpid running upon startup, but if I don't explicitly restart it, I get the following errors from acpid upon an event coming in (taken from /var/log/acpid):

> [Fri Jul 27 09:52:16 2007] received event "ibm/hotkey HKEY 00000080 00001002"
[Fri Jul 27 09:52:16 2007] executing action "/home/lfm/scripts/lock.sh"
[Fri Jul 27 09:52:16 2007] BEGIN HANDLER MESSAGES
[Fri Jul 27 09:52:16 2007] END HANDLER MESSAGES
[Fri Jul 27 09:52:16 2007] **action exited with status 1**
[Fri Jul 27 09:52:16 2007] completed event "ibm/hotkey HKEY 00000080 00001002"


I have tried running a script upon startup which stops and restarts the acpid daemon, this doesn't seem to help.  I have messed around with the run-levels of the script, to no avail.  The only thing that works is to restart acpid after logging in, and I don't want to have to manually do it every single time.

Any ideas?  Anybody know what an error status of 1 would indicate from acpid?

Thanks!
Mike

---

### Post by ihatecompaq on 2007-09-26
if you have figured this out let me know, I am having the same problem.

---

### Post by mbsullivan on 2007-10-21
Hi ihatecompaq,

Yeah, I figured out a work-around a while ago... I guess I never posted it b/c nobody's ever shown any interst.  It's a bit of a hack, but it works.  

(1) First, go to someplace where you can put commands to execute upon startup (such as ~/.xinitrc). 

(2) Add the following to be executed upon startup:

```
# fix ACPI visual hotkeys
xhost local:root	# allow root to run X applications
```

(3) Now restart ACPI... Because this requires root access, I added acpid to my /etc/sudoers file (to allow sudo privileges without password):

(3a) Edit your sudoers file:

```
sudo visudo
```

(3b) Add the following to the middle of the file (under the heading # Cmnd alias specification):

```
Cmnd_Alias     ACPID = /etc/init.d/acpid
```

(3c) Add the following to the bottom of the file (under the heading # Members of the admin group may gain root privileges):

```
[your username]	ALL = NOPASSWD : ACPID
```

(3d) Restart acpid (add to the file which will execute commands upon startup):

```
sudo /etc/init.d/acpid restart
```

Okay... Now your errors should go away!  Let me know if you have any questions... there are multiple ways to execute commands upon startup, so that part of my instructions are a bit vague.

Mike

---

