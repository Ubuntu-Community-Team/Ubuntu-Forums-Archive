---
title: "Disable user list at log-in"
date: 2018-10-05
forum: General Help
---

### Post by sarisisop on 2018-10-05
New install 18.04.1 with one user. 

How can I turn off the Orange log-in panel where I have to click enter and just ask for the one users password ?

I tried dconf editor > org/gnome/login-screen > disable user list but no luck. 

Thank you.

---

### Post by TheFu on 2018-10-05
Depends on the display manager being used.  Which flavor of ubuntu will control that.  Each seems to do it a slightly different way, for example mine will only show uids over a certain value, so setting it to 63000 stops all others from being displayed.

I use lightdm, so the config is in /etc/lightdm/users.conf 
```
[UserList]
minimum-uid=5500
```  That should prevent any uids less than 5500 from being displayed. There are other settings to hide specific accounts by name too.

But the display manager will control that.  So, which DM does your install use?

---

### Post by sarisisop on 2018-10-05
> **TheFu said:**
> 

So, which DM does your install use?

Sorry I don't know. How would I find out ?

---

### Post by TheFu on 2018-10-05
Either post the flavor of ubuntu you are running or check the process table for something that ends in "dm".

It isn't safe to assume everyone uses the same stuff you use.  But I will assume you don't have the same file that I posted?

---

### Post by sarisisop on 2018-10-05
> **TheFu said:**
> Either post the flavor of ubuntu you are running or check the process table for something that ends in "dm".

It isn't safe to assume everyone uses the same stuff you use.  But I will assume you don't have the same file that I posted? 

It's the standard Ubuntu 18. I had too many problems with the upgrade from 16 to 18 and ended up doing a complete new install of 18. 

I think it's Ubuntu 18.04 LTS Gnome and using whatever came in the package, everything is default. 

Sorry I don't know any more than that.

---

### Post by TheFu on 2018-10-05
I don't have 18.04 here, so I cannot be certain.  Let's verify a few things. In a terminal, look at some stuff.

To see the official installed version, 
```
more /etc/lsb-release
```

To see which display manager is running (or at least get a good guess), 
```
 ps -eaf |grep dm| egrep -v grep
```

This will show 5-10 lines probably, but one will have something like gdm ... I think.

Mine shows: 
```
root       978     1  0 Sep30 ?        00:00:00 /usr/sbin/lightdm
root      1135   978  0 Sep30 ?        00:00:00 lightdm --session-child 12 19
```
among other lines.

See how the "code tags" makes things readable? Please do that too.

---

### Post by TheFu on 2018-10-05
Google found a few answers, but for some people those ended up in a boot-loop and the user needed help to break out of that.  If you aren't confident you can do that, may be best to avoid this for now.

