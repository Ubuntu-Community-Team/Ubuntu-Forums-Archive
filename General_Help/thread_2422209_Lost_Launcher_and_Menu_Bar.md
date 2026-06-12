---
title: "Lost Launcher and Menu Bar"
date: 2019-07-03
forum: General Help
---

### Post by bilkay on 2019-07-03
When I started my laptop this morning, after I signed in, I got an internal error message, followed by a message from google dropbox (which I reluctantly installed a week or so ago). I responded to the dropbox message and then restarted the computer. I had to do an fsck which reported a whole lot of errors, most of which appeared to be related to dropbox. Now when I sign in, all I get is my desktop with no launcher bar or task bar. I could ctrl-alt-f{n] to get to a terminal and get a terminal by right-clicking in the desktop, and I was able to remove dropbox, but it didn't make any difference. Also, when I open a terminal by right-clicking in the desktop, when I right-click in the terminal and select "Show menu bar", it doesn't. Also, apps opened from the terminal don't have menu bars.

I found a thread ([https://ubuntuforums.org/showthread.php?t=2278870&highlight=Lost+Launcher+Menu+Bar](https://ubuntuforums.org/showthread.php?t=2278870&highlight=Lost+Launcher+Menu+Bar)) with a similar problem, except that it only applied to a single user. My problem is also with the Guest user. I applied the suggested fixes in that thread with no change. 

Here's the syslog entries from the last time I signed in: [http://paste.ubuntu.com/p/nkDvwtJrNp/](http://paste.ubuntu.com/p/nkDvwtJrNp/)

I'd really hate to have to do a re-installation.

---

### Post by bilkay on 2019-07-03
This didn't work either:

$ initctl restart unity-panel-service

---

### Post by bilkay on 2019-07-03
This also didn't work:

$ sudo apt-get install --reinstall ubuntu-desktop
$ sudo service lightdm restart

---

### Post by bilkay on 2019-07-03
Installed compizconfig-settings-manager, then ran DISPLAY=:0 ccsm and got the following errors:

compizconfig - Error: dlopen: /usr/lib/x86_64-linux-gnu/compizconfig/backends/libgsettings.so: file too short
compizconfig - Warning: unable to open backend gsettings, falling back to ini
compizconfig - Error: dlopen: /usr/lib/x86_64-linux-gnu/compizconfig/backends/libini.so: invalid ELF header
compizconfig - Error: failed to open any backends, aborting
Aborted (core dumped)

---

### Post by bilkay on 2019-07-03
Here's the output of unity --debug (it hangs up after "Error: Failed to load plugin: ccp" - had to ctrl-c):

```
compizconfig - Error: dlopen: /usr/lib/x86_64-linux-gnu/compizconfig/backends/libgsettings.so: file too short
compizconfig - Warning: unable to open backend gsettings, falling back to ini
compizconfig - Error: dlopen: /usr/lib/x86_64-linux-gnu/compizconfig/backends/libini.so: invalid ELF header
compizconfig - Error: failed to open any backends, aborting
unity-panel-service stop/waiting
unity-panel-service start/running, process 10862
[Thread debugging using libthread_db enabled]
Using host libthread_db library "/lib/x86_64-linux-gnu/libthread_db.so.1".
/usr/bin/compiz (core) - Info: Loading plugin: core
/usr/bin/compiz (core) - Info: Starting plugin: core
[New Thread 0x7ffff3613700 (LWP 10942)]
/usr/bin/compiz (core) - Info: Loading plugin: ccp
/usr/bin/compiz (core) - Error: Failed to load plugin: ccp

Thread 1 "compiz" received signal SIGINT, Interrupt.
0x00007ffff728074d in poll () at ../sysdeps/unix/syscall-template.S:84
84    ../sysdeps/unix/syscall-template.S: No such file or directory.
#0  0x00007ffff728074d in poll () at ../sysdeps/unix/syscall-template.S:84
No locals.
#1  0x00007ffff5aaf38c in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
No symbol table info available.
#2  0x00007ffff5aaf712 in g_main_loop_run () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
No symbol table info available.
#3  0x00007ffff7b4526f in compiz::private_screen::EventManager::startEventLoop(_XDisplay*) () from /usr/lib/x86_64-linux-gnu/libcompiz_core.so.ABI-20180221
No symbol table info available.
#4  0x00000000004017c1 in main ()
No symbol table info available.
```

---

### Post by bilkay on 2019-07-03
This is syslog from boot to login screen: [http://paste.ubuntu.com/p/433p7PrgDd/](http://paste.ubuntu.com/p/433p7PrgDd/)

By the way, the login screen has a task bar.

---

