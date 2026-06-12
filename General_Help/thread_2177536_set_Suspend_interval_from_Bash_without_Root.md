---
title: "set Suspend interval from Bash without Root"
date: 2013-09-29
forum: General Help
---

### Post by dgm5555 on 2013-09-29
I would like to be able to set the duration of inactivity before ubuntu suspends from a bash script without needing sudo (just like is possible with the system settings/power dialog). 
This is because I'm sending commands to a 3D printer, and if I forget to inactivate suspend the print is ruined (the printer doesn't have a large enough memory to store the entire print.
I want to set either 5mins or "don't suspend".
There seem to be a number of options, but they all either require sudo (root), or no longer work due to version changes. I don't want to have to enter root (or do it manually from the power dialog) each time I load the program as this is prone to me forgetting or is pesky entering root password each time I enter or exit the program, so I'm hoping there's another option.
Thanks
David

---

### Post by TheFu on 2013-09-29
I don't really understand, but could an alias named as the program work which incorporates the sudo stuff you want?  It is possible to have sudo not ask for a password for specific commands, BTW.[B]
man sudoers[/B] explains.

---

### Post by steeldriver on 2013-09-29
You can access the parameters from the 'System Settings --> Power' dialog from the command line by using gsettings or dconf to access the org.gnome.settings-daemon.plugins.power schema e.g.

```
gsettings list-recursively org.gnome.settings-daemon.plugins.power
```

```

$ gsettings get org.gnome.settings-daemon.plugins.power sleep-inactive-battery-timeout
1800
$ gsettings get org.gnome.settings-daemon.plugins.power sleep-inactive-battery-type
'suspend'

```

The timeout interval is in seconds i.e. 1800 sec = 30 mins in the example above. For example to disable suspend when on battery power, set the sleep-inactive-battery-timeout to zero

```

$ gsettings set org.gnome.settings-daemon.plugins.power sleep-inactive-battery-timeout 0

```

---

