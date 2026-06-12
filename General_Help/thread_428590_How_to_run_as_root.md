---
title: "How to run as root"
date: 2007-04-30
forum: General Help
---

### Post by fourthdimension on 2007-04-30
Hey all

How do I run as root to tweak the preferences in guarddog?  Also, the telnet port remains open by default when the firewall is running - is that a security issue I should fix?
And what's a good telnet client?  I can't seem to get putty to work.


Thanks :cool:

---

### Post by aysiu on 2007-04-30
Alt-F2 ```
gksudo guarddog
```

Or, if you're using Kubuntu, Alt-F2 ```
kdesu guarddog
```

Read more here:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by ola on 2007-04-30
You could try to run telnet from the command line. If you need any more information about that telnet client you can try man telnet.

If you can use SSH instead that would be preferred since it is encrypted (and telnet is totally unencrypted).

If you want to run a program from the command line as root you can use sudo command. To get a sudo-shell you can use sudo -s.

Good luck!

---

### Post by fourthdimension on 2007-04-30
> **aysiu said:**
> Alt-F2 ```
gksudo guarddog
```

Or, if you're using Kubuntu, Alt-F2 ```
kdesu guarddog
```

Read more here:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

Thanks.  That worked pretty well except I got an odd error message:

```

  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
Link points to "/tmp/ksocket-root"
Link points to "/tmp/kde-root"
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
kbuildsycoca running...
Reusing existing ksycoca
kio (KService*): WARNING: The desktop entry file /usr/share/applications/DefaultPlugins.desktop has Type=Link instead of "Application" or "Service"
kio (KService*): WARNING: Invalid Service : /usr/share/applications/DefaultPlugins.desktop
kio (KSycoca): ERROR: No database available!
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
Launched ok, pid = 5890
/bin/cp: cannot stat `/etc/rc.firewall': No such file or directory

```

And I have putty SSH, but I can't get anything to work through the terminal...  I'm a bit new to that.

Thanks for the help so far, and for the quick response.

---

### Post by aysiu on 2007-04-30
> **fourthdimension said:**
> Thanks.  That worked pretty well except I got an odd error message: Did it launch successfully after that error message appeared? Did it appear to launch and then crash? Or did it not launch at all?

---

### Post by fourthdimension on 2007-04-30
Well, it launched, but then I had no internet...  (I didn't touch any of the settings yet).  I probably didn't have to, but I ended up reinstalling it because I couldn't find what went wrong.  Still doesn't work, though, and the same thing happened.  Convinced I'm a noob yet? :)

---

