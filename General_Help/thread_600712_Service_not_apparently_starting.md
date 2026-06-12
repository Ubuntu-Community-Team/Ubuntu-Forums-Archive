---
title: "Service not apparently starting"
date: 2007-11-02
forum: General Help
---

### Post by gorlak75 on 2007-11-02
Hello,
    I have a specific question. Background: I have had a ubuntu computer 7.04 up and running for about 4 months so far with the webmin program installed and working like a champ. However since i was tinkering with different desktops (i cause most of my own problems with tinkering) for some reason webmin doesn't want to start after rebooting the machine. So I have to go the console and start the service manually. The program appears to be functioning correctly other than that ie: after i start the service all of the program's functions work. My question- where would i look and what log files would i need to look through, for errors on why a service wouldn't start, even if its already been configured to start? the program says its "suppose" to start at boot, and is located in the init.d folder, but in practical application never does, and "/etc/init.d/webmin start" starts the service just fine. i never really restart the computer, so once its running after a reboot there aren't any problems I'm just wondering what is going on under the hood to keep it from starting at boot time. 


Thanks in advance.

---

### Post by lolindrath on 2007-11-02
give this a try:

```
update-rc.d webadmin default
```

That should add the init script back into the boot process.

If that doesn't work you can look through your log directory (grep webmin /var/log/*).

--Lolindrath

---

### Post by gorlak75 on 2007-11-02
when i tried the update i get this-

 update-rc.d -n webmin defaults
 System startup links for /etc/init.d/webmin already exist.
(had to modify the command since it wasnt working completely)

and i looked through the log files for anything that had webmin associated with it, lots of log files but nothing that i saw that i thought out of place. i do however see -

/var/log/auth.log:Nov  2 20:39:13 desktop webmin[5511]: Webmin starting

i see that line but its the same line before and after i starting having this problem.

Thanks

---

