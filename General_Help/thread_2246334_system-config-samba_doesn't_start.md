---
title: "system-config-samba doesn't start"
date: 2014-09-30
forum: General Help
---

### Post by kleinempfaenger on 2014-09-30
Messing around with Samba suddenly system-config-samba stopped working, I think after restart.

Traceback (most recent call last):
  File "/usr/sbin/system-config-samba", line 45, in <module>
    mainWindow.MainWindow(debug_flag)
  File "/usr/share/system-config-samba/mainWindow.py", line 116, in __init__
    self.samba_user_data = sambaUserData.SambaUserData(self)
  File "/usr/share/system-config-samba/sambaUserData.py", line 46, in __init__
    self.readSmbPasswords()
  File "/usr/share/system-config-samba/sambaUserData.py", line 63, in readSmbPasswords
    raise RuntimeError, (_("You do not have permission to execute %s." % pdbeditcmd))
RuntimeError: You do not have permission to execute /usr/bin/pdbedit.

Uninstalled and purged samba, but nothing. I think Samba is working.
How could I make system-config-samba to work again?

Thanks, kl

---

### Post by John_Ten on 2014-09-30
Maybe try the fixes here:[https://bugs.launchpad.net/ubuntu/+source/system-config-samba/+bug/964681](https://bugs.launchpad.net/ubuntu/+source/system-config-samba/+bug/964681). e.g. gksudo system-config-samba

---

### Post by kleinempfaenger on 2014-09-30
Thanks, I had tried that before - without success. I should have mentioned that. 
What is the problem for this bug? 
Is there another fix? 
Greetings

---

