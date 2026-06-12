---
title: "Standby/Suspend mode not working"
date: 2013-09-10
forum: General Help
---

### Post by Geziefer on 2013-09-10
I just installed the current Lubuntu on my netbook (Intellibook).
Suprisingly, the hibernate mode was working out of the box (I had troubles with it on another laptop), but the sleep mode (suspend/standby) does not work. It looks like it suspends correctly, but after trying to wake it up, nothing happens on the screen and I have to do a hard power off.
The links I googled seem to address either the problem of not going into any suspend mode or describe older versions.
Can someone point me to the right setting or at least possible source of the problem?

---

### Post by Toz on 2013-09-10
Hello and welcome to the forums.

A little more information would be helpful in diagnosing the issue:

1. The full make and model of your computer.

2. The video card in your computer and the driver it is using. The following terminal command will identify that for you:
```
lspci -k | grep -A3 VGA
```

3. Confirmation whether the system is returning from suspend or not. This information will be available in the /var/log/pm-suspend.log file. Use this command to upload a copy of the log file to paste.ubuntu.com so that it can be reviewed by others:
```
pastebinit /var/log/pm-suspend.log
```
...and post back the link that is generated.

4. Any syslog error messages during the suspend/resume cycle. The following command will identify those (preferably run right after a suspend attempt when the machine is restarted):
```
cat /var/log/syslog | grep PM:
```

More information is available in the "Kernel Suspend" debugging page linked to in my signature.

---

