---
title: "Xubuntu boots to last user instead of lightdm"
date: 2019-08-29
forum: General Help
---

### Post by lou6 on 2019-08-29
I recently installed Xubuntu 18.04.3 64-bit (replacing 32-bit to get out ahead of the elimination of 32-bt).  Most everything working well except when I power on for the day the machine boots up to the last user instead of to lightdm.  The only option checked in sessions&startup is prompt on logout and I'm sure that both users logout correctly before shut down. Obviously not a big problem but a mildly annoying one.

A little help will be greatly appreciated...

---

### Post by Artim on 2019-08-29
**Menu --> Settings --> Users and Groups**.  Explore that a bit, one user may have auto-login enabled.

---

### Post by again? on 2019-08-29
Although I don't see how this setting would have changed,
you can check lightdm settings with...
```
lightdm --show-config
```

Look for a setting [COLOR="#FF0000"]autologin-user[/COLOR]
You may see similar as below, where settings are shown, preceded by a corresponding [COLOR="#0000FF"]source file letter[/COLOR].
Bottom section shows source config files.
eg....
```
**[COLOR="#006400"]glen@Bionic:~$[/COLOR] lightdm --show-config**
   [Seat:*]
K  allow-guest=false
M  greeter-wrapper=/usr/lib/lightdm/lightdm-greeter-session
N  guest-wrapper=/usr/lib/lightdm/lightdm-guest-session
R  greeter-session=lightdm-gtk-greeter
P  xserver-command=X -core
Q  greeter-setup-script=xubuntu-numlockx
S  user-session=xubuntu
T  type=xlocal
T  display-setup-script=/sbin/prime-offload
T  display-stopped-script=/sbin/prime-switch
[COLOR="#0000FF"]**U**[/COLOR]  [COLOR="#FF0000"]autologin-user[/COLOR]=test

   [LightDM]
L  backup-logs=false

Sources:
K  /usr/share/lightdm/lightdm.conf.d/50-disable-guest.conf
L  /usr/share/lightdm/lightdm.conf.d/50-disable-log-backup.conf
M  /usr/share/lightdm/lightdm.conf.d/50-greeter-wrapper.conf
N  /usr/share/lightdm/lightdm.conf.d/50-guest-wrapper.conf
O  /usr/share/lightdm/lightdm.conf.d/50-slick-greeter.conf
P  /usr/share/lightdm/lightdm.conf.d/50-xserver-command.conf
Q  /usr/share/lightdm/lightdm.conf.d/50-xubuntu-numlock.conf
R  /usr/share/lightdm/lightdm.conf.d/60-lightdm-gtk-greeter.conf
S  /usr/share/lightdm/lightdm.conf.d/60-xubuntu.conf
T  /usr/share/lightdm/lightdm.conf.d/90-nvidia.conf
K  /usr/share/lightdm/lightdm.conf.d/50-disable-guest.conf
L  /usr/share/lightdm/lightdm.conf.d/50-disable-log-backup.conf
M  /usr/share/lightdm/lightdm.conf.d/50-greeter-wrapper.conf
N  /usr/share/lightdm/lightdm.conf.d/50-guest-wrapper.conf
O  /usr/share/lightdm/lightdm.conf.d/50-slick-greeter.conf
P  /usr/share/lightdm/lightdm.conf.d/50-xserver-command.conf
Q  /usr/share/lightdm/lightdm.conf.d/50-xubuntu-numlock.conf
R  /usr/share/lightdm/lightdm.conf.d/60-lightdm-gtk-greeter.conf
S  /usr/share/lightdm/lightdm.conf.d/60-xubuntu.conf
T  /usr/share/lightdm/lightdm.conf.d/90-nvidia.conf
[COLOR="#0000FF"]**U  /etc/lightdm/lightdm.conf**[/COLOR]
```

You can then, as admin comment out([COLOR="#008000"]**#**[/COLOR]) the [COLOR="#FF0000"]autologin-user[/COLOR] line in that file
so it looks like...
```
[COLOR="#008000"]**#**[/COLOR]autologin-user = [COLOR="#696969"]test[/COLOR]
```

If unsure, post the output of....
```
lightdm --show-config
```

---

