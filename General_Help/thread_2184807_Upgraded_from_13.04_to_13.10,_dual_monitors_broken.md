---
title: "Upgraded from 13.04 to 13.10, dual monitors broken"
date: 2013-10-30
forum: General Help
---

### Post by Chibana on 2013-10-30
It's 64-bit Ubuntu with nvidia GT 640 video card.  I have two monitors, one on the HDMI out and one on the VGA out.  VGA has always been display 0 and HDMI 1, but I used the nvideo settings tool to configure X so that HDMI was always the left (main) monitor and the VGA the right monitor, and also forced the resolution of HDMI to 1920x1080 and VGA to 1280x1024.  I saved these settings to both xorg.conf and to users' .nvidia-settings-rc file.  This worked great on 13.04.

After the upgrade, both gdm and lightdm now default to the VGA monitor, and the system thinks that the two are reversed.  It's acting like it's not using the xorg.conf file at all.  I do not have Mir installed (I have verified).  For some reason, using the nvidia settings tool and resaving my .nvidia-settings-rc file seems to have worked for my account, but not for my son's or my wife's accounts.  My account is an administrator, so maybe that has something to do with it.  I've verified permissions on all three .nvidia-settings-rc files.  Each is owned by the appropriate user and has 0644 permissions.

I can get the other two accounts' monitors switched around if I use randr to save a script and then manually run it, but putting that script in .xprofile does not work, even with a 10 second sleep delay.

I'm at a loss.  It seems like every time I upgrade or install to the latest version of Ubuntu too soon I get burned.  Why don't I learn?

---

### Post by Chibana on 2013-10-31
I was able to get a temporary (I hope) workaround by putting an xrandr command in each user's startup programs.  The lightdm greeter is still a bit messed up.

---

