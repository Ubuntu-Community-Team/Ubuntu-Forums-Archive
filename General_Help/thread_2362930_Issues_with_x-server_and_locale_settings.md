---
title: "Issues with x-server and locale settings"
date: 2017-06-03
forum: General Help
---

### Post by cbstryker on 2017-06-03
OS: Budgie Remix 16.10
CPU: Xeon E3-1230 V5
RAM: 32GB
GPU: EVGA NVIDIA 1050 TI

So long story short, my video card died, but it was a long process. It was slowly dying for the past few months, but I took the symptoms as simply driver issues. So over the past few months, I flipped back and forth between the 375, 378, and 381 NVIDIA drivers each time I ran into some issue, like the screen not waking back up or showing strange scaling (4K monitor). Eventually the display would not show anything above 1080 no matter what I tried. Plugged it into another computer and 4K worked no problem.

So I bought a new 1050 TI card, and I'm getting new issues. I can't remember all of the things that I've tried, but somewhere along the way I pooched the locale settings (gnome-terminal won't launch) and the scaling is off with text and graphical elements.

This is what I get if I try to launch gnome-terminal from Xvt (which itself closes on its own after a minute or so)

```
Error constructing proxy for or.gnome.Terminal:/org/gnome/Terminal/Factory0: Error calling StartServiceByName for org.gnome.Terminal: Timeout was reached
```

But if I launch with:
```
dbus-launch gnome-terminal
```
it works just fine.

Usually the following combination with a logout and login will get gnome-terminal working again.
```
sudo locale-gen --purge
sudo localectl set-locale LANG="en_CA.UTF-8"
sudo dpkg-reconfigure locales
```
But I notice at some point around 30 minutes later (after getting into my workflow) that gnome-terminal won't open anymore.

The issue with my scaling and such is likely because before I realized the problem with my monitor was in-fact my video card, I tried to manually add modes to xrandr, and they seem to still be there.

The only oddity I see in dmesg is this:

```
[    4.862834] NVRM: Your system is not currently configured to drive a VGA console
[    4.862835] NVRM: on the primary VGA device. The NVIDIA Linux graphics driver
[    4.862835] NVRM: requires the use of a text-mode VGA console. Use of other console
[    4.862836] NVRM: drivers including, but not limited to, vesafb, may result in
[    4.862836] NVRM: corruption and stability problems, and is not supported.
```

Here's the last 100 or so lines in /var/log/syslog

