---
title: "pulseaudio appears to be failing after login - 18.04.4"
date: 2020-06-19
forum: General Help
---

### Post by Pow_2k on 2020-06-19
Can't recall anything specific to the timing of when this started.  Laptop is an HP dm4 which has been running Ubuntu without issue for some time now.  Only dealing with the internal audio to the built-in speakers.  Here is what I'm experiencing...

* Boot from power off.  At login screen the speaker icon exists in the top right of the screen.  I can click on it and if adjusting the level I get the confirmation tone.
* Login, speaker icon no longer present at top right.
Wait for a bit...
* "System problem detected" window appears.  No indication what this relates to but I'm willing to bet it is pulseaudio having an issue.
* Open sound settings, no output device listed.  Not even the "dummy device" I've seen mentioned in some of my research.
* Open a terminal, enter "pulseaudio --check".  No exit code returned.
* In terminal, enter "pulseaudio -D".  The output device now shows in sound settings and works.  (with exception, see below)

So it seems to me that pulseaudio is likely crashing after login.  I'm at a loss to explain why.  In the troubleshooting that led up to me discovering that "pulseaudio -D" seems to be my temporary fix, I had gone through steps of reinstalling both pulseaudio and alsa-base, forcing reload of alsa, deleting the .config/pulseaudio directory.  Hoping for some tips to confirm that the "system problem detected" is pulseaudio crashing, and anything else that could help me progress to solving this.

The "exception" that I mentioned is that even after getting output working the audio test available in the sound settings does not work.  I can see the clicks for the left or right channel buttons register, but no audio is heard.  Mentioning this separately as I don't feel it is necessarily tied to the problem of pulseaudio needing to be restarted.

---

### Post by dino99 on 2020-06-20
Do you get something useful from 'journalctl -b | grep puls' ?

---

### Post by CatKiller on 2020-06-20
Crash reports are put in /var/crash.

---

