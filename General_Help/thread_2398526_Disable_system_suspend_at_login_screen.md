---
title: "Disable system suspend at login screen"
date: 2018-08-13
forum: General Help
---

### Post by fpvflyingbits on 2018-08-13
Hi there,

I'm having a tough time with this one. I've tried a few things I've found a few possible solutions but the system is still going to sleep. Found forum posts that did similar things but still frustrated. If anyone can help shed some light on the power management organization that's confounding me I'd certainly appreciate it!

**My problem: **
I'm trying to keep a laptop from going to into suspend after a reboot where the lid was never opened. I often SSH into this system to access it, and rarely interact with it directly. I occasionally have need for it to have a GUI available, otherwise I would have installed the Server flavor of Ubuntu. I may need to reboot the system while connected remotely through SSH. If I do this, **20 minutes** after reboot (timed and also based on ping icmp_seq ~1200 from power on to network loss when pinging it), if I'm not logged back in/active, the system suspends itself and networking is powered down, forcing me to open the lid and close it again before I can SSH in again remotely. 

If I log in directly on the laptop, then lock the screen/session and close the lid, it  will never suspend, following the settings I've given it under "System  Settings" --> "Power"

My issue is more directly related to how Ubuntu handles power settings before any user has logged in. 

**Other things to note:**
Running **Ubuntu Desktop 16.04 LTS**. It would complicate things if I had to upgrade for this. 
The network connection is wired
The laptop is always plugged in to power.
The battery is not discharging, and remains at 100% throughout the issue.
The system in question is not connected to the internet.

**I have tried the following so far **(on recommendations from existing forum posts here and elsewhere)**:**

-Settings in "System Settings" --> "Power" to the following, which work so long as I log in once between reboots, but do not seem to have any effect on the system after a reboot, before login, at the login screen as I mentioned.

[TABLE="class: grid, width: 500, align: left"]
[TR]
[TD][/TD]
[TD]On battery power:[/TD]
[TD]When plugged in:[/TD]
[/TR]
[TR]
[TD]Suspend when inactive for[/TD]
[TD]Don't suspend[/TD]
[TD]Don't suspend[/TD]
[/TR]
[TR]
[TD]When power is critically low[/TD]
[TD](blank)[/TD]
[TD][/TD]
[/TR]
[TR]
[TD]When the lid is closed[/TD]
[TD]Do nothing[/TD]
[TD]Do nothing[/TD]
[/TR]
[/TABLE]







-Change /etc/systemd/logind.conf to uncomment/modify the following lines:
```
HandleLidSwitch=ignore     # Was suspend
IdleAction=ignore    # Was commented out... I know it says it's a default, but I wanted to be sure it was being set properly
IdleActionSec=30min    # Was commented out. Not sure if it's required when the above is uncommented.
```

I don't believe the above IdleAction is to blame, as the suspend happens after 20 minutes, not 30.

-Change /etc/UPower/UPower.conf:
```
IgnoreLid=true     # Was false
```


Thank you in advance.

---

### Post by ajgreeny on 2018-08-13
Not sure what you've already tried but just in the hope that it helps have a look at the thread at [https://ubuntuforums.org/showthread.php?t=2283523](https://ubuntuforums.org/showthread.php?t=2283523).

---

### Post by fpvflyingbits on 2018-08-14
Thanks for the link, ajgreeny, I hadn't seen that one yet. 

I wasn't too hopeful about this since the default, and the value this   held prior to me setting it (found with "gsettings get" and the same   string) was 300, or 5 minutes, and my issue happens at 20 minutes on the   dot.

No joy.

In case anyone else needs to run a gsettings command like this in the future, I needed a bit more to make it work without X11:

```
sudo su
su lightdm -s /bin/bash
dbus-launch gsettings set com.canonical.unity-greeter idle-timeout 0
exit
exit
```

While trying to figure out how to use gsettings without X11, I happened on this other site, with a similar-but-not-same problem:

[http://php.mandelson.org/mk3/index.php/2012/06/19/stopping-laptop-suspend-on-ubuntu-linux/](http://php.mandelson.org/mk3/index.php/2012/06/19/stopping-laptop-suspend-on-ubuntu-linux/)

It's an older entry, but there was still a setting corresponding to the  command he listed on my system, which was set to "suspend". I changed  it to "nothing" :

```
sudo su
su lightdm -s /bin/bash
dbus-launch gsettings set org.gnome.settings-daemon.plugins.power lid-close-ac-action nothing
exit
exit
```

No joy.

I also found a setting in the BIOS for the computer to disable the OS's ability to go into sleep mode. 

No joy. It didn't seem to stop Ubuntu from going into sleep. Perhaps at least not the same type of sleep/suspend?

Then I found this bugtracker which sounded relevant:

[https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/1759325](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/1759325)

which lead me to:

[https://gitlab.gnome.org/GNOME/gnome-settings-daemon/commit/2fdb48fa](https://gitlab.gnome.org/GNOME/gnome-settings-daemon/commit/2fdb48fa)

where I found the required settings to change to solve my problem:

```
sudo su
su lightdm -s /bin/bash
dbus-launch gsettings set org.gnome.settings-daemon.plugins.power sleep-inactive-ac-timeout 0
exit
exit
```

As the comments mentioned, setting the key to 0 disabled the behavior of system sleep due to inactivity while under AC power. 

There is an equivalent key for battery power, which I did not need, but might help someone else in the future: sleep-inactive-battery-timeout

---

