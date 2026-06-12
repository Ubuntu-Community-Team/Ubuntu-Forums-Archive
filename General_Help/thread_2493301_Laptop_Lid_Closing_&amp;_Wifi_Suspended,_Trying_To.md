---
title: "Laptop Lid Closing &amp; Wifi Suspended, Trying To Find A Fix (22.04)"
date: 2023-12-10
forum: General Help
---

### Post by nbbelleau on 2023-12-10
I'm basically using a dedicated old laptop to run a plex server on 24/7 and I want to be able to leave the laptop with the lid closed without it going into suspend mode.

Here are some solutions I have tried;


[LIST=1]
[*]Installing Gnome-Tweaks and changing the ''Suspend when laptop lid is closed''
[*]Changing the configuration file in /etc/systemd/logind.conf from #HandleLidSwitch=suspend to #HandleLidSwitch=Ignore
[/LIST]

Anything else you guys think might work?

Thanks!

---

### Post by MAFoElffen on 2023-12-10
If the base OS is Ubuntu Desktop Edition, do
```

gsettings set org.gnome.settings-daemon.plugins.power lid-close-ac-action blank

```
While plugged in, when the lid is closed, that will turn off / blank the display, without turning off, suspending or hibernating the computer.

---

### Post by nbbelleau on 2023-12-14
> **MAFoElffen said:**
> If the base OS is Ubuntu Desktop Edition, do
```

gsettings set org.gnome.settings-daemon.plugins.power lid-close-ac-action blank

```
While plugged in, when the lid is closed, that will turn off / blank the  display, without turning off, suspending or hibernating the  computer.


Unfortunately that did not work. I'm not sure if I'm supposed to be getting a response from the terminal upon entering that command but I get nothing, and the Wi-Fi still goes in suspend mode.

---

### Post by MAFoElffen on 2023-12-14
Okay. Time for a bigger hammer...

If this
```

grep -A10 'Do we ignore the lid state' /etc/UPower/UPower.conf

```
Returns this:
```

# Do we ignore the lid state
#
# Some laptops are broken. The lid state is either inverted, or stuck
# on or off. We can't do much to fix these problems, but this is a way
# for users to make the laptop panel vanish, a state that might be used
# by a couple of user-space daemons. On Linux systems, see also
# logind.conf(5).
#
# default=false
IgnoreLid=false

```
Then do this:
```

sudo sed -i 's/IgnoreLid=false/IgnoreLid=true/g' /etc/UPower/UPower.conf

```
If this
```

grep 'Handle' /etc/systemd/logind.conf

```
returns these values, and are all commented like this
```

#HandlePowerKey=poweroff
#HandleSuspendKey=suspend
#HandleHibernateKey=hibernate
#HandleLidSwitch=suspend
#HandleLidSwitchExternalPower=suspend
#HandleLidSwitchDocked=ignore
#HandleRebootKey=reboot

```
Then do this
```

sudo sed -i 's/\#HandleLidSwitchExternalPower=suspend/HandleLidSwitchExternalPower=nothing/g' /etc/systemd/logind.conf
sudo echo -e "HandleLidSwich=ignore" >> /etc/systemd/logind.conf
sudo systemctl restart systemd-logind

```
The restart of that will log you out in the process... Test.

---

### Post by nbbelleau on 2023-12-15
> **MAFoElffen said:**
> 
Then do this
```

sudo -i 's/\#HandleLidSwitchExternalPower=suspend/HandleLidSwitchExternalPower=nothing/g' /etc/systemd/logind.conf
sudo echo -e "HandleLidSwich=ignore" >> /etc/systemd/logind.conf
sudo systemctl restart systemd-logind

```
The restart of that will log you out in the process... Test.


I get: 
```

-bash: line 1: /etc/systemd/logind.conf: Permission denied

```

---

### Post by MAFoElffen on 2023-12-15
Dang, besides having a slight typo there, there also seems to be a permissions challenge with that.

If the permissions on that file is 644 or 600, then you will have to be root to make changes to that file. Let me check...
```

mafoelffen@Mikes-B460M:~$ ls -l /etc/systemd/logind.conf
-rw-r--r-- 1 root root 1374 Apr  7  2022 /etc/systemd/logind.conf

```
That's the problem there... Instead do this first
```

sudo su
sed -i 's/\#HandleLidSwitchExternalPower=suspend/HandleLidSwitchExternalPower=nothing/g' /etc/systemd/logind.conf
echo -e "HandleLidSwich=ignore" >> /etc/systemd/logind.conf
systemctl restart systemd-logind

```

---

