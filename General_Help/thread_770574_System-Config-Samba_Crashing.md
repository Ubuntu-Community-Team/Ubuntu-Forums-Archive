---
title: "System-Config-Samba Crashing"
date: 2008-04-27
forum: General Help
---

### Post by skathrein on 2008-04-27
System-Config-Samba is crashing every time I try to run it.  I've tried reinstalling both it and samba itself but that doesn't help.  Has anyone else had this problem or found a solution?
Thanks.

---

### Post by cb951303 on 2008-04-27
I have the same problem 
here is the console output

```

cosku@cosku-desktop:~$ gksu system-config-samba
File "/usr/sbin/system-config-samba", line 41, in <module> mainWindow.MainWindow(debug_flag)
File "/usr/share/system-config-samba/mainWindow.py", line 118, in __init__ self.basic_preferences_win = basicPreferencesWin.BasicPreferencesWin(self, self.xml, self.samba_data, self.samba_backend, self.main_window)
File "/usr/share/system-config-samba/basicPreferencesWin.py", line 93, in __init__ self.admin = libuser.admin()
SystemError: could not open configuration file `/etc/libuser.conf': No such file or directory

```

---

### Post by skathrein on 2008-04-27
Yeah, same report for me too:
```
File "/usr/sbin/system-config-samba", line 41, in <module> mainWindow.MainWindow(debug_flag)
File "/usr/share/system-config-samba/mainWindow.py", line 118, in __init__self.basic_preferences_win = basicPreferencesWin.BasicPreferencesWin(self, self.xml, self.samba_data, self.samba_backend, self.main_window)
File "/usr/share/system-config-samba/basicPreferencesWin.py", line 93, in __init__self.admin = libuser.admin()
SystemError: could not open configuration file `/etc/libuser.conf': No such file or directory

```

---

### Post by Thanh-BKK on 2008-04-27
Hello :)

Identical problem here, Hardy Heron 8.04. Already re-installed Samba - no avail, it crashes each time i open it.

Best regards....

Thanh

---

### Post by milia on 2008-04-27
Same effect here, different buggy lines though.

Sent crash reports.

Samba sharing works just fine though.


```

milia@Archimedes:~$ gksu system-config-samba
    mainWindow.MainWindow(debug_flag)
  File "/usr/share/system-config-samba/mainWindow.py", line 118, in __init__
    self.basic_preferences_win = basicPreferencesWin.BasicPreferencesWin(self, self.xml, self.samba_data, self.samba_backend, self.main_window)
  File "/usr/share/system-config-samba/basicPreferencesWin.py", line 93, in __init__
    self.admin = libuser.admin()
**SystemError: could not open configuration file `/etc/libuser.conf': No such file or directory**
```

---

### Post by cb951303 on 2008-04-27
launchpad had the solution

```
 sudo touch /etc/libuser.conf 
```

---

### Post by Thanh-BKK on 2008-04-27
Hi :)

That does work indeed! 

Thank you so much!!

Thanh

---

### Post by skathrein on 2008-04-27
Thanks cb951303!!!
Works perfectly now.

By the way, I know its a strange question, but how did you find the solution...I have no idea how to search launchpad.  Any guidance is appreciated.
Thanks again!

---

### Post by cb951303 on 2008-04-28
no problem :)

1-goto [https://bugs.launchpad.net/ubuntu/](https://bugs.launchpad.net/ubuntu/)
2-then search for the package name (i.e: samba-config-error) with "newest first" ordering
3-look for the specific bug description and read the 'comments' :guitar:

PS: Also if the bug report doesn't exist, you can always add it :popcorn:

cheers

---

### Post by milia on 2008-04-28
> **cb951303 said:**
> launchpad had the solution

```
 sudo touch /etc/libuser.conf 
```

Thank you :).

---

