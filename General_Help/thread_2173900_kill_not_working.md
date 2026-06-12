---
title: "kill not working"
date: 2013-09-11
forum: General Help
---

### Post by rebeltaz on 2013-09-11
Since upgrading to 12.04, evolution keeps freezing. I have tried the forcequit icon, which does nothing for it. I have tried switching to a new terminal window and running either 'killall evolution -v' or 'kill xxxxx'. Both commands report that the process has been terminated, but that is not the case. Evolution is still running and locked up. I haven't had any other programs lock up, but both kill commands work fine with other programs that are actively running and not locked up, evolution included. 

Why? Why does evolution keep locking up and why does kill not kill?

---

### Post by Impavidus on 2013-09-12
Kill by default sends the terminate signal, which is a request to terminate, allowing the applications to do some cleanup, make backups of files and things like that. If a program has a signal handler for SIGTERM and has completely locked up, it may not respond. In this case, try SIGKILL```
kill -9 <ID>
```

As to why evolution is freezing, I've got no idea.

---

### Post by nerdtron on 2013-09-12
```
pgrep evolution
```
Then use this number for the kill -9 command.

---

### Post by rebeltaz on 2013-09-12
Thanks guys. When it locks up again, I will try those. I wish I knew why it kept locking up though. It NEVER did that with 10.04!

---

### Post by ian-weisser on 2013-09-12
My evolution locks up, too. 

From my long experience with this problem, -9 works. -1 also works. I use:
```
pkill -1 evolution
```

---

### Post by rebeltaz on 2013-09-15
Thanks guys... That worked when firefox locked up today. I would really like to know why my system NEVER locked up running 10.04, but when I _upgraded_ to 12.04 it locks up as much as that OS that we are trying to avoid?

---

### Post by QIII on 2013-09-15
Hello!

Did you upgrade or do a fresh installation?

---

### Post by rebeltaz on 2013-09-15
> **QIII said:**
> Hello!

Did you upgrade or do a fresh installation?

I did an upgrade.... Please don't tell me I need to do a fresh install... I have way too many programs and settings to redo everything! :(

---

### Post by rebeltaz on 2013-09-25
Can I ask why I should have done a fresh install instead of an upgrade? If Ubuntu works correctly, shouldn't an upgrade work just fine?

---

### Post by nerdtron on 2013-09-25
I don't know why, but I'm not lucky on performing in-place distro upgrades. I usually update from one version to another by reinstalling the system. It's almost a ritual. :)
I think some applications and binaries and settings are very dependent on the current version which can cause some weird errors etc.

---

### Post by ian-weisser on 2013-09-25
> **rebeltaz said:**
> Can I ask why I should have done a fresh install instead of an upgrade? If Ubuntu works correctly, shouldn't an upgrade work just fine?

The recommendation for a fresh install often boils down to "I don't know why it's broken, but I know this will fix it." Time to diagnose minor issues can get expensive quickly.
For example, if you change a setting (and then forget you changed it), an upgrade won't reset the setting. But a reinstall will.

Upgrades are tested to be a safe path. I use upgrades in some situations. (One production machine upgraded since 2008 with no problems)
New-installs are also tested to be a safe path. I use reinstalls in some situations. (Lots of customizations to undo, or standard images for lots of machines)
I think it's a simple matter of your preference, and how much time you have available to troubleshoot the issue.

As to why a current application is crashing when a previous version didn't, that's a whole different thread for discussion. It could be a corrupt preferences or data file, it could be a bug in the application, it could be hardware failure, it could be a lot of things.

---

