---
title: "System Program Problem Detected"
date: 2017-02-15
forum: General Help
---

### Post by daniell59 on 2017-02-15
Never had this error message before. This happened after I installed Ubuntu 16.04.1 on a flash drive and ran it. To clarify, I am not referring to a problem while running it off the flash drive.
Any insight into this will be appreciated.

Ubuntu 14.04 32

---

### Post by Keith_Helms on 2017-02-15
You'll need to provide more info, such as when does this happen, where does the error appear and is there anything in the logfiles such as /var/log/syslog and when you run dmesg.

---

### Post by RobGoss on 2017-02-15
Not providing any information on what kind of errors you're seeing does not  help trouble shoot your issue

---

### Post by daniell59 on 2017-02-15
It occurs when I first boot up.
Perhaps this may make it clearer. I do not know how to remedy this however.

_usr_bin_rhythmbox.1000.crash     _usr_bin_totem.1000.crash
_usr_bin_rhythmbox.1000.upload    _usr_sbin_unity-greeter.112.crash
_usr_bin_rhythmbox.1000.uploaded
daniel@daniel-N68SA-M2S:/var/crash$

---

### Post by daniell59 on 2017-02-15
I may have solve the problem with the following

sudo rm /var/crash/*

I will wait a while before called it solved.

---

