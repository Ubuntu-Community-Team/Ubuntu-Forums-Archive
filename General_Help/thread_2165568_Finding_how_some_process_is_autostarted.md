---
title: "Finding how some process is autostarted"
date: 2013-08-05
forum: General Help
---

### Post by ofnuts on 2013-08-05
I have a process whihc is autostarted to "help" me but since I don't use it it is a waste of resources. I'm trying to find how it is autostarted. I have checked
[LIST]
[*]~/.config/autostart/
[*]/etc/init.d,
[*]/etc/rc*.d
[*]/etc/rc.local
[/LIST]
.. and I couldn't find it.

Its parent is "init" and it runs with my id.

Where else should I look?

---

### Post by GwL3eNC on 2013-08-05
Hi,

have you tried 

sudo update-rc.d -f yourprocess remove 

Or you can try install rcconf or sysv-rc-conf tool.

---

### Post by ian-weisser on 2013-08-05
Sysvinit startup processes are in /etc/init.d
Upstart (native) startup processes are in /etc/init

---

### Post by ofnuts on 2013-08-05
These are the place I looked in. Also fount /etc/xdg/autostart/*.desktop... but my application isn't there either. 

OTOH deep down in the application preferences, you can disable the preload, so there :)

---

### Post by ian-weisser on 2013-08-06
Here is another approach:

If you can identify the process (PID), you can find the name and other clues using "cat /proc/$PID/cmdline"

In this example, the command is "foo" with no flags, and it requires Python.
```
$ cat /proc/2302/cmdline
/usr/bin/python/**usr/bin/foo**/var/run/foo.pid
```

If you know the command, you can see what package installed it using "dpkg -S /path/to/application"

For example, the "hello" command is installed by the "hello" package:
```
$ dpkg -S /usr/bin/hello
hello: /usr/bin/hello
```

If you know the package name, you can see how it autostarts by listing the files using "dpkg -L packagename"

For example, the "cron" package is autostarted using both sysvinit-compatible and upstart-native methods:
```
$ dpkg -L cron
[...]
/etc/init/cron.conf
[...]
/etc/init.d/cron
```

If your helper process is installed by a package, you can also simply uninstall the package.
We don't know if your helper application is installed by a package, of course. Only you can tell us that.

---

### Post by ofnuts on 2013-08-06
Went that route too...  the application is big (Lotus Symphony, don't ask :)), but "dpkg -L symphony  | grep /etc" doesn't list anything suspiscious

---

### Post by ian-weisser on 2013-08-06
Tried the solution at [http://www-10.lotus.com/ldd/lswiki.nsf/dx/How_to_prevent_Lotus_Symphony_3_from_running_at_start_up](http://www-10.lotus.com/ldd/lswiki.nsf/dx/How_to_prevent_Lotus_Symphony_3_from_running_at_start_up) ?

---

### Post by ofnuts on 2013-08-06
Yes, see an earlier post... it works ok,  but it has now become a matter of curiosity...  I disabled it, then re-enabled it to continue the hunt :) This mere function means that this is done somewhere in the user's domain, so there should be some clue under /home/me.... 

Of course there is always the solution to take a snapshot of the whole system before/after enabling it and watch for differences :)

Hmmm Looking at PID numbers may help me find out when it is started by comparing that with the PID of other user-level processes...

---

### Post by GwL3eNC on 2013-08-06
Hallo,

cant bring you the PPID further? As i understand it is the process which starts your helper. Then evtl.
you can try to proceed as above.

---

