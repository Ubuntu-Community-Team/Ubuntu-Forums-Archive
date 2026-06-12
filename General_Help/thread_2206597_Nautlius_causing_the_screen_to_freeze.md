---
title: "Nautlius causing the screen to freeze"
date: 2014-02-19
forum: General Help
---

### Post by Brandon_MacEachern on 2014-02-19
Whenever I am in Nautilus and doing a lot of file management, I keep getting freezes.  By this I mean, only the mouse cursor moves, all stuff on screen remains completely frozen.  Can't click anything, clock stops, etc.

I can get to TTY2 however, and if I do a sudo restart lightdm, I can log back in, but I loose everything I was doing.

This is extremely important to get fixed.

For logs, this is literally all I can contribute.  That's my entire system log.  Nothing even related to Nautilus.  About the only thing I can say though, the freeze has ALWAYS happened when Nautilus is being used.

```
Feb 19 17:16:46 brandon-MacBookPro anacron[21377]: Job `cron.daily' terminatedFeb 19 17:16:46 brandon-MacBookPro anacron[21377]: Normal exit (1 job run)
Feb 19 17:17:01 brandon-MacBookPro CRON[22407]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Feb 19 17:19:04 brandon-MacBookPro whoopsie[1273]: online
Feb 19 17:20:15  whoopsie[1273]: last message repeated 2 times
Feb 19 17:20:15 brandon-MacBookPro wpa_supplicant[1021]: eth1: WPA: Group rekeying completed with e0:91:f5:a2:f1:40 [GTK=CCMP]
Feb 19 17:32:10 brandon-MacBookPro whoopsie[1273]: online
Feb 19 17:33:11  whoopsie[1273]: last message repeated 2 times
Feb 19 17:36:07 brandon-MacBookPro whoopsie[1273]: online
Feb 19 17:37:28  whoopsie[1273]: last message repeated 2 times
Feb 19 17:57:22 brandon-MacBookPro whoopsie[1273]: online
Feb 19 17:58:23  whoopsie[1273]: last message repeated 2 times
Feb 19 18:09:21 brandon-MacBookPro dbus[817]: [system] Activating service name='org.freedesktop.hostname1' (using servicehelper)
Feb 19 18:09:21 brandon-MacBookPro dbus[817]: [system] Successfully activated service 'org.freedesktop.hostname1'
Feb 19 18:10:16 brandon-MacBookPro whoopsie[1273]: online
Feb 19 18:11:30  whoopsie[1273]: last message repeated 2 times
Feb 19 18:14:58 brandon-MacBookPro whoopsie[1273]: online
Feb 19 18:15:59  whoopsie[1273]: last message repeated 2 times
Feb 19 18:17:01 brandon-MacBookPro CRON[23387]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Feb 19 18:20:15 brandon-MacBookPro wpa_supplicant[1021]: eth1: WPA: Group rekeying completed with e0:91:f5:a2:f1:40 [GTK=CCMP]
Feb 19 18:20:50 brandon-MacBookPro whoopsie[1273]: online
Feb 19 18:22:00  whoopsie[1273]: last message repeated 2 times
Feb 19 18:27:19 brandon-MacBookPro dbus[817]: [system] Activating service name='org.freedesktop.hostname1' (using servicehelper)
Feb 19 18:27:19 brandon-MacBookPro dbus[817]: [system] Successfully activated service 'org.freedesktop.hostname1'
Feb 19 18:32:10 brandon-MacBookPro whoopsie[1273]: online
Feb 19 18:33:11  whoopsie[1273]: last message repeated 2 times
Feb 19 18:40:13 brandon-MacBookPro whoopsie[1273]: online
Feb 19 18:41:43 brandon-MacBookPro whoopsie[1273]: online
Feb 19 18:41:44 brandon-MacBookPro whoopsie[1273]: online
Feb 19 18:42:51 brandon-MacBookPro dbus[817]: [system] Activating service name='org.freedesktop.hostname1' (using servicehelper)
Feb 19 18:42:51 brandon-MacBookPro dbus[817]: [system] Successfully activated service 'org.freedesktop.hostname1'
Feb 19 18:51:07 brandon-MacBookPro dbus[817]: [system] Activating service name='org.freedesktop.hostname1' (using servicehelper)
Feb 19 18:51:07 brandon-MacBookPro dbus[817]: [system] Successfully activated service 'org.freedesktop.hostname1'
Feb 19 18:51:20 brandon-MacBookPro whoopsie[1273]: online
Feb 19 18:53:19 brandon-MacBookPro whoopsie[1273]: online
Feb 19 18:54:32  whoopsie[1273]: last message repeated 4 times
Feb 19 18:55:11 brandon-MacBookPro acpid: client 23831[0:0] has disconnected
Feb 19 18:55:11 brandon-MacBookPro acpid: client connected from 23831[0:0]
Feb 19 18:55:11 brandon-MacBookPro acpid: 1 client rule loaded
Feb 19 18:55:35 brandon-MacBookPro whoopsie[1273]: online
Feb 19 18:57:02  whoopsie[1273]: last message repeated 2 times
Feb 19 18:58:53 brandon-MacBookPro whoopsie[1273]: online
Feb 19 18:59:39  whoopsie[1273]: last message repeated 2 times
Feb 19 18:59:39 brandon-MacBookPro colord: device removed: xrandr-Apple Computer Inc-Color LCD
Feb 19 18:59:39 brandon-MacBookPro colord: Profile removed: icc-1f7b8fd240963696441a2471dd1f51bd
Feb 19 18:59:39 brandon-MacBookPro colord: Profile removed: icc-e0c9c08be3713e2a2fd29be48ee55ba1
Feb 19 18:59:39 brandon-MacBookPro gnome-session[24248]: Gdk-WARNING: gnome-session: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.#012
Feb 19 18:59:44 brandon-MacBookPro bluetoothd[900]: Endpoint unregistered: sender=:1.57 path=/MediaEndpoint/HFPAG
Feb 19 18:59:44 brandon-MacBookPro bluetoothd[900]: Endpoint unregistered: sender=:1.57 path=/MediaEndpoint/HFPHS
Feb 19 18:59:44 brandon-MacBookPro bluetoothd[900]: Endpoint unregistered: sender=:1.57 path=/MediaEndpoint/A2DPSource
Feb 19 18:59:44 brandon-MacBookPro bluetoothd[900]: Endpoint unregistered: sender=:1.57 path=/MediaEndpoint/A2DPSink
Feb 19 18:59:46 brandon-MacBookPro pulseaudio[25816]: [pulseaudio] client-conf-x11.c: xcb_connection_has_error() returned true
Feb 19 18:59:46 brandon-MacBookPro pulseaudio[25819]: [pulseaudio] pid.c: Stale PID file, overwriting.
Feb 19 18:59:47 brandon-MacBookPro acpid: client 23831[0:0] has disconnected
Feb 19 18:59:47 brandon-MacBookPro acpid: client connected from 25814[0:0]
Feb 19 18:59:47 brandon-MacBookPro acpid: 1 client rule loaded
Feb 19 18:59:48 brandon-MacBookPro pulseaudio[25819]: [pulseaudio] module-alsa-card.c: Failed to find a working profile.
Feb 19 18:59:48 brandon-MacBookPro pulseaudio[25819]: [pulseaudio] module.c: Failed to load module "module-alsa-card" (argument: "device_id="1" name="pci-0000_01_00.1" card_name="alsa_card.pci-0000_01_00.1" namereg_fail=false tsched=yes fixed_latency_range=no ignore_dB=no deferred_volume=yes use_ucm=yes card_properties="module-udev-detect.discovered=1""): initialization failed.
Feb 19 18:59:48 brandon-MacBookPro pulseaudio[25819]: [pulseaudio] server-lookup.c: Unable to contact D-Bus: org.freedesktop.DBus.Error.NoServer: Failed to connect to socket /tmp/dbus-20r0X95oOb: Connection refused
Feb 19 18:59:48 brandon-MacBookPro pulseaudio[25819]: [pulseaudio] main.c: Unable to contact D-Bus: org.freedesktop.DBus.Error.NoServer: Failed to connect to socket /tmp/dbus-20r0X95oOb: Connection refused
Feb 19 18:59:48 brandon-MacBookPro bluetoothd[900]: Endpoint registered: sender=:1.1365 path=/MediaEndpoint/HFPAG
Feb 19 18:59:48 brandon-MacBookPro bluetoothd[900]: Endpoint registered: sender=:1.1365 path=/MediaEndpoint/HFPHS
Feb 19 18:59:48 brandon-MacBookPro bluetoothd[900]: Endpoint registered: sender=:1.1365 path=/MediaEndpoint/A2DPSource
Feb 19 18:59:48 brandon-MacBookPro bluetoothd[900]: Endpoint registered: sender=:1.1365 path=/MediaEndpoint/A2DPSink
Feb 19 18:59:51 brandon-MacBookPro dbus[817]: [system] Activating service name='org.freedesktop.systemd1' (using servicehelper)
Feb 19 18:59:51 brandon-MacBookPro dbus[817]: [system] Successfully activated service 'org.freedesktop.systemd1'
Feb 19 18:59:52 brandon-MacBookPro rtkit-daemon[1631]: Successfully made thread 25958 of process 25958 (n/a) owned by '111' high priority at nice level -11.
Feb 19 18:59:52 brandon-MacBookPro rtkit-daemon[1631]: Supervising 1 threads of 1 processes of 2 users.
Feb 19 18:59:52 brandon-MacBookPro colord: Device added: xrandr-Apple Computer Inc-Color LCD
Feb 19 18:59:52 brandon-MacBookPro colord: Automatic metadata add icc-9dc698972a72ad1fbd8f5b0822d6b601 to xrandr-Apple Computer Inc-Color LCD
Feb 19 18:59:52 brandon-MacBookPro colord: Profile added: icc-9dc698972a72ad1fbd8f5b0822d6b601
Feb 19 18:59:52 brandon-MacBookPro rtkit-daemon[1631]: Successfully made thread 25990 of process 25958 (n/a) owned by '111' RT at priority 5.
Feb 19 18:59:52 brandon-MacBookPro rtkit-daemon[1631]: Supervising 2 threads of 1 processes of 2 users.
Feb 19 18:59:54 brandon-MacBookPro rtkit-daemon[1631]: Successfully made thread 26011 of process 25958 (n/a) owned by '111' RT at priority 5.
Feb 19 18:59:54 brandon-MacBookPro rtkit-daemon[1631]: Supervising 3 threads of 1 processes of 2 users.
Feb 19 18:59:55 brandon-MacBookPro rtkit-daemon[1631]: Successfully made thread 26013 of process 25958 (n/a) owned by '111' RT at priority 5.
Feb 19 18:59:55 brandon-MacBookPro rtkit-daemon[1631]: Supervising 4 threads of 1 processes of 2 users.
Feb 19 18:59:55 brandon-MacBookPro bluetoothd[900]: Endpoint registered: sender=:1.1384 path=/MediaEndpoint/HFPAG
Feb 19 18:59:55 brandon-MacBookPro bluetoothd[900]: Endpoint registered: sender=:1.1384 path=/MediaEndpoint/HFPHS
Feb 19 18:59:55 brandon-MacBookPro bluetoothd[900]: Endpoint registered: sender=:1.1384 path=/MediaEndpoint/A2DPSource
Feb 19 18:59:55 brandon-MacBookPro bluetoothd[900]: Endpoint registered: sender=:1.1384 path=/MediaEndpoint/A2DPSink
Feb 19 18:59:55 brandon-MacBookPro rtkit-daemon[1631]: Successfully made thread 26016 of process 26016 (n/a) owned by '111' high priority at nice level -11.
Feb 19 18:59:55 brandon-MacBookPro rtkit-daemon[1631]: Supervising 5 threads of 2 processes of 2 users.
Feb 19 18:59:55 brandon-MacBookPro pulseaudio[26016]: [pulseaudio] pid.c: Daemon already running.
Feb 19 19:00:01 brandon-MacBookPro acpid: client 25814[0:0] has disconnected
Feb 19 19:00:01 brandon-MacBookPro acpid: client connected from 25814[0:0]
Feb 19 19:00:01 brandon-MacBookPro acpid: 1 client rule loaded
Feb 19 19:00:09 brandon-MacBookPro acpid: client 25814[0:0] has disconnected
Feb 19 19:00:09 brandon-MacBookPro acpid: client connected from 25814[0:0]
Feb 19 19:00:09 brandon-MacBookPro acpid: 1 client rule loaded
Feb 19 19:00:12 brandon-MacBookPro colord: device removed: xrandr-Apple Computer Inc-Color LCD
Feb 19 19:00:12 brandon-MacBookPro colord: Profile removed: icc-9dc698972a72ad1fbd8f5b0822d6b601
Feb 19 19:00:12 brandon-MacBookPro NetworkManager[961]: <warn> error requesting auth for org.freedesktop.NetworkManager.wifi.share.protected: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.1378': no such name
Feb 19 19:00:12 brandon-MacBookPro NetworkManager[961]: <warn> error requesting auth for org.freedesktop.NetworkManager.wifi.share.open: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.1378': no such name
Feb 19 19:00:14 brandon-MacBookPro dbus[817]: [system] Activating service name='org.freedesktop.systemd1' (using servicehelper)
Feb 19 19:00:14 brandon-MacBookPro dbus[817]: [system] Successfully activated service 'org.freedesktop.systemd1'
Feb 19 19:00:14 brandon-MacBookPro dbus[817]: [system] Activating service name='org.freedesktop.locale1' (using servicehelper)
Feb 19 19:00:14 brandon-MacBookPro colord: Device added: xrandr-Apple Computer Inc-Color LCD
Feb 19 19:00:14 brandon-MacBookPro colord: Automatic database add icc-1f7b8fd240963696441a2471dd1f51bd to xrandr-Apple Computer Inc-Color LCD
Feb 19 19:00:14 brandon-MacBookPro colord: Profile added: icc-1f7b8fd240963696441a2471dd1f51bd
Feb 19 19:00:14 brandon-MacBookPro colord: Automatic database add icc-e0c9c08be3713e2a2fd29be48ee55ba1 to xrandr-Apple Computer Inc-Color LCD
Feb 19 19:00:14 brandon-MacBookPro colord: Automatic metadata add icc-e0c9c08be3713e2a2fd29be48ee55ba1 to xrandr-Apple Computer Inc-Color LCD
Feb 19 19:00:14 brandon-MacBookPro colord: Profile added: icc-e0c9c08be3713e2a2fd29be48ee55ba1
Feb 19 19:00:14 brandon-MacBookPro dbus[817]: [system] Successfully activated service 'org.freedesktop.locale1'
Feb 19 19:00:32 brandon-MacBookPro bluetoothd[900]: Endpoint unregistered: sender=:1.1384 path=/MediaEndpoint/HFPAG
Feb 19 19:00:32 brandon-MacBookPro bluetoothd[900]: Endpoint unregistered: sender=:1.1384 path=/MediaEndpoint/HFPHS
Feb 19 19:00:32 brandon-MacBookPro bluetoothd[900]: Endpoint unregistered: sender=:1.1384 path=/MediaEndpoint/A2DPSource
Feb 19 19:00:32 brandon-MacBookPro bluetoothd[900]: Endpoint unregistered: sender=:1.1384 path=/MediaEndpoint/A2DPSink
Feb 19 19:04:16 brandon-MacBookPro whoopsie[1273]: online
Feb 19 19:05:17  whoopsie[1273]: last message repeated 2 times

