---
title: "Ubuntu goes to black screen with text"
date: 2013-06-25
forum: General Help
---

### Post by EddieMonah on 2013-06-25
Hello!
I'm experiencing problems with my installation of Ubuntu from Wubi. Every time I boot up, it loads to a screen concluding in:
```
* The PostgreSQL server failed to start. Please check the log output:
[fail]
 * Starting haproxy haproxy [ OK ]
Starting rabbitmq-server: FAILED - check /var/log/rabbitmq/startup_{log, _err} rabbitmq_server.
speech-dispatcher disabled; edit /etc/default/speech-dispatcher
 * Starting the Winbind daemon winbind [ OK ]
saned disabled; edit /etc/default/saned
 * Starting web server apache2
(98)Address already in use: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs
Action 'start' failed.
The Apache error log may have more information.
[fail]
 * Checking battery state... [ OK ]
```
I can't do anything after this. I can access recovery mode. What should I do?

---

### Post by Ranko Kohime on 2013-06-25
The log you posted only includes things related to Apache, which is a web server.  Apache errors should not be stalling the boot.

Try pressing Ctrl+Alt+F1, and logging in.  If you can do that, someone else might be able to tell you which log to look into to find the real culprit.

---

### Post by EddieMonah on 2013-06-26
Thank you; I'll try that!

[edit]
I can log in to Ubuntu, but I can't open Nautilus.
```
** (nautilus:2524): WARNING **: Command line 'dbus-launch --autolaunch=23979778e8f3d5a219f4805e00000008 --binary-sntax --close-stderr' exited with non-zero exit status 1: Autolaunch error: x11 initialization failed.\n
Could not parse arguments: Cannot open display:
```

---

