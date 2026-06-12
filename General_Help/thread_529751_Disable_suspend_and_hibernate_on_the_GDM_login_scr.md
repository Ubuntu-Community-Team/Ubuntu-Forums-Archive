---
title: "Disable suspend and hibernate on the GDM login screen"
date: 2007-08-19
forum: General Help
---

### Post by mrk112 on 2007-08-19
Is there any way to disable suspend and hibernate options on the GDM login screen?

I've used gconf-editor to disable them for all users when they're logged in, but they're still available on the login screen..

---

### Post by fastpakr on 2007-09-04
I'll bump this since I've got the same question.  Anybody?

---

### Post by jobr on 2008-05-01
Open a Terminal and enter the command below

```
§ sudo gedit /etc/gdm/gdm.conf
```

The file should open and you are looking for the section shown below

> # System command support.
#
# Reboot, Halt and suspend commands, you can add different commands separated
# by a semicolon.  GDM will use the first one it can find.
RebootCommand=/sbin/shutdown -r now "Rebooted via gdm."
HaltCommand=/sbin/shutdown -h now "Shut Down via gdm."
SuspendCommand=/usr/sbin/pm-suspend
HibernateCommand=/usr/sbin/pm-hibernate

# The following options specify how GDM system commands are supported.
#
# Specify which actions are displayed in the greeter.  Valid values are HALT,
# REBOOT, HIBERNATE, SUSPEND, and CUSTOM_CMD separated by semicolons.
SystemCommandsInMenu=HALT;REBOOT;HIBERNATE;SUSPEND;CUSTOM_CMD

# Specify which actions are supported by QUERY_LOGOUT_ACTION, SET_LOGOUT_ACTION
# and SET_SAFE_LOGOUT_ACTION.  Valid values are HALT, REBOOT, HIBERNATE, SUSPEND, and
# CUSTOM_CMD separated by semicolons.
AllowLogoutActions=HALT;REBOOT;HIBERNATE;SUSPEND;CUSTOM_CMD

When you find it, just modify the section above as you like :) I hope the config file explains itself.

Have a nice day :)

---

### Post by HDave on 2008-05-02
Under Gutsy, I was able to disable hibernate by editing /etc/default/acpi-support and commenting out the lines regarding hibernate.

However, after I upgraded to Hardy, it's back!  

Editing gdm.conf did turn it off either.  

I was able to disable it for my personal account via gconf-editor (apps/gnome-power-manager/general/can-hibernate), but I really want to disable it for the entire machine.

EDIT:  Do a "sudo" to edit as root, then when you uncheck the hibernate settings, click right on the setting and pick "Mandatory".  This sets the value firm for all users.

---

