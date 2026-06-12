---
title: "Netatalk Broken since Feisty Upgrade"
date: 2007-04-21
forum: General Help
---

### Post by fuzzypig on 2007-04-21
Yesterday I upgraded to Ubuntu Feisty. Netatalk had an upgrade error during the distro upgrade, but everything seemed to work fine. I did want to remove netatalk, though. I tried to do so, but netatalk cannot be removed. I get an error:

```
(Reading database ... 266323 files and directories currently installed.)
Removing netatalk ...
hostname: Unknown host
invoke-rc.d: initscript netatalk, action "stop" failed.
dpkg: error processing netatalk (--remove):
 subprocess pre-removal script returned error exit status 1
hostname: Unknown host
invoke-rc.d: initscript netatalk, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 netatalk

```

How might I fix the problem, or even remove netatalk manually?

---

### Post by sbakker on 2007-06-06
Has anyone else seen or solved this problem?  I tried to install netatalk and received the same error on install, and I am getting the same error when I try to remove or reinstall it.  In the near future, I would like to use Fiesty as a file server for my Mac network, and I've been told that netatalk is the way to go.

Any help would be appreciated.

Cheers,
Shaun

---

### Post by jonlink on 2007-06-27
I installed it via synaptic just fine, I then reinstalled it with SSL by following [instructions in a post on this forum]("http://ubuntuforums.org/showthread.php?t=410274") and that also worked out just fine.  Though I haven't tried connecting to anything yet netatalk started just fine.


**EDIT:** Well it works and it doesn't work.  Things are running, but I just got a message that netatalk's version of AFP is outdated and incompatible. Awesome! It looks like the post to add SSL is the culprit though.

**EDIT 2:** Installs & starts just fine, but now I can't see the computer listed on the network. ...wonder if it needs the SSL?.... at anyrate I can connect via IP

---

### Post by jamescoy on 2007-07-01
I have a somewhat similar situation whereby it seems that netatalk is starting up, but it doesn't see my AppleTalk-only printer.

---

### Post by Moelito on 2007-07-19
Found the problem! In the netatalk startup script, netatalk tries to get the host name by using "/bin/hostname -short" but the flag short doesn't seem to work anymore. Just remove the "-short" flag and netatalk will start.
According to the startup script you should only change /etc/default/netatalk but I had to change in /etc/init.d/netatalk too.

//Moelito

---

