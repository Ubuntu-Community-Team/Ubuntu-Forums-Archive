---
title: "Feedback: 18.04 pulseaudio unreliable"
date: 2020-10-04
forum: General Help
---

### Post by peridian on 2020-10-04
Just wanted to share my frustrations with pulseaudio on 18.04.  I had 16.04 for 2 years and had no issues.  Ever since upgrading I spent a month trying to get it to work properly.  The main clue was that no audio devices would appear in the sound settings device list, and a repeated series of pulseaudio start up errors in syslog.

Eventually I managed to figure out that there are some subtleties to the instructions in the official Ask Ubuntu help posts.

The steps that worked for me were:

1) > sudo adduser {USER} audio

It appears neither of my user accounts were added to the "audio" group.  This appears to affect pulseaudio's ability to access certain files (I _think_ it may be the lock file), presumably as it appears to run under the logged-in user.  Without this change, I got a lot of file permission errors whenever pulseaudio tried to run.

2) > [FONT=Consolas]sudo apt-get remove alsa-base pulseaudio[/FONT]

There are some versions of this command that try to remove the package "alsa"  This did not work for me, it has to be the "alsa-base" package (no idea why).

Also, you may have to pay attention for any dependency libraries that are removed as well.  In my case, I also had to reinstall "pulseaudio-module-bluetooth" and "libcanberra-pulse".

3) > rm -rf [FONT=Consolas]~/.config/pulse[/FONT]

It's not enough to do this on one user account, you have to get rid of it under every user account home directory.  In my case that was easy as there were only two users.

4) Reboot!

This seems to be the crucial thing, you have to reboot the system before attempting to reinstall anything.  Attempting the below before rebooting does not fix this.  I _think_ it's because something is left behind after the uninstall that automatically restores the old pulse directory, even though it's a new install.

5) > [FONT=Consolas]sudo apt-get install alsa-base pulseaudio[/FONT]

Remember any of those dependency libraries you removed as well.

6) > [FONT=Consolas]sudo alsa force-reload&#65279;[/FONT]

Not sure how necessary this command actually is, but it was part of the working solution, so...

7) > pulseaudio --start

All my previous attempts to run this command, along with "pulseaudio -k", always gave me various errors about socket connection retries or file permissions.  After following the above sequence of steps, it finally worked without issue.

Granted, I then had choppy sound issues on my headphones, but that turned out to be due to a bad version of bluez after the upgrade.  Updating that fixed it.

So yeah, I've got sound back and working as before, but the number of hoops I had to jump through to try and figure out the precise steps for how to fix it was annoying.  Hopefully the next upgrade will not be quite as frustrating.

Regards,
Rob.

---

### Post by TheFu on 2020-10-04
TL;DR

PulseAudio has been a problem for me since it was first introduced on Ubuntu. I've talked to friends who run different distros and they don't seem to have the same problems. To them, audio just works.  I was happily using a manual ALSA config for years, until Firefox decided to stop supporting ALSA directly.  All our systems still use ALSA, just with PulseAudio above it to make things "simpler."  

In the last week, I had to restart the pulseaudio daemon 3 times after it crashed. I have a script that does it now.
```
pulseaudio -k
pulseaudio &
```

Pulse likes it when our users are members of the plugdev group.  That should be automatic if you login on the console, but if we don't use the console, all sorts of thing break.  Plugdev unlocks access to normal desktop hardware like audio ports, micrphones, USB storage, stuff like that.  plugdev should automatically add audio and video groups to the userid on the console.  Check with the 'id' command.
  The intent is to stop the fun and games we used to play in the 1990s through remote connections playing audio on a system without the person using it understanding why.  There are some other methods around this. Pulse uses the X11 DISPLAY environment variable for terrible security.  To play audio over an ssh connection, but through the speakers connected to the remote system, just ssh in, then run the CLI music player after setting the DISPLAY correctly.  For example, 
```
DISPLAY=:0 /usr/bin/mpv /path/to/playlist.m3u
```

BTW, No need to reboot after making most changes.  Changing groups just requires a **newgrp** command or just logout and login again if you need more than 1 terminal to see the group change now. Basic group and user management stuff.

Bluetooth is a security nightmare. Takes less time to hack than to look up the 4 digit codes.

---

