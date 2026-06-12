---
title: "Lost Suspend Mode in 14.04"
date: 2015-09-26
forum: General Help
---

### Post by oldefoxx on 2015-09-26
After the last automatic update Ubuntu 14.94 will no longer shut down when I clock on Suspend.

It does, however, return the screen to full brightness when I open the lid of the laptop again.  I posted the problem about the Brightness and Lock setting not locking the display setting and it going back to full brightness after a reboot, and now it wants to do it again after Suspens, but tt won't Suspend properly.

I get the feeling somebody is trying to tell me to move on to a later release.

---

### Post by pqwoerituytrueiwoq on 2015-09-26
last i checked suspend is not supposed to shutdown the system
* today my system decided to ask me for my password when i enter suspend

as for the brightness that could be a lot of things, you may need a boot parameter though what i did was make a script to record the brightness at shutdown and restore on boot via lightdm scripts
you an use a script like [backlightx]("http://pastebin.com/HzzHrS2g") (does not require a x session) or a application like xbacklight

also i don't have any idea what kind of hardware you are using...

---

### Post by oldefoxx on 2015-09-29
Thanks for the suggestions.  The suspend mode is back. but I had it where it did not shutdown at one point.  Seems to be sort of Iffy at times.  Might be related to what I was doing.

During an update today, I got this message:
> debconf: unable to initialize frontend: Gnome
debconf: (Can't locate Gtk2.pm in @INC (you may need to install the Gtk2 module) (@INC contains: /etc/perl /usr/local/lib/perl/5.18.2 /usr/local/share/perl/5.18.2 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.18 /usr/share/perl/5.18 /usr/local/lib/site_perl .) at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 91.)
debconf: falling back to frontend: Dialog

I think it is kin to a message I got on my other laptop awhile back.  I don't remember how it got fixed though.  It too the installation of a missing libgtk I think.  But thay's not close enough to get the job done.

---

### Post by oldefoxx on 2015-09-29
> **pqwoerituytrueiwoq said:**
> last i checked suspend is not supposed to shutdown the system
* today my system decided to ask me for my password when i enter suspend

as for the brightness that could be a lot of things, you may need a boot parameter though what i did was make a script to record the brightness at shutdown and restore on boot via lightdm scripts
you an use a script like [backlightx]("http://pastebin.com/HzzHrS2g") (does not require a x session) or a application like xbacklight

also i don't have any idea what kind of hardware you are using...

Suspend blanks  the screen and puts everything on hold.  On my old laptop, I have to revive it with a brief press on the power button.  On the new laptop, touvh any key will do it.  Or sometimes jusy lifting the lid.  But when it doesn't work, the screen stays lit.

I don't follow how you made a script to control your brightness.  You lost me on that one.  I did find the link for dealing with the autoupdate problem.

---

### Post by pqwoerituytrueiwoq on 2015-10-02
here is my configuration
relavant script lines are in blue and the command i ran to show the file is in green
```
[COLOR=#008000]chad@A54C-NB91:~$ cat /etc/lightdm/lightdm.conf[/COLOR]
[SeatDefaults]
greeter-session=lightdm-gtk-greeter
user-session=xubuntu
[COLOR=#0000ff]greeter-setup-script=/usr/local/bin/greeter-setup-script
session-cleanup-script=/usr/local/bin/session-cleanup-script[/COLOR]
session-setup-script=sh -c '/usr/local/bin/session-setup-script &'
#display-setup-script =
[COLOR=#008000]chad@A54C-NB91:~$ cat /usr/local/bin/greeter-setup-script[/COLOR]
#!/bin/bash
numlockx on
[COLOR=#0000ff]if [ -f /var/log/backlightx ];then
    val=$(cat /var/log/backlightx)
    if [ ${#val} -gt 0 ];then
        xbacklight -set $((10*$val))
    fi
fi[/COLOR]
if [ $(date +%H) -lt 9 ];then
    #Too early for standard brightness, make it super dim
    echo 50 > /sys/class/backlight/intel_backlight/brightness
fi
ogg123 /usr/share/sounds/ubuntu/stereo/system-ready.ogg &
exit
[COLOR=#008000]chad@A54C-NB91:~$ cat /usr/local/bin/session-cleanup-script [/COLOR]
#!/bin/bash
[COLOR=#0000ff]backlightx --get current > /var/log/backlightx[/COLOR]
pid="$(pgrep -f gmusicbrowser | head -1)"
if [ "0$pid" -gt "0" ]; then
    user="$(ps aux | awk '{print $1" "$2}' | grep $pid | awk '{print $1}')"
    sudo -u "$user" gmusicbrowser -cmd Quit > /var/log/testList
fi
ogg123 /usr/share/sounds/ubuntu/stereo/desktop-logout.ogg 2> /dev/null &
killall inhibit-powersave

```

---