### Post by Pow_2k on 2020-06-29
> **dino99 said:**
> Do you get something useful from 'journalctl -b | grep puls' ?
Thanks for pointing me in that direction.  I get... a lot.  "Useful" maybe, but not immediately to me.
```
craig@HP-dm4:~$ journalctl -b | grep puls
Jun 29 21:15:07 HP-dm4 systemd[1]: Mounting Mount unit for pulseaudio, revision 9...
Jun 29 21:15:07 HP-dm4 systemd[1]: Mounted Mount unit for pulseaudio, revision 9.
Jun 29 21:15:08 HP-dm4 audit[777]: AVC apparmor="STATUS" operation="profile_load" profile="unconfined" name="snap.pulseaudio.config" pid=777 comm="apparmor_parser"
Jun 29 21:15:08 HP-dm4 audit[778]: AVC apparmor="STATUS" operation="profile_load" profile="unconfined" name="snap.pulseaudio.pactl" pid=778 comm="apparmor_parser"
Jun 29 21:15:08 HP-dm4 audit[780]: AVC apparmor="STATUS" operation="profile_load" profile="unconfined" name="snap.pulseaudio.parec" pid=780 comm="apparmor_parser"
Jun 29 21:15:08 HP-dm4 audit[779]: AVC apparmor="STATUS" operation="profile_load" profile="unconfined" name="snap.pulseaudio.paplay" pid=779 comm="apparmor_parser"
Jun 29 21:15:08 HP-dm4 audit[781]: AVC apparmor="STATUS" operation="profile_load" profile="unconfined" name="snap.pulseaudio.pulseaudio" pid=781 comm="apparmor_parser"
Jun 29 21:15:08 HP-dm4 audit[791]: AVC apparmor="STATUS" operation="profile_load" profile="unconfined" name="snap-update-ns.pulseaudio" pid=791 comm="apparmor_parser"
Jun 29 21:15:09 HP-dm4 systemd[1]: Started Service for snap application pulseaudio.pulseaudio.
Jun 29 21:15:10 HP-dm4 pulseaudio.pulseaudio[989]: + export LD_LIBRARY_PATH=/var/lib/snapd/lib/gl:/var/lib/snapd/lib/gl32:/var/lib/snapd/void:/snap/pulseaudio/9/usr/lib:/snap/pulseaudio/9/usr/lib/x86_64-linux-gnu::/snap/pulseaudio/9/lib:/snap/pulseaudio/9/usr/lib:/snap/pulseaudio/9/usr/lib/x86_64-linux-gnu:/snap/pulseaudio/9/usr/lib/pulseaudio:/snap/pulseaudio/9/usr/lib/pulse-8.0/modules/
Jun 29 21:15:10 HP-dm4 pulseaudio.pulseaudio[989]: + export PULSE_STATE_PATH=/var/snap/pulseaudio/9/state
Jun 29 21:15:10 HP-dm4 pulseaudio.pulseaudio[989]: + export ALSA_CONFIG_UCM=/snap/pulseaudio/9/usr/share/alsa/ucm
Jun 29 21:15:10 HP-dm4 pulseaudio.pulseaudio[989]: + export ALSA_CONFIG_TPLG=/snap/pulseaudio/9/usr/share/alsa/topology
Jun 29 21:15:10 HP-dm4 pulseaudio.pulseaudio[989]: + export ALSA_CONFIG_PATH=/snap/pulseaudio/9/usr/share/alsa/alsa.conf
Jun 29 21:15:10 HP-dm4 pulseaudio.pulseaudio[989]: + export ALSA_MIXER_SIMPLE=/snap/pulseaudio/9/usr/share/alsa/smixer.conf
Jun 29 21:15:10 HP-dm4 pulseaudio.pulseaudio[989]: + mkdir -p /var/snap/pulseaudio/9/state
Jun 29 21:15:10 HP-dm4 pulseaudio.pulseaudio[989]: + EXTRA_ARGS=
Jun 29 21:15:10 HP-dm4 pulseaudio.pulseaudio[989]: + [ -e /var/snap/pulseaudio/9/config/debug ]
Jun 29 21:15:10 HP-dm4 pulseaudio.pulseaudio[989]: + /snap/pulseaudio/9/usr/bin/pulseaudio --exit-idle-time=-1 --disallow-exit=yes --system -F /snap/pulseaudio/9/etc/pulse/default.pa -p /snap/pulseaudio/9/usr/lib/pulse-8.0/modules -n
Jun 29 21:15:11 HP-dm4 audit[1180]: AVC apparmor="DENIED" operation="open" profile="snap.pulseaudio.pulseaudio" name="/etc/pulse/daemon.conf" pid=1180 comm="pulseaudio" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
Jun 29 21:15:11 HP-dm4 pulseaudio.pulseaudio[989]: W: [pulseaudio] main.c: Running in system mode, but --disallow-module-loading not set.
Jun 29 21:15:11 HP-dm4 pulseaudio.pulseaudio[989]: N: [pulseaudio] main.c: Running in system mode, forcibly disabling SHM mode.
Jun 29 21:15:11 HP-dm4 kernel: audit: type=1400 audit(1593479711.213:61): apparmor="DENIED" operation="open" profile="snap.pulseaudio.pulseaudio" name="/etc/pulse/daemon.conf" pid=1180 comm="pulseaudio" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
Jun 29 21:15:11 HP-dm4 pulseaudio.pulseaudio[989]: W: [pulseaudio] main.c: Home directory of user 'root' is not '/var/run/pulse', ignoring.
Jun 29 21:15:11 HP-dm4 pulseaudio.pulseaudio[989]: W: [pulseaudio] caps.c: Normally all extra capabilities would be dropped now, but that's impossible because PulseAudio was built without capabilities support.
Jun 29 21:15:11 HP-dm4 audit[1180]: AVC apparmor="DENIED" operation="open" profile="snap.pulseaudio.pulseaudio" name="/sys/devices/virtual/dmi/id/board_vendor" pid=1180 comm="pulseaudio" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
Jun 29 21:15:11 HP-dm4 pulseaudio.pulseaudio[989]: W: [pulseaudio] main.c: OK, so you are running PA in system mode. Please note that you most likely shouldn't be doing that.
Jun 29 21:15:11 HP-dm4 pulseaudio.pulseaudio[989]: W: [pulseaudio] main.c: If you do it nonetheless then it's your own fault if things don't work as expected.
Jun 29 21:15:11 HP-dm4 pulseaudio.pulseaudio[989]: W: [pulseaudio] main.c: Please read http://www.freedesktop.org/wiki/Software/PulseAudio/Documentation/User/WhatIsWrongWithSystemWide/ for an explanation why system mode is usually a bad idea.
Jun 29 21:15:11 HP-dm4 kernel: audit: type=1400 audit(1593479711.237:62): apparmor="DENIED" operation="open" profile="snap.pulseaudio.pulseaudio" name="/sys/devices/virtual/dmi/id/board_vendor" pid=1180 comm="pulseaudio" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
Jun 29 21:15:11 HP-dm4 audit[1180]: AVC apparmor="DENIED" operation="open" profile="snap.pulseaudio.pulseaudio" name="/sys/devices/virtual/dmi/id/board_vendor" pid=1180 comm="pulseaudio" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
Jun 29 21:15:11 HP-dm4 kernel: audit: type=1400 audit(1593479711.525:63): apparmor="DENIED" operation="open" profile="snap.pulseaudio.pulseaudio" name="/sys/devices/virtual/dmi/id/board_vendor" pid=1180 comm="pulseaudio" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
Jun 29 21:15:11 HP-dm4 audit[1180]: AVC apparmor="DENIED" operation="open" profile="snap.pulseaudio.pulseaudio" name="/sys/devices/virtual/dmi/id/board_vendor" pid=1180 comm="pulseaudio" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
Jun 29 21:15:11 HP-dm4 kernel: audit: type=1400 audit(1593479711.581:64): apparmor="DENIED" operation="open" profile="snap.pulseaudio.pulseaudio" name="/sys/devices/virtual/dmi/id/board_vendor" pid=1180 comm="pulseaudio" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
Jun 29 21:15:11 HP-dm4 pulseaudio.pulseaudio[989]: W: [pulseaudio] authkey.c: Failed to open cookie file '/var/run/pulse/.config/pulse/cookie': No such file or directory
Jun 29 21:15:11 HP-dm4 pulseaudio.pulseaudio[989]: W: [pulseaudio] authkey.c: Failed to load authentication key '/var/run/pulse/.config/pulse/cookie': No such file or directory
Jun 29 21:15:11 HP-dm4 pulseaudio.pulseaudio[989]: W: [pulseaudio] authkey.c: Failed to open cookie file '/var/run/pulse/.pulse-cookie': No such file or directory
Jun 29 21:15:11 HP-dm4 pulseaudio.pulseaudio[989]: W: [pulseaudio] authkey.c: Failed to load authentication key '/var/run/pulse/.pulse-cookie': No such file or directory
Jun 29 21:15:13 HP-dm4 dbus-daemon[878]: [system] Activating via systemd: service name='org.freedesktop.RealtimeKit1' unit='rtkit-daemon.service' requested by ':1.35' (uid=121 pid=1260 comm="/usr/bin/pulseaudio --daemonize=no " label="unconfined")
Jun 29 21:15:32 HP-dm4 pulseaudio.pulseaudio[989]: W: [pulseaudio] protocol-native.c: Denied access to client with invalid authentication data.
Jun 29 21:15:32 HP-dm4 pulseaudio.desktop[2138]: Connection failure: Access denied
Jun 29 21:15:32 HP-dm4 gnome-session[1879]: gnome-session-binary[1879]: WARNING: App 'pulseaudio.desktop' exited with code 1
Jun 29 21:15:32 HP-dm4 gnome-session-binary[1879]: WARNING: App 'pulseaudio.desktop' exited with code 1
Jun 29 21:15:33 HP-dm4 pulseaudio.pulseaudio[989]: W: [pulseaudio] protocol-native.c: Denied access to client with invalid authentication data.

```
This last line repeats quite a few times.  I'm suspecting that the "AVC apparmor="DENIED" " and problems that reference "/var/run/pulse/.config/pulse/*cookie" might be relevant, and ultimately the exit at 21:15:32 is where it crashed.  I'll test my google-fu with these messages and see what I can turn up, but if anyone wants to jump in with a head start it would be appreciated.

> **CatKiller said:**
> Crash reports are put in /var/crash.
Thanks for the info!  I guess what I'm getting isn't that type of "crash" as the directory is empty.

---

### Post by Pow_2k on 2020-06-29
So the trick seems to have been the following:
```
sudo adduser [user] pulse-access
```
Where user was my user ID.  journalctl still shows some of the "errors" from last time, such as the "AVC apparmor="DENIED" " and pulseaudio.desktop exiting with code 1, but no more of the cookie messages.  And no more problem/crash window pop-up.

So while this is great, I still don't understand *why* this happened.  Any thoughts?  I'd assume it was something in one of the updates that got pulled down but if so I would have expected to find a lot more hits when I was searching on the issue.  Also, as I understand it the adduser command added me to the group pulse-access, but I can't seem to find that group.  Shouldn't that show up if I just start the "groups" command and then prompt for group names in the shell via the tab key?  I'm missing something here.

Thanks guys for the replies that helped to teach me something more and got me to the fix.

---

### Post by haytham-med on 2020-06-30
Is pulseaudio installed via snap?

---

### Post by Pow_2k on 2020-07-06
> **haytham-med said:**
> Is pulseaudio installed via snap?
No, it is installed via apt.

---

