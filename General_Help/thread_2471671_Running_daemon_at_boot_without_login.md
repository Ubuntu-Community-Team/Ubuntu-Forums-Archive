---
title: "Running daemon at boot without login"
date: 2022-02-06
forum: General Help
---

### Post by tdit2 on 2022-02-06
Hi all,

I have a daemon I run on an Ubuntu server in the format of "sudo deamonname path switches etc" which prompts for the admin password.

Ideally I need to be able to start the box and run that daemon, without actually logging into Ubuntu. In other words, power the system and walk away. Is this possible?
Thanks in advance!

---

### Post by TheFu on 2022-02-06
Of course it is possible.

Create a systemd "Unit" file for this service.  By default, those run as root and it won't be prompted for any credentials.
However, you'll need to fully specify the **deamonname** (which is just the name of the program), since the environment for a daemon is very different from that of an interactive user.

There must be 100+ "Unit" file examples on your system already.  In theory, those should be easier to understand. Just get the dependencies correct and don't try to start it before anything it needs is running. For example, if it is a web server, then bringing that process up before networking is up completely won't work.   

In the old days, we'd create a 15 line script with start/stop/restart/status options and put that into /etc/init.d/  Then we'd link that script under the specific 'run-level' directory for starting and stopping using numeric order to manage dependencies.  But systemd changed all that to be "easier."

[https://www.freedesktop.org/software/systemd/man/systemd.unit.html](https://www.freedesktop.org/software/systemd/man/systemd.unit.html) is the documentation home for systemd, such as it is.

---