```

---

### Post by Brandon_MacEachern on 2014-02-19
Almost seems related to this.

[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1184451](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1184451)

---

### Post by deadflowr on 2014-02-19
Define "Lots of file management", please?

I find if I'm moving around a lot of files, the system can freeze momentarily, sometimes.
Depending on the file sizes and where they are moving from.

If you click on the close button, rapidly, does a force quit window open?

---

### Post by Brandon_MacEachern on 2014-02-19
> **deadflowr said:**
> Define "Lots of file management", please?

I find if I'm moving around a lot of files, the system can freeze momentarily, sometimes.
Depending on the file sizes and where they are moving from.

If you click on the close button, rapidly, does a force quit window open?
Lots of file management, like organizing folders of documents, images, etc.  Not large actually, just moving things around or copying.  We are talking folders of about 50MB.

No, nothing comes up whatsoever.  It's just completely frozen.  It almost sounds like the computer is actually still running because pressing the volume buttons causes the "pop" sound, but nothing on the screen shows up to represent it.

Still, TTY2, "sudo restart lightdm", always resolves the issue, albeit loosing unsaved stuff.

Also, last time it froze, I thought perhaps it was just "thinking", so I left it.  Hour later, clock is 1 hour behind, and still frozen.

---

### Post by Bucky Ball on 2014-02-19
You could try another file manager and see if you can pin this down to Nautilus. PCmanFM is very light and in the repositories. Perhaps try that and see if problem persists. If not, it's Nautilus. If so, it's not and dig elsewhere. :-k

Also, when the system freezes, can you hit the hot keys and open a terminal? Terminal usually still opens in all but the most dire circumstances. If you can open one, issue this:

dmesg

At the bottom will be the problem that is causing this. You could also try that command after a crash and coming back with restarting lightdm, but it may have lost the dmesg info from the crash by the restart.

---

### Post by Brandon_MacEachern on 2014-02-20
When frozen, nothing works.  Actually, going to TTY2, while it gives me the terminal, going back to the X manager TTY screen, it causes the last text mode TTY image to be stuck, with a mouse cursor over it.

Like the frame buffer is no longer working.

I will try another file manager and see what happens.

---

### Post by Brandon_MacEachern on 2014-02-22
So far using another file manager, no crash whatsoever.

---

### Post by Bucky Ball on 2014-02-23
I know this may be a bit troublesome, but perhaps you could look [HERE]("https://help.ubuntu.com/community/ReportingBugs"). It's looking a bit buggish and you might be able to help by having a look around.

Not sure you've mentioned the release or flavour you're using, but if you do file a bug report, stick all that in there. ;)

---

### Post by Brandon_MacEachern on 2014-02-24
I plan to post here actually.

[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1184451](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1184451)

Seems to be the same bug.

I am just using Ubuntu 13.10, regular 64-bit.  Nothing special.

---

### Post by mc4man on 2014-02-24
> **Brandon_MacEachern said:**
> I plan to post here actually.

[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1184451](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1184451)

Seems to be the same bug.

I am just using Ubuntu 13.10, regular 64-bit.  Nothing special.
That report is basically dead, the suggestion would be to file a new, your  hardware specific,  bug on xorg-xserver
(though the suggestion after doing that would be to try 14.04 dev & see if it's still an issue

---

### Post by Brandon_MacEachern on 2014-02-25
Like the other person, running an alpha OS is out of the question.

Why exactly is the reason it's dead?  Because no one bothered to work on it?

---

### Post by deadflowr on 2014-02-25
> **Brandon_MacEachern said:**
> Like the other person, running an alpha OS is out of the question.

Why exactly is the reason it's dead?  Because no one bothered to work on it?


No, because the bug report is too all over the place.
First the OP, bug reporter left it incomplete, originally filing it against Ubuntu in general.
Then the follow-up posters have cluttered it up even more, it's hard to tell what the problem is anymore.

If you do file a new report, use the title of this thread.
Bug reports work best when you are as specific about the problem as possible.
Your problem was that nautilus kept freezing, use that.

Off hand, though, is anything else freezing?

---

### Post by Brandon_MacEachern on 2014-02-25
Nothing else is freezing X Server, no.  Only Nautilus is taking down X Server causing the computer inoperable until "sudo restart lightdm".  Other file managers work fine too.

To be honest, when I first started running into this freeze, I didn't know what was causing it, I thought it was Ubuntu freezing, until I realized that every time the freeze happened, Nautilus was right up in front.

---

