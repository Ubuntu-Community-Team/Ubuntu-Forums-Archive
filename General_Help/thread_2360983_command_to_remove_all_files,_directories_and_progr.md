---
title: "command to remove all files, directories and programs"
date: 2017-05-10
forum: General Help
---

### Post by sludvg on 2017-05-10
above all i wanted apologized cause for my bad english...

so, i recently installed the asterisk in ubuntu server, but this not worked and i like know if exist anyone command for delete/remove all files and directories with asterisk in the name.

and, please, correct my writing so I do not make the same english mistakes.

---

### Post by TheFu on 2017-05-10
Welcome to the forums.

Make a backup, so you can start over if anything bad happens.

It depends on how you installed asterisk. If you used the normal package manager, then
```
sudo apt-get purge asterisk*
```
should get most of the stuff - programs, /etc/asterisk, stuff like that.

However, if you installed any other dependencies, those will need to be removed using the reverse method for the installation method you employed.

It will not remove everything, since you haven't been clear on what was created or how it was placed onto the system.  Only you know that.  But if you didn't do much and stayed in the package manager, then that command will get almost everything.

In the future, know that asterisk really needs to be on dedicated hardware and that most places do a "fork-lift" upgrade between version to avoid unplanned downtime.  Also, most people don't add it to an existing linux server, they install a purpose-built distro, just for asterisk.  It has been a few years since I touched asterisk, but back then freePBX was the normal method.  Things have probably changed.  
I suspect there is a good beginner solution that runs on a Raspberry Pi.

---

### Post by ian-weisser on 2017-05-10
> **sludvg said:**
> i recently installed the asterisk in ubuntu server, but this not worked

It failed to install? 
It installed, but it did not work?
It installed, but did not work the way you expected?

---

### Post by sludvg on 2017-05-12
didn't work, when i register a sip account the softphone return "error 403 - forbidden"... i will restore machine and to try install again

---

### Post by TheFu on 2017-05-12
You purge the software and expect it to work?
I'm confused.

If the client hasn't been setup inside asterisk, then it should reject the SIP registration.  All client devices need to be pre-configured.

But you are better off using a pre-built distro than a generic Ubuntu box, especially if you are knew to SIP.

---

