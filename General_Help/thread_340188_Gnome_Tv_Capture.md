---
title: "Gnome Tv Capture"
date: 2007-01-16
forum: General Help
---

### Post by Atrio05 on 2007-01-16
Hi everyone I have recently tried to install MythTV and of course NO LUCK there, But any way i was wondering if anyone here has or has heard of a good (and easy to install) program to capture live TV and schedule recordings and stuff along those lines? If anyone has any information please reply or feel free to PM me! 

Thanx!!

---

### Post by ardchoille42 on 2007-01-16
I'd be very interested in this too :)

---

### Post by Atrio05 on 2007-01-16
There's got to be something out there. Right?

---

### Post by JohnPhys on 2007-01-17
What specifically didn't work with MythTV?  I've got it running on a breezy box just using the packages from the repos, works like a charm.  Perhaps I could help?

---

### Post by anaconda on 2007-01-17
kaffeine is both good and easy to install..

However it is KDE program not GNOME. I use it in GNOME, and it works wel.

---

### Post by gmc on 2007-01-17
> **Atrio05 said:**
> Hi everyone I have recently tried to install MythTV and of course NO LUCK there, But any way i was wondering if anyone here has or has heard of a good (and easy to install) program to capture live TV and schedule recordings and stuff along those lines? If anyone has any information please reply or feel free to PM me! 

Thanx!!

I'm using **crontab** and **at** and a set of scripts to record TV shows on a weekly basis. It's not fancy, but it works reliably for me. Unfortunately I'm at work right now and no access to the scripts and due to the nature of my setup/hardware they probably won't work for you, but they might give you a starting point. I'll post them here, when I get home.

Gord

```

#!/bin/bash

OUTPUT="~/Desktop/TV/`date +%y%m%d-%H%M.avi`"

echo false > /sys/class/pvrusb2/*/ctl_mute/cur_val
echo 58980 > /sys/class/pvrusb2/*/ctl_volume/cur_val
echo television > /sys/class/pvrusb2/*/ctl_input/cur_val
echo 77250000 > /sys/class/pvrusb2/*/ctl_frequency/cur_val

mencoder -ovc lavc    -lavcopts vcodec=mpeg4:vbitrate=1400 \
         -oac mp3lame -lameopts br=96 -vop scale=512:384,pp=lb \
         -endpos 00:29:55 \
         -o $OUTPUT /dev/video

exit 0

```The above script sets the channel on my WinTV PVR (usb2) to channel 5 and records for approximately 30 minutes (29m 55sec). It ensures the recording is not muted and the volume is set to a reasonable level.

I have a series of such scripts with various channels set and length of record times. Now in my crontab I have the following:

```

# Cornation St (Chnnl 5)
1 0 * * 1-5  /usr/bin/at -f ~/bin/30m  18:00

# WWE RAW Recovery (Chnnl 53)
1 0 * * 1    /usr/bin/at -f ~/bin/135m 22:00

# WWE Smackdown (Chnnl 53)
1 0 * * 5    /usr/bin/at -f ~/bin/120m 20:00

# Hockey Night in Canada (Chnnl 5)
1 0 * * 6    /usr/bin/at -f ~/bin/180m 19:00

```Now cron will run "at" at midnight to run at the appropriate time (huh :-) ). I use "at" so if I need to change or cancel the recording, I can issue 'atrm #' and stop the recording and/or issue 'at -f ~/bin/<script name> <new time>".

Hope that made sense!

Gord

---

### Post by Atrio05 on 2007-01-17
> **JohnPhys said:**
> What specifically didn't work with MythTV?  I've got it running on a breezy box just using the packages from the repos, works like a charm.  Perhaps I could help?

[LEFT]well i am having problems getting the mythfrontend to load heres the errors i get back : *josh@josh-ubuntu:~$ mythfrontend*
*X Error: BadDevice, invalid or uninitialized input device 168*
*  Major opcode:  145*
*  Minor opcode:  3*
*  Resource id:  0x0*
*Failed to open device*
*X Error: BadDevice, invalid or uninitialized input device 168*
*  Major opcode:  145*
*  Minor opcode:  3*
*  Resource id:  0x0*
*Failed to open device*
*2007-01-17 13:13:53.618 Using runtime prefix = /usr*
*2007-01-17 13:13:53.658 Gnome-Screensaver support enabled*
*2007-01-17 13:13:53.659 DPMS is active.*
*2007-01-17 13:13:53.660 Unable to read configuration file mysql.txt*
*2007-01-17 13:13:53.661 Trying to create a basic mysql.txt file*
*2007-01-17 13:13:53.661 Could not open settings file /home/josh/.mythtv/mysql.txt for writing*
[I]2007-01-17 13:13:53.662 Failed to init MythContext, exiting.
[/I]
can anyone help with this?[/LEFT]

---

### Post by Atrio05 on 2007-01-17
> **gmc said:**
> I'm using **crontab** and **at** and a set of scripts to record TV shows on a weekly basis. It's not fancy, but it works reliably for me. Unfortunately I'm at work right now and no access to the scripts and due to the nature of my setup/hardware they probably won't work for you, but they might give you a starting point. I'll post them here, when I get home.

Gord

```

#!/bin/bash

OUTPUT="~/Desktop/TV/`date +%y%m%d-%H%M.avi`"

echo false > /sys/class/pvrusb2/*/ctl_mute/cur_val
echo 58980 > /sys/class/pvrusb2/*/ctl_volume/cur_val
echo television > /sys/class/pvrusb2/*/ctl_input/cur_val
echo 77250000 > /sys/class/pvrusb2/*/ctl_frequency/cur_val

mencoder -ovc lavc    -lavcopts vcodec=mpeg4:vbitrate=1400 \
         -oac mp3lame -lameopts br=96 -vop scale=512:384,pp=lb \
         -endpos 00:29:55 \
         -o $OUTPUT /dev/video

exit 0

```The above script sets the channel on my WinTV PVR (usb2) to channel 5 and records for approximately 30 minutes (29m 55sec). It ensures the recording is not muted and the volume is set to a reasonable level.

I have a series of such scripts with various channels set and length of record times. Now in my crontab I have the following:

```

# Cornation St (Chnnl 5)
1 0 * * 1-5  /usr/bin/at -f ~/bin/30m  18:00

# WWE RAW Recovery (Chnnl 53)
1 0 * * 1    /usr/bin/at -f ~/bin/135m 22:00

# WWE Smackdown (Chnnl 53)
1 0 * * 5    /usr/bin/at -f ~/bin/120m 20:00

# Hockey Night in Canada (Chnnl 5)
1 0 * * 6    /usr/bin/at -f ~/bin/180m 19:00

```Now cron will run "at" at midnight to run at the appropriate time (huh :-) ). I use "at" so if I need to change or cancel the recording, I can issue 'atrm #' and stop the recording and/or issue 'at -f ~/bin/<script name> <new time>".

Hope that made sense!

Gord

hey that might work if you could help me figure out how to modify it! and how to use it, i probably only need to modify a few things in it.

---

