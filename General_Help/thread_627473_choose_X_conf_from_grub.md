---
title: "choose X conf from grub"
date: 2007-11-30
forum: General Help
---

### Post by redsun82 on 2007-11-30
Hello.

I have a laptop and want to plug it to a separate monitor via the VGA output when I'm at home. Mine's not really a problem, as everything quite works, but if I understood well the switch from one monitor to the other can be done only by changing xorg.conf and restarting the server. By now I do this via the nvidia settings manager that comes with their drivers and that has an option to change the settings and save them to xorg.conf (if you run the manager with sudo), without fiddling with the file itself.

What I'd like to obtain is the possibility to plug the laptop to keyboard, monitor and mouse and startup without having to open it to use its monitor to do the switch. Is there a way to do so? As I hint in the title, maybe an option in grub's menu.lst to choose from different xorg configuration files, so I can startup differently depending if I'm at home or ouside?

The screens have different resolutions (and ratios), so I woludn't want a configuration that sends a single screen to both monitors, but if it's the simplest solution I'd take it, as changing resolution is at least something that can be done without an X restart...

Thanks in advance.

---

### Post by kidders on 2007-12-01
Hi there & welcome,

The new Xorg is supposed to be much more flexible than previous versions, when it comes to changing things around while it's running. Personally, I still like to explicitly configure it the way I used to with 7.2 though ... clearly you do too hehe.

I'm not sure there's a way to use grub to select the xorg.conf that gets used ... not a *clean* one anyway. It'd be far more desirable to find some other way of doing it. For instance, the presence/absence of a particular USB keyboard might be a good choice. That way, as well as avoiding having to find some way of passing messages between grub and Xorg, you wouldn't have to reboot your machine every time you wanted to switch configurations.

For instance ...```
$ lsusb
...
Bus 004 Device 002: ID 099a:610c Zippy Technology Corp. EL-610 Super Mini Electron luminescent Keyboard
...
```

```
$ [ -n "`lsusb | grep 099a:610c`" ] && echo "xorg.external.conf" || echo "xorg.internal.conf"
xorg.external.conf
```

On the basis of a test like that, you could construct a new /etc/init.d/gdm (eg /etc/init.d/gdm-real), and use it in place of Ubuntu's default display manager service. Of course, being able to detect the external monitor would be better, but that's not always feasible.

Is that any help?

---

### Post by redsun82 on 2007-12-01
Sounds cool (and also somewhat fun ;)), I'll try it when I'll have more time. In my case it would work perfectly.

Thanks!

---

### Post by kidders on 2007-12-01
No problem. :-)

---

### Post by redsun82 on 2007-12-01
Ok, I checked via the lsusb command and found the id of the usb hub inbuilt in the monitor, I therefore wrote the script /usr/sbin/gdm as

```

#! /bin/bash
[ -n "`lsusb | grep 0424:2504`" ] && cp /etc/X11/xorg.conf.home /etc/X11/xorg.conf || cp /etc/X11/xorg.conf.laptop /etc/X11/xorg.conf
gdm $*

```
(with the last line I wanted to pass eventual parameters to gdm, but don't know if I've done it right) where I prepared beforehand the two different xorgs.

Manually it works as a charm: if I stop gdm and runthe script it does exactly what it should.

Now, how do I tell the system to use this instead of gdm? I tried changing /X11/defaul-display-manager, and then fiddling with the gdm startup script /etc/init.d/gdm but nothing came out of it... Obviously if I configure any disaply manager this "new" one doesn't appear (no surprise), and it makes me choose just between the ones regularily installed.

---

### Post by redsun82 on 2007-12-02
I did it by adding the line in /etc/init.d/gdm script itself! Thanks!

---