```
Jun  3 22:12:30 Chris-PC-Linux at-spi-bus-launcher[1660]: Successfully activated service 'org.a11y.atspi.Registry'
Jun  3 22:12:30 Chris-PC-Linux at-spi-bus-launcher[1660]: Activating service name='org.a11y.atspi.Registry'
Jun  3 22:12:30 Chris-PC-Linux [7950]: AT-SPI: Cannot open default display
Jun  3 22:12:30 Chris-PC-Linux org.a11y.atspi.Registry[1674]: SpiRegistry daemon is running with well-known name - org.a11y.atspi.Registry
Jun  3 22:12:30 Chris-PC-Linux budgie-plank.desktop[3487]: #033[93m[WARN 22:12:30.392733]#033[0m AT-SPI: Could not obtain desktop path or name
Jun  3 22:12:30 Chris-PC-Linux at-spi2-registr[7952]: Could not open X display
Jun  3 22:12:30 Chris-PC-Linux at-spi-bus-launcher[1660]: Successfully activated service 'org.a11y.atspi.Registry'
Jun  3 22:12:30 Chris-PC-Linux org.a11y.atspi.Registry[1674]: SpiRegistry daemon is running with well-known name - org.a11y.atspi.Registry
Jun  3 22:12:30 Chris-PC-Linux at-spi2-registr[7952]: AT-SPI: Cannot open default display
Jun  3 22:12:30 Chris-PC-Linux at-spi-bus-launcher[1660]: Activating service name='org.a11y.atspi.Registry'
Jun  3 22:12:30 Chris-PC-Linux at-spi2-registr[7954]: Could not open X display
Jun  3 22:12:30 Chris-PC-Linux at-spi-bus-launcher[1660]: Successfully activated service 'org.a11y.atspi.Registry'
Jun  3 22:12:30 Chris-PC-Linux org.a11y.atspi.Registry[1674]: SpiRegistry daemon is running with well-known name - org.a11y.atspi.Registry
Jun  3 22:12:30 Chris-PC-Linux at-spi2-registr[7954]: AT-SPI: Cannot open default display
Jun  3 22:12:30 Chris-PC-Linux at-spi-bus-launcher[1660]: Activating service name='org.a11y.atspi.Registry'
Jun  3 22:12:30 Chris-PC-Linux at-spi2-registr[7956]: Could not open X display
Jun  3 22:12:30 Chris-PC-Linux at-spi-bus-launcher[1660]: Successfully activated service 'org.a11y.atspi.Registry'
Jun  3 22:12:30 Chris-PC-Linux org.a11y.atspi.Registry[1674]: SpiRegistry daemon is running with well-known name - org.a11y.atspi.Registry
Jun  3 22:12:30 Chris-PC-Linux at-spi2-registr[7956]: AT-SPI: Cannot open default display
Jun  3 22:12:30 Chris-PC-Linux at-spi-bus-launcher[1660]: Activating service name='org.a11y.atspi.Registry'
Jun  3 22:12:30 Chris-PC-Linux at-spi2-registr[7958]: Could not open X display
Jun  3 22:12:30 Chris-PC-Linux at-spi-bus-launcher[1660]: Successfully activated service 'org.a11y.atspi.Registry'
Jun  3 22:12:30 Chris-PC-Linux org.a11y.atspi.Registry[1674]: SpiRegistry daemon is running with well-known name - org.a11y.atspi.Registry
Jun  3 22:12:30 Chris-PC-Linux at-spi2-registr[7958]: AT-SPI: Cannot open default display
Jun  3 22:12:30 Chris-PC-Linux at-spi-bus-launcher[1660]: Activating service name='org.a11y.atspi.Registry'
Jun  3 22:12:30 Chris-PC-Linux at-spi2-registr[7960]: Could not open X display
Jun  3 22:12:30 Chris-PC-Linux at-spi-bus-launcher[1660]: Successfully activated service 'org.a11y.atspi.Registry'
Jun  3 22:12:30 Chris-PC-Linux org.a11y.atspi.Registry[1674]: SpiRegistry daemon is running with well-known name - org.a11y.atspi.Registry
Jun  3 22:12:30 Chris-PC-Linux at-spi2-registr[7960]: AT-SPI: Cannot open default display
Jun  3 22:12:30 Chris-PC-Linux at-spi-bus-launcher[1660]: Activating service name='org.a11y.atspi.Registry'
Jun  3 22:12:30 Chris-PC-Linux shutter.desktop[3489]: WARNING **: AT-SPI: Could not obtain desktop path or name
Jun  3 22:12:30 Chris-PC-Linux at-spi2-registr[7962]: Could not open X display
Jun  3 22:12:30 Chris-PC-Linux at-spi-bus-launcher[1660]: Successfully activated service 'org.a11y.atspi.Registry'
Jun  3 22:12:30 Chris-PC-Linux org.a11y.atspi.Registry[1674]: SpiRegistry daemon is running with well-known name - org.a11y.atspi.Registry
Jun  3 22:12:30 Chris-PC-Linux at-spi2-registr[7962]: AT-SPI: Cannot open default display
Jun  3 22:12:30 Chris-PC-Linux shutter.desktop[3489]: WARNING **: AT-SPI: Could not obtain desktop path or name
Jun  3 22:12:30 Chris-PC-Linux at-spi-bus-launcher[1660]: Activating service name='org.a11y.atspi.Registry'
Jun  3 22:12:30 Chris-PC-Linux shutter.desktop[3489]: WARNING **: AT-SPI: Could not obtain desktop path or name
Jun  3 22:12:30 Chris-PC-Linux shutter.desktop[3489]: message repeated 5 times: [ WARNING **: AT-SPI: Could not obtain desktop path or name]
Jun  3 22:12:30 Chris-PC-Linux at-spi2-registr[7964]: Could not open X display
Jun  3 22:12:30 Chris-PC-Linux at-spi-bus-launcher[1660]: Successfully activated service 'org.a11y.atspi.Registry'
Jun  3 22:12:30 Chris-PC-Linux org.a11y.atspi.Registry[1674]: SpiRegistry daemon is running with well-known name - org.a11y.atspi.Registry
Jun  3 22:12:30 Chris-PC-Linux at-spi2-registr[7964]: AT-SPI: Cannot open default display
Jun  3 22:12:30 Chris-PC-Linux at-spi-bus-launcher[1660]: Activating service name='org.a11y.atspi.Registry'
Jun  3 22:12:30 Chris-PC-Linux at-spi2-registr[7966]: Could not open X display
Jun  3 22:12:30 Chris-PC-Linux at-spi-bus-launcher[1660]: Successfully activated service 'org.a11y.atspi.Registry'
Jun  3 22:12:30 Chris-PC-Linux org.a11y.atspi.Registry[1674]: SpiRegistry daemon is running with well-known name - org.a11y.atspi.Registry
Jun  3 22:12:30 Chris-PC-Linux at-spi2-registr[7966]: AT-SPI: Cannot open default display
Jun  3 22:12:30 Chris-PC-Linux shutter.desktop[3489]: WARNING **: AT-SPI: Could not obtain desktop path or name
Jun  3 22:12:30 Chris-PC-Linux at-spi-bus-launcher[1660]: Activating service name='org.a11y.atspi.Registry'
Jun  3 22:12:30 Chris-PC-Linux at-spi2-registr[7968]: Could not open X display
Jun  3 22:12:30 Chris-PC-Linux at-spi-bus-launcher[1660]: Successfully activated service 'org.a11y.atspi.Registry'
Jun  3 22:12:30 Chris-PC-Linux org.a11y.atspi.Registry[1674]: SpiRegistry daemon is running with well-known name - org.a11y.atspi.Registry
Jun  3 22:12:30 Chris-PC-Linux at-spi2-registr[7968]: AT-SPI: Cannot open default display
Jun  3 22:12:30 Chris-PC-Linux shutter.desktop[3489]: WARNING **: AT-SPI: Could not obtain desktop path or name
Jun  3 22:12:30 Chris-PC-Linux at-spi-bus-launcher[1660]: Activating service name='org.a11y.atspi.Registry'
Jun  3 22:12:30 Chris-PC-Linux at-spi2-registr[7970]: Could not open X display
Jun  3 22:12:30 Chris-PC-Linux at-spi-bus-launcher[1660]: Successfully activated service 'org.a11y.atspi.Registry'
Jun  3 22:12:30 Chris-PC-Linux org.a11y.atspi.Registry[1674]: SpiRegistry daemon is running with well-known name - org.a11y.atspi.Registry
Jun  3 22:12:30 Chris-PC-Linux at-spi2-registr[7970]: AT-SPI: Cannot open default display
Jun  3 22:12:30 Chris-PC-Linux shutter.desktop[3489]: WARNING **: AT-SPI: Could not obtain desktop path or name
Jun  3 22:12:30 Chris-PC-Linux at-spi-bus-launcher[1660]: Activating service name='org.a11y.atspi.Registry'
Jun  3 22:12:30 Chris-PC-Linux at-spi2-registr[7972]: Could not open X display
Jun  3 22:12:30 Chris-PC-Linux at-spi-bus-launcher[1660]: Successfully activated service 'org.a11y.atspi.Registry'
Jun  3 22:12:30 Chris-PC-Linux org.a11y.atspi.Registry[1674]: SpiRegistry daemon is running with well-known name - org.a11y.atspi.Registry
Jun  3 22:12:30 Chris-PC-Linux at-spi2-registr[7972]: AT-SPI: Cannot open default display
Jun  3 22:12:30 Chris-PC-Linux shutter.desktop[3489]: WARNING **: AT-SPI: Could not obtain desktop path or name
Jun  3 22:12:30 Chris-PC-Linux at-spi-bus-launcher[1660]: Activating service name='org.a11y.atspi.Registry'
Jun  3 22:12:30 Chris-PC-Linux at-spi2-registr[7974]: Could not open X display
Jun  3 22:12:30 Chris-PC-Linux at-spi-bus-launcher[1660]: Successfully activated service 'org.a11y.atspi.Registry'
Jun  3 22:12:30 Chris-PC-Linux org.a11y.atspi.Registry[1674]: SpiRegistry daemon is running with well-known name - org.a11y.atspi.Registry
Jun  3 22:12:30 Chris-PC-Linux at-spi2-registr[7974]: AT-SPI: Cannot open default display
Jun  3 22:12:30 Chris-PC-Linux shutter.desktop[3489]: WARNING **: AT-SPI: Could not obtain desktop path or name
Jun  3 22:12:30 Chris-PC-Linux shutter.desktop[3489]: WARNING **: AT-SPI: Could not obtain desktop path or name
Jun  3 22:13:17 Chris-PC-Linux at-spi-bus-launcher[1660]: Activating service name='org.a11y.atspi.Registry'
Jun  3 22:13:17 Chris-PC-Linux at-spi-bus-launcher[1660]: Successfully activated service 'org.a11y.atspi.Registry'
Jun  3 22:13:17 Chris-PC-Linux org.a11y.atspi.Registry[1674]: SpiRegistry daemon is running with well-known name - org.a11y.atspi.Registry
Jun  3 22:13:17 Chris-PC-Linux chromoting: Host started for user: cblasko@gmail.com
Jun  3 22:13:17 Chris-PC-Linux gnome-session[8048]: gnome-session-is-accelerated: llvmpipe detected.
Jun  3 22:13:17 Chris-PC-Linux gnome-session[8048]: gnome-session-binary[8048]: CRITICAL: We failed, but the fail whale is dead. Sorry....
Jun  3 22:13:17 Chris-PC-Linux gnome-session-binary[8048]: CRITICAL: We failed, but the fail whale is dead. Sorry....
Jun  3 22:13:17 Chris-PC-Linux org.a11y.atspi.Registry[1674]: XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":20"
Jun  3 22:13:17 Chris-PC-Linux org.a11y.atspi.Registry[1674]:       after 21 requests (21 known processed) with 0 events remaining.
Jun  3 22:13:43 Chris-PC-Linux anacron[1161]: Job `cron.weekly' started
Jun  3 22:13:43 Chris-PC-Linux anacron[8195]: Updated timestamp for job `cron.weekly' to 2017-06-03
Jun  3 22:13:45 Chris-PC-Linux /usr/lib/snapd/snapd[1172]: store.go:1194: DEBUG: Deltas enabled. Adding header X-Ubuntu-Delta-Formats: xdelta3
Jun  3 22:13:45 Chris-PC-Linux /usr/lib/snapd/snapd[1172]: snapmgr.go:422: No snaps to auto-refresh found
Jun  3 22:13:45 Chris-PC-Linux snapd[1172]: 2017/06/03 22:13:45.750729 snapmgr.go:422: No snaps to auto-refresh found
Jun  3 22:14:29 Chris-PC-Linux anacron[1161]: Job `cron.weekly' terminated (mailing output)
Jun  3 22:14:29 Chris-PC-Linux anacron[1161]: anacron: Can't find sendmail at /usr/sbin/sendmail, not mailing output
Jun  3 22:14:29 Chris-PC-Linux anacron[1161]: Can't find sendmail at /usr/sbin/sendmail, not mailing output
Jun  3 22:14:29 Chris-PC-Linux anacron[1161]: Normal exit (1 job run)
Jun  3 22:15:01 Chris-PC-Linux CRON[8248]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Jun  3 22:16:13 Chris-PC-Linux budgie-wm.desktop[3229]: Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x1600007 (budgie-pan)
Jun  3 22:16:24 Chris-PC-Linux at-spi-bus-launcher[1660]: Activating service name='org.a11y.atspi.Registry'
Jun  3 22:16:24 Chris-PC-Linux at-spi2-registr[8289]: Could not open X display
Jun  3 22:16:24 Chris-PC-Linux at-spi-bus-launcher[1660]: Successfully activated service 'org.a11y.atspi.Registry'
Jun  3 22:16:24 Chris-PC-Linux org.a11y.atspi.Registry[1674]: SpiRegistry daemon is running with well-known name - org.a11y.atspi.Registry
Jun  3 22:16:24 Chris-PC-Linux at-spi2-registr[8289]: AT-SPI: Cannot open default display
Jun  3 22:16:24 Chris-PC-Linux shutter.desktop[3489]: WARNING **: AT-SPI: Could not obtain desktop path or name
Jun  3 22:16:24 Chris-PC-Linux dbus-daemon[1651]: Activating via systemd: service name='org.gnome.Terminal' unit='gnome-terminal-server.service'
Jun  3 22:16:24 Chris-PC-Linux systemd[1376]: Starting GNOME Terminal Server...
Jun  3 22:16:24 Chris-PC-Linux gnome-terminal-server[8292]: Failed to connect to Mir: Failed to connect to server socket: No such file or directory
Jun  3 22:16:24 Chris-PC-Linux gnome-terminal-server[8292]: Unable to init server: Could not connect: Connection refused
Jun  3 22:16:24 Chris-PC-Linux gnome-terminal-server[8292]: Failed to parse arguments: Cannot open display:
Jun  3 22:16:24 Chris-PC-Linux systemd[1376]: gnome-terminal-server.service: Main process exited, code=exited, status=10/n/a
Jun  3 22:16:24 Chris-PC-Linux systemd[1376]: Failed to start GNOME Terminal Server.
Jun  3 22:16:24 Chris-PC-Linux systemd[1376]: gnome-terminal-server.service: Unit entered failed state.
Jun  3 22:16:24 Chris-PC-Linux systemd[1376]: gnome-terminal-server.service: Failed with result 'exit-code'.
Jun  3 22:17:01 Chris-PC-Linux CRON[8309]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jun  3 22:17:30 Chris-PC-Linux org.a11y.Bus[8328]: Activating service name='org.a11y.atspi.Registry'
Jun  3 22:17:30 Chris-PC-Linux at-spi-bus-laun[8332]: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
Jun  3 22:17:30 Chris-PC-Linux org.a11y.Bus[8328]: Successfully activated service 'org.a11y.atspi.Registry'
Jun  3 22:17:30 Chris-PC-Linux org.a11y.atspi.Registry[8337]: SpiRegistry daemon is running with well-known name - org.a11y.atspi.Registry
Jun  3 22:18:24 Chris-PC-Linux dbus-daemon[1651]: Failed to activate service 'org.gnome.Terminal': timed out
Jun  3 22:18:44 Chris-PC-Linux /usr/lib/snapd/snapd[1172]: snapmgr.go:496: DEBUG: Next refresh scheduled for 2017-06-04 00:51:47.196626726 -0400 EDT.
Jun  3 22:18:44 Chris-PC-Linux systemd[1]: Starting Cleanup of Temporary Directories...
Jun  3 22:18:44 Chris-PC-Linux systemd-tmpfiles[8451]: [/usr/lib/tmpfiles.d/var.conf:14] Duplicate line for path "/var/log", ignoring.
Jun  3 22:18:44 Chris-PC-Linux systemd[1]: Started Cleanup of Temporary Directories.
Jun  3 22:24:10 Chris-PC-Linux gnome-terminal-[8354]: Allocating size to GtkBox 0x55d5be81a7b0 without calling gtk_widget_get_preferred_width/height(). How does the code know the size to allocate?
Jun  3 22:24:11 Chris-PC-Linux gnome-terminal-[8354]: message repeated 12 times: [ Allocating size to GtkBox 0x55d5be81a7b0 without calling gtk_widget_get_preferred_width/height(). How does the code know the size to allocate?]
```

I see a lot of these in /var/log/lightdm/lightdm.org

```
[+11.75s] CRITICAL: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
```

I would consider a complete reinstall of the OS and not spend time trying to fix this, but I would rather wait for 17.10 at this point, so my next best option is to fix my current setup.

Edit: oh, a few months back I decided to play around with Gnome Shell. So I installed it, but I ran into an issue where after entering my password at the login it would just kick me back to the login. Removing Xauthority didn't do the trick, only reinstalling the NVIDIA driver (no idea why). Eventually it wouldn't login no matter what. Removing Gnome Shell ultimately did the trick, but part of the process of removing it decided I didn't need lightdm anymore. So I had to manually install it again. So this is where I'm at now.

Edit2: so it seems in my many attempts to find the issue, I also reset my monitors settings (it's actually a 38" Seiki 4K TV) which set the sharpness setting back to default which displays very badly on a desktop. But now my desktop boots into 1080p and not into 4K by default like it used to.

---