[http://ubuntuhandbook.org/index.php/2018/04/hide-user-list-ubuntu-18-04-login-screen/](http://ubuntuhandbook.org/index.php/2018/04/hide-user-list-ubuntu-18-04-login-screen/) has a detailed answer that is different from the others. That is a reputable site, but I don't know if their solution actually works.  Make backups for anything you modify and have a way to put them back without being able to login normally.  May need to use a different tty or boot from alternate media.

---

### Post by sarisisop on 2018-10-05
> **TheFu said:**
> I don't have 18.04 here, so I cannot be certain.  Let's verify a few things. In a terminal, look at some stuff.

To see the official installed version, 
```
more /etc/lsb-release
```


```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=18.04
DISTRIB_CODENAME=bionic
DISTRIB_DESCRIPTION="Ubuntu 18.04.1 LTS"
```


> **TheFu said:**
> 

To see which display manager is running (or at least get a good guess), 
```
 ps -eaf |grep dm| egrep -v grep
```

This will show 5-10 lines probably, but one will have something like gdm ... I think.

Mine shows: 
```
root       978     1  0 Sep30 ?        00:00:00 /usr/sbin/lightdm
root      1135   978  0 Sep30 ?        00:00:00 lightdm --session-child 12 19
```
among other lines.

See how the "code tags" makes things readable? Please do that too.

```

root       897     1  0 15:40 ?        00:00:00 /usr/sbin/gdm3
root       907   897  0 15:40 ?        00:00:00 gdm-session-worker [pam/gdm-launch-environment]
gdm        972     1  0 15:40 ?        00:00:00 /lib/systemd/systemd --user
gdm        977   972  0 15:40 ?        00:00:00 (sd-pam)
gdm       1039   907  0 15:40 tty1     00:00:00 /usr/lib/gdm3/gdm-wayland-session gnome-session --autostart /usr/share/gdm/greeter/autostart
gdm       1066   972  0 15:40 ?        00:00:00 /usr/bin/dbus-daemon --session --address=systemd: --nofork --nopidfile --systemd-activation --syslog-only
gdm       1081  1039  0 15:40 tty1     00:00:00 /usr/lib/gnome-session/gnome-session-binary --autostart /usr/share/gdm/greeter/autostart
gdm       1097  1081  0 15:40 tty1     00:00:25 /usr/bin/gnome-shell
gdm       1124  1097  0 15:40 tty1     00:00:00 /usr/bin/Xwayland :1024 -rootless -terminate -accessx -core -listen 4 -listen 5 -displayfd 6
gdm       1131   972  0 15:40 ?        00:00:00 /usr/lib/at-spi2-core/at-spi-bus-launcher
gdm       1136  1131  0 15:40 ?        00:00:00 /usr/bin/dbus-daemon --config-file=/usr/share/defaults/at-spi2/accessibility.conf --nofork --print-address 3
gdm       1138   972  0 15:40 ?        00:00:00 /usr/lib/at-spi2-core/at-spi2-registryd --use-gnome-session
gdm       1142   972  0 15:40 ?        00:00:00 /usr/bin/pulseaudio --daemonize=no
gdm       1157  1097  0 15:40 tty1     00:00:00 ibus-daemon --xim --panel disable
gdm       1160  1157  0 15:40 tty1     00:00:00 /usr/lib/ibus/ibus-dconf
gdm       1163     1  0 15:40 tty1     00:00:00 /usr/lib/ibus/ibus-x11 --kill-daemon
gdm       1168   972  0 15:40 ?        00:00:00 /usr/lib/ibus/ibus-portal
gdm       1175  1081  0 15:40 tty1     00:00:00 /usr/lib/gnome-settings-daemon/gsd-xsettings
gdm       1181   972  0 15:40 ?        00:00:00 /usr/lib/dconf/dconf-service
gdm       1194  1081  0 15:40 tty1     00:00:00 /usr/lib/gnome-settings-daemon/gsd-a11y-settings
gdm       1195  1081  0 15:40 tty1     00:00:00 /usr/lib/gnome-settings-daemon/gsd-clipboard
gdm       1196  1081  0 15:40 tty1     00:00:01 /usr/lib/gnome-settings-daemon/gsd-color
gdm       1199  1081  0 15:40 tty1     00:00:00 /usr/lib/gnome-settings-daemon/gsd-datetime
gdm       1200  1081  0 15:40 tty1     00:00:00 /usr/lib/gnome-settings-daemon/gsd-housekeeping
gdm       1205  1081  0 15:40 tty1     00:00:00 /usr/lib/gnome-settings-daemon/gsd-keyboard
gdm       1206  1081  0 15:40 tty1     00:00:00 /usr/lib/gnome-settings-daemon/gsd-media-keys
gdm       1210  1081  0 15:40 tty1     00:00:00 /usr/lib/gnome-settings-daemon/gsd-mouse
gdm       1211  1081  0 15:40 tty1     00:00:00 /usr/lib/gnome-settings-daemon/gsd-power
gdm       1213  1081  0 15:40 tty1     00:00:00 /usr/lib/gnome-settings-daemon/gsd-print-notifications
gdm       1215  1081  0 15:40 tty1     00:00:00 /usr/lib/gnome-settings-daemon/gsd-rfkill
gdm       1216  1081  0 15:40 tty1     00:00:00 /usr/lib/gnome-settings-daemon/gsd-screensaver-proxy
gdm       1220  1081  0 15:40 tty1     00:00:00 /usr/lib/gnome-settings-daemon/gsd-sharing
gdm       1225  1081  0 15:40 tty1     00:00:00 /usr/lib/gnome-settings-daemon/gsd-smartcard
gdm       1226  1081  0 15:40 tty1     00:00:00 /usr/lib/gnome-settings-daemon/gsd-sound
gdm       1231  1081  0 15:40 tty1     00:00:00 /usr/lib/gnome-settings-daemon/gsd-wacom
gdm       1238  1157  0 15:40 tty1     00:00:00 /usr/lib/ibus/ibus-engine-simple
root      1304   897  0 15:41 ?        00:00:00 gdm-session-worker [pam/gdm-password]
fred      1326  1304  0 15:41 tty2     00:00:00 /usr/lib/gdm3/gdm-x-session --run-script env GNOME_SHELL_SESSION_MODE=ubuntu gnome-session --session=ubuntu
fred      1328  1326  3 15:41 tty2     00:04:50 /usr/lib/xorg/Xorg vt2 -displayfd 3 -auth /run/user/1000/gdm/Xauthority -background none -noreset -keeptty -verbose 3
```

I think after reading your last post I'll put up with it, it's a new install do I don't want to go messing it up for a small issue.

Thank you for your help and the information.

---

### Post by TheFu on 2018-10-05
Is there a reason you are using wayland?  It was removed from being the default after multiple problems were experienced in the test 17.10 release.

---

### Post by sarisisop on 2018-10-05
> **TheFu said:**
> Is there a reason you are using wayland?  It was removed from being the default after multiple problems were experienced in the test 17.10 release.

I just downloaded the latest from here [https://www.ubuntu.com/#download](https://www.ubuntu.com/#download) for Desktop and installed it. 

Sorry I don't know what wayland is or what it does.

---

### Post by TheFu on 2018-10-05
On the login screen, before you login, there is a gear to let us change the DE we use and the display. The default is xorg, so at some point you had to select Wayland instead.  Possible?
Wayland doesn't allow screen capture or video capture programs to work. I think that was the largest of the many issues.  There is much to like about Wayland and once remote applications and capture work correctly, I'll try it.  Until then, it is useless in my environment.  I routinely run programs on other computers and just have the window/GUI displayed on the system I sit behind.  X/Windows has supported this for many decades and it is a part of my workflow the last 30+ yrs.

---

### Post by deadflowr on 2018-10-05
The gear cog to change desktops only shows when the user has been selected, it'll show next the the password field.
(should be next to, or around the signin box)
ftr

---

### Post by TheFu on 2018-10-05
> **deadflowr said:**
> The gear cog to change desktops only shows when the user has been selected, it'll show next the the password field.
(should be next to, or around the signin box)
ftr

On lightDM is it always shown in the upper right corner area with a few other icons.

---

### Post by #&amp;thj^% on 2018-10-05
To disable the user list and also disallow guest logins on Lightdm only, add this content to a file in the "etc/lightdm/lightdm.conf.d" directory (I used the filename 00-hide-user-list.conf):
To make the file I used this:
```
sudoedit etc/lightdm/lightdm.conf.d/00-hide-user-list.conf

```
and then added the below:
```
[SeatDefaults]
greeter-hide-users=true
greeter-show-manual-login=true
allow-guest=false
```

Once this file is created, you&#8217;ll need to either restart your Ubuntu system, or restart the LightDM service. (I would just do a reboot. :) ) **_Note that restarting the LightDM service will kill your graphical applications, so be sure to save anything important first._** The next time you log in, you should have to manually enter both the username and the password, and guest logins should be disabled.
Let us know if you do want to allow a guest login. And if you prefer to disable a Wayland login.

---

### Post by deadflowr on 2018-10-05
Ubuntu uses gdm on 18.04

---

### Post by #&amp;thj^% on 2018-10-05
> **deadflowr said:**
> Ubuntu uses gdm on 18.04

Opps I read TheFu's "** ps -eaf |grep dm| egrep -v grep**" which shows Lightdm I will add this then
For GDM edit the following lines in /etc/gdm3/greeter.dconf-defaults:
Looks like:
```

#[org/gnome/login-screen]
# disable-user-list=true
```

Change to look like the below:
```

[org/gnome/login-screen]
disable-user-list=true
```

Be sure to edit both lines as above^^^
Thanks deadflowr More coffee needed

Mine:
```
 ps -eaf |grep dm| egrep -v grep && lsb_release -a
root       853     1  0 11:14 ?        00:00:00 /usr/sbin/lightdm
root       869   853  2 11:14 tty7     00:00:59 /usr/lib/xorg/Xorg -core :0 -seat seat0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
root      1003   853  0 11:14 ?        00:00:00 lightdm --session-child 12 21
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 18.04.1 LTS
Release:	18.04
Codename:	bionic

```

---

### Post by sarisisop on 2018-10-05
I've had a look and the Gear Icon has a choice of Ubuntu or Ubuntu on Wayland. 

The one at the top was Ubuntu and is the only one I have used. 

Screen capture works fine. 

Yes it's using gdm3. 

Hope that helps, but I think it's best I leave it alone and wait and see if there is a fix in an update. 

Though I do have a couple of questions: 

If Wayland was removed, how come I got it on the latest download ?

And as it's a new install would I be better of trying another download ?

---

### Post by TheFu on 2018-10-05
> **1fallen said:**
> Opps I read TheFu's "** ps -eaf |grep dm| egrep -v grep**" which shows Lightdm I will add this then
For GDM edit the following lines in /etc/gdm3/greeter.dconf-defaults:
Looks like:
```

#[org/gnome/login-screen]
# disable-user-list=true

Change to look like the below:
[code]
[org/gnome/login-screen]
disable-user-list=true
```

Be sure to edit both lines as above^^^
Thanks deadflowr More coffee needed

I saw this suggesting a few places, but some people said that resulted in a reboot-loop (as they explained it).  Seemed that something more was needed thanks to dconf.  I looked at about 5 different suggested answers for 18.04 before posting the link to ubuntuhandbook with the warning about the others.  At least that was my intention.
  But if you've tested this solutions, fantastic!

---

### Post by #&amp;thj^% on 2018-10-05
Wayland was not removed>>>just a option to login to.
No you do not need another download as both Wayland and Xorg are there.
And again if you want to disable wayland let us know. ;)

---

### Post by #&amp;thj^% on 2018-10-05
> **TheFu said:**
> I saw this suggesting a few places, but some people said that resulted in a reboot-loop (as they explained it).  Seemed that something more was needed thanks to dconf.  I looked at about 5 different suggested answers for 18.04 before posting the link to ubuntuhandbook with the warning about the others.  At least that was my intention.
  _But if you've tested this solutions, fantastic!_
I have yes. :)
But both dconf and the edited file i showed need to be set to "disable-user-list=true" there was a bug filed back on 17.10 and still present on 18.04.\
EDIT: I also have Wayland disabled. May be an important piece to note.
EDIT2: I came up with this from: [https://help.gnome.org/admin/system-admin-guide/stable/login-userlist-disable.html.en](https://help.gnome.org/admin/system-admin-guide/stable/login-userlist-disable.html.en)

---

### Post by sarisisop on 2018-10-05
Just wanted to say a big thank you to all of those that help newbies like me. The technical side is sometimes a bit over my head, but the support here is excellent. 

I'm a recent convert from windows and although I have had a few problems, I am much happier with Ubuntu.

---

### Post by TheFu on 2018-10-05
There's always more to learn, since the GUI guys keep changing things.

If you avoid the GUI, things don't change nearly as much.  I'm using many of the same scripts I wrote in the early 1990s today, for example.  And if you like, you can run those older, simpler GUIs. Many are still maintained by the main developer. Just comes down to user preference.

And sometimes the server stuff gets changed in ways that will eventually be "better" for some value of "better", though in my mind, 10.04 Ubuntu Server was the pinnacle of Linux server achievement (with a few small caveats). ;)

---

