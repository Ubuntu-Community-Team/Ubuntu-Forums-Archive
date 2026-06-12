---
title: "How to add a program to startup?"
date: 2015-01-11
forum: General Help
---

### Post by TriforceOfKirby on 2015-01-11
So I installed Maximus using
```

sudo apt-get install maximus

```
I've read that it needs to be run on startup to auto-maximize windows; however, for some reason the "Startup Applications" program doesn't seem to exist in Ubuntu 14.10. So how can I add a this to startup?

---

### Post by Z80A on 2015-01-12
Add [FONT=courier new]maximus [/FONT]command to your [FONT=courier new].profile [/FONT]file in your home folder. If navigating with Nautilus file manager, make sure hidden files are visible (Ctrl-H).

---

### Post by Dennis N on 2015-01-12
> for some reason the "Startup Applications" program doesn't seem to exist in Ubuntu 14.10.

Although I have not upgraded to 14.10, I would be very surprised by this. There has always been a GUI dialog for user startup applications. Use the Dash and type "startup" and it should show up.

---

### Post by TriforceOfKirby on 2015-01-12
Ok I will try that, typing startup in dash shows nothing, I just did a clean install of Ubuntu 14.10 about a week ago, not upgraded.

---

### Post by TriforceOfKirby on 2015-01-12
Ok so I added the line to my .profile file and rebooted, maximus still isn't running according to System Monitor. Is the line supposed to be in a specific location in the .profile file? Also, is there perhaps a configuration setting that auto-maximizes windows? If so I wouldn't have any need for maximus.

---

### Post by ian-weisser on 2015-01-12
> **Brandon_Schumann said:**
> Ok I will try that, typing startup in dash shows nothing, I just did a clean install of Ubuntu 14.10 about a week ago, not upgraded.

How strange.

On my recent fresh install of 14.10, typing 'start' in dash exposes Startup Applications and Startup Disk Creator immediately. Perhaps a typo? Or you hadn't built the index yet? Or you installed some funny way?

You can also find it under Dash --> Application Lens --> 'Customization' Category Filter --> Scroll down to 'S' apps.

Or you can simply add the .desktop file to your /home/$YOU/.config/autostart directory. That's most of what Startup Applications does - it just looks prettier when it does it.

---

### Post by CantankRus on 2015-01-13
....or in the terminal check for errors when running...
```
gnome-session-properties
```

**PS:** I successfully installed maximus and added it to startup applications in 14.04.
Performs as intended.

---

### Post by TriforceOfKirby on 2015-01-13
Doing gnome-session-properties results in it saying "The program 'gnome-session-properties' is currently not installed. You can install it by typing: sudo apt-get install gnome-session-bin"

So I proceeded to install it with that command and it says it is already installed, trying gnome-session-properties again still doesn't work. Maybe I should do a re-install?
Startup Disk Creator is in the 'S' apps, Startup Applications is not.

Also Maximus doesn't seem to have a .desktop file.

What's the recommended tool for creating an Ubuntu 14.10 USB Drive? I used UNetbootin to create it when I did the install, should I use the Startup Disk Creator? Before I install Ubuntu should I use GParted and wipe my HDD? I have no important files on it currently so I could do that.

---

### Post by CantankRus on 2015-01-13
I just booted to a live iso of 14.10 where I was able to find startup applications in dash and successfully installed maximus.
Maximus is a desktop daemon and it installs a **.desktop** file in ** /etc/xdg/autostart**
The .desktop file however is not configured to start in Unity.

You can set maximus to autostart when you login by copying **/etc/xdg/autostart/maximus-autostart.desktop** to **~/.config/autostart**
and editing it.
```
cp /etc/xdg/autostart/maximus-autostart.desktop ~/.config/autostart
```

```
gedit ~/.config/autostart/maximus-autostart.desktop
```
...and change the line...
```
OnlyShowIn=GNOME;XFCE;
```
to
```
OnlyShowIn=GNOME;XFCE;[COLOR="#FF0000"]Unity;[/COLOR]
```
Save and close.

Log out and back in and maximus should be running.
You can check if running with....
```
ps aux | grep [m]aximus
```

As to the startup applications problem, if you think you may have caused this error by adding third party ppas
it may be easiest to reinstall.

---

### Post by mc4man on 2015-01-13
It's most likely nothing to do with your install method, more what you've done since.
Maybe take a read thru here, same 'nonsense' (not really), message about ''gnome-session-properties' is currently not installed', ect.
[http://ubuntuforums.org/showthread.php?t=2257311](http://ubuntuforums.org/showthread.php?t=2257311)

---

### Post by TriforceOfKirby on 2015-01-13
Thanks! Maximus is now running and I got Startup Applications back thanks to that other thread.

---

