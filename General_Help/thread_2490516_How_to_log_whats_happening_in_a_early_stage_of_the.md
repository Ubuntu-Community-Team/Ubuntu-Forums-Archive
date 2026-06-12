---
title: "How to log whats happening in a early stage of the booting process"
date: 2023-09-06
forum: General Help
---

### Post by marietto2008 on 2023-09-06
Hello.

I've upgraded Ubuntu 18.04 to 20.04 on my ARM (32 bit armhf) Chromebook. While Ubuntu 18.04 works perfectly,Ubuntu 20.04 has some kind of problem. I think that during the upgrade something broken.

At the beginning I've added this lines in rc.local :

```
journalctl --boot --no-pager > /home/linux/log 
exit 0
```

and I've got this log file : [https://pastebin.ubuntu.com/p/QZMygg8cjP/](https://pastebin.ubuntu.com/p/QZMygg8cjP/)

unfortunately,later,the same technique stopped working. It didn't produce that log file anymore. I tried to execute different commands and binary files putting them before and after "exit 0" on the file /etc/rc.local,but nothing has been created anymore. For example :

```

echo > /home/linux/ciao1
sudo systemctl set-default multi-user.target
echo > /home/linux/ciao2
journalctl --boot --no-pager > /home/linux/log0
/bin/journalctl --boot --no-pager > /home/linux/log1
/bin/./journalctl --boot --no-pager > /home/linux/log2
/bin/./journalctl --boot --no-pager > /log3
journalctl --boot --no-pager > /log4
exit 0
sudo systemctl set-default multi-user.target
echo > /home/linux/ciao3

```

What do you suggest me to do to ? I imagine that I should understand why it doesnt create a log file anymore and / or I should choose another technique to produce the log file from a different run level ? Anyway,I want to understand how to fix it.

---

### Post by TheFu on 2023-09-06
**dmesg** has the boot log.

As for why redirecting stdout to a log file doesn't work, perhaps you need to redirect stderr to a log file as well?
Search for "the art of the command line" for a guide in github.

Also, you can't try to save a log file to /log3 through redirection unless you are already root.  File permissions won't allow it and filling / with crap is just a terrible idea.
```
journalctl --boot --no-pager 2>&1 | tee  /home/linux/log4
```
or 
```
journalctl --boot --no-pager  2>&1 | sudo tee  /var/log/log4
```
would make more sense.  But all the data available is in the journals, so there's little reason to also dump it to a file.  journalctl provides access to journald's stuff and we can control how much is retained and search it for the specific things we need.

---

### Post by Holger_Gehrke on 2023-09-06
> **marietto2008 said:**
> Hello.

I've upgraded Ubuntu 18.04 to 20.04 on my ARM (32 bit armhf) Chromebook. While Ubuntu 18.04 works perfectly,Ubuntu 20.04 has some kind of problem. I think that during the upgrade something broken.

At the beginning I've added this lines in rc.local :


Would that be /etc/rc.local ? With systemd you need the service rc-local enabled and the file /etc/rc.local has to be executable (as opposed to the older init system which sourced that script, whether it was executable or not). The advantage of this is of course that rc.local doesn't have to be a shell script, it can be anything, for example a python script provided it has the right shebang line at the start ... The disadvantage is that you can't set variables in this script and expect them to be available to the rest of the system.

Holger

---

