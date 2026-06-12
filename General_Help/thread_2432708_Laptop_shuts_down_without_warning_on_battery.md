---
title: "Laptop shuts down without warning on battery"
date: 2019-12-07
forum: General Help
---

### Post by odee2 on 2019-12-07
Hi everybody,
I have problem with my laptop Dell inspiron 7720. When is on battery, after a while shuts down without warning.
I already bought new battery, but laptop shuts down after a while with new battery as well. It occurs I think randomly.
I can watch youtube on fulscreen, or composing new email, it shuts down.
I tried to take off the battery an used only adapter, notebook worked fine without shutting down for 8 days.
When shuts down, i can turn it on again, but when is xubuntu started shuts down inmediately.

So this is my test. I plugged out adapter an used laptop on battery
```
TIME 14:47
andrej@andrej-inspiron-7720:~$ acpitool -B
  Battery #1     : present
    Remaining capacity : unknown, 99.75%, 00:00:00
    Design capacity    : 6600 mA
    Last full capacity : 6095 mA, 92.35% of design capacity
    Capacity loss      : 7.652%
    Present rate       : 1766 mA
    Charging state     : Discharging
    Battery type       : Li-ion 
    Model number       : Dell
```[COLOR=#000000]
After shutting down xubuntu without  warning, I plugged back my adapter and turned on laptop:
[/COLOR]```
TIME 15:49
andrej@andrej-inspiron-7720:~$ acpitool -B
  Battery #1     : present
    Remaining capacity : unknown, 55.67%, 01:21:55
    Design capacity    : 6600 mA
    Last full capacity : 6095 mA, 92.35% of design capacity
    Capacity loss      : 7.652%
    Present rate       : 1979 mA
    Charging state     : Charging
    Battery type       : Li-ion 
    Model number       : Dell
```
That was only for checking battery capacity when laptop suddenly turns off.
I have dualboot with windows, so after a unlpugged my laptop from charger (i had it only two minutes plugged in),
I went to windows and I ran it till battery was in windows at 7%. I pulled back the charger and restarted to xubuntu.
```
TIME 17:05
andrej@andrej-inspiron-7720:~$ acpitool -B
  Battery #1     : present
    Remaining capacity : unknown, 6.00%, 02:53:15
    Design capacity    : 6600 mA
    Last full capacity : 6095 mA, 92.3% of design capacity
    Capacity loss      : 7.65%
    Present rate       : 1984 mA
    Charging state     : Charging
    Battery type       : Li-ion 
    Model number       : Dell
```

there is also xfce power manager,  critical power level 10%, I tried already a DO NOTHING on critical battery but Dell keep shutting down.

Can somebody help me please?
[COLOR=#000000]
[/COLOR]

---

### Post by mörgæs on 2019-12-08
Could you try creating a new user, reboot and see if there is any difference using him?

---

### Post by odee2 on 2019-12-08
I tried just now, same fast shutdown like a cut cord power line off at a desktop pc :) even with new user on my laptop dies. Now my battery was at 69%.

---

### Post by Holger_Gehrke on 2019-12-08
I'd check the logs (/var/log/syslog) and  the journal ('journalctl -b -1|tail -n 100|less' gets the last 100 messages from the previous (that's the '-1') boot). This should give you an idea whether it's a controlled emergency shutdown because power management 'thinks' power is low or if the battery actually stopped delivering current and the system shut down uncontrolled.

Holger

---

### Post by Autodave on 2019-12-08
This may or may not help, but it will cost you nothing and only take a little of your time.  Whenever I get a laptop that is doing something stupid, or one that all of a sudden something quit working on it, this is the very first thing that I do:

1. Shut it down normally.
2. Disconnect EVERY cable from it.  EVERY cable especially power.
3. Remove battery.
4. Wait 10 minutes.
5. Reinstall battery and then power cable.  Power up and see what happens.

I probably fix at least 50% of laptops doing this.

---

### Post by odee2 on 2019-12-11
(var/log/syslog)
```

Dec 11 08:01:05 andrej-inspiron-7720 kernel: [15377.715507] atkbd serio0: Unknown key pressed (translated set 2, code 0x8e on isa0060/serio0).
Dec 11 08:01:05 andrej-inspiron-7720 kernel: [15377.715513] atkbd serio0: Use 'setkeycodes e00e <keycode>' to make it known.
Dec 11 07:54:54 andrej-inspiron-7720 udisksd[971]: Error performing housekeeping for drive /org/freedesktop/UDisks2/drives/KINGSTON_SUV400S37480G_50026B776607E79A: Error updating SMART data: sk_disk_smart_read_data: Input/output error (udisks-error-quark, 0)
Dec 11 08:04:31 andrej-inspiron-7720 systemd[1]: Started Run anacron jobs.
Dec 11 08:04:31 andrej-inspiron-7720 anacron[18088]: Anacron 2.3 started on 2019-12-11
Dec 11 08:04:31 andrej-inspiron-7720 anacron[18088]: Normal exit (0 jobs run)
Dec 11 08:04:54 andrej-inspiron-7720 udisksd[971]: Error performing housekeeping for drive /org/freedesktop/UDisks2/drives/KINGSTON_SUV400S37480G_50026B776607E79A: Error updating SMART data: sk_disk_smart_read_data: Input/output error (udisks-error-quark, 0)
Dec 11 08:09:00 andrej-inspiron-7720 systemd[1]: Starting Clean php session files...
Dec 11 08:09:00 andrej-inspiron-7720 systemd[1]: Started Clean php session files.
Dec 11 08:09:01 andrej-inspiron-7720 CRON[18160]: (root) CMD (  [ -x /usr/lib/php/sessionclean ] && if [ ! -d /run/systemd/system ]; then /usr/lib/php/sessionclean; fi)
Dec 11 08:14:54 andrej-inspiron-7720 udisksd[971]: Error performing housekeeping for drive /org/freedesktop/UDisks2/drives/KINGSTON_SUV400S37480G_50026B776607E79A: Error updating SMART data: sk_disk_smart_read_data: Input/output error (udisks-error-quark, 0)
Dec 11 08:17:01 andrej-inspiron-7720 CRON[18176]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec 11 08:17:41 andrej-inspiron-7720 wpa_supplicant[1021]: wlp2s0: CTRL-EVENT-SIGNAL-CHANGE above=1 signal=-40 noise=9999 txrate=58500
Dec 11 08:17:42 andrej-inspiron-7720 wpa_supplicant[1021]: wlp2s0: CTRL-EVENT-SIGNAL-CHANGE above=1 signal=-35 noise=9999 txrate=58500
Dec 11 08:18:31 andrej-inspiron-7720 acpid: client 1147[0:0] has disconnected
Dec 11 08:18:31 andrej-inspiron-7720 acpid: client connected from 18187[0:0]
Dec 11 08:18:31 andrej-inspiron-7720 acpid: 1 client rule loaded
Dec 11 08:18:32 andrej-inspiron-7720 kernel: [16424.594241] broken atomic modeset userspace detected, disabling atomic
Dec 11 08:18:32 andrej-inspiron-7720 kernel: [16425.252324] broken atomic modeset userspace detected, disabling atomic
Dec 11 08:18:32 andrej-inspiron-7720 acpid: client 18187[0:0] has disconnected
Dec 11 08:18:32 andrej-inspiron-7720 acpid: client connected from 18216[0:0]
Dec 11 08:18:32 andrej-inspiron-7720 acpid: 1 client rule loaded
Dec 11 08:18:34 andrej-inspiron-7720 systemd[1]: Created slice User Slice of lightdm.
Dec 11 08:18:34 andrej-inspiron-7720 systemd[1]: Starting User Manager for UID 110...
Dec 11 08:18:34 andrej-inspiron-7720 systemd[1]: Started Session c4 of user lightdm.
Dec 11 08:18:34 andrej-inspiron-7720 systemd[18293]: Listening on GnuPG network certificate management daemon.
Dec 11 08:18:34 andrej-inspiron-7720 systemd[18293]: Starting D-Bus User Message Bus Socket.
Dec 11 08:18:34 andrej-inspiron-7720 systemd[18293]: Listening on GnuPG cryptographic agent and passphrase cache.
Dec 11 08:18:34 andrej-inspiron-7720 systemd[18293]: Listening on REST API socket for snapd user session agent.
Dec 11 08:18:34 andrej-inspiron-7720 systemd[18293]: Listening on GnuPG cryptographic agent (ssh-agent emulation).
Dec 11 08:18:34 andrej-inspiron-7720 systemd[18293]: Listening on GnuPG cryptographic agent and passphrase cache (restricted).
Dec 11 08:18:34 andrej-inspiron-7720 systemd[18293]: Reached target Paths.
Dec 11 08:18:34 andrej-inspiron-7720 systemd[18293]: Reached target Timers.
Dec 11 08:18:34 andrej-inspiron-7720 systemd[18293]: Listening on GnuPG cryptographic agent and passphrase cache (access for web browsers).
Dec 11 08:18:34 andrej-inspiron-7720 systemd[18293]: Listening on D-Bus User Message Bus Socket.
Dec 11 08:18:34 andrej-inspiron-7720 systemd[18293]: Reached target Sockets.
Dec 11 08:18:34 andrej-inspiron-7720 systemd[18293]: Reached target Basic System.
Dec 11 08:18:34 andrej-inspiron-7720 systemd[18293]: Reached target Default.
Dec 11 08:18:34 andrej-inspiron-7720 systemd[18293]: Startup finished in 40ms.
Dec 11 08:18:34 andrej-inspiron-7720 systemd[1]: Started User Manager for UID 110.
Dec 11 08:18:35 andrej-inspiron-7720 systemd[18293]: Started D-Bus User Message Bus.
Dec 11 08:18:35 andrej-inspiron-7720 dbus-daemon[18313]: [session uid=110 pid=18313] AppArmor D-Bus mediation is enabled
Dec 11 08:18:35 andrej-inspiron-7720 dbus-daemon[18313]: [session uid=110 pid=18313] Activating via systemd: service name='org.a11y.Bus' unit='at-spi-dbus-bus.service' requested by ':1.1' (uid=110 pid=18311 comm="/usr/sbin/lightdm-gtk-greeter " label="unconfined")
Dec 11 08:18:35 andrej-inspiron-7720 systemd[18293]: Starting Accessibility services bus...
Dec 11 08:18:35 andrej-inspiron-7720 dbus-daemon[18313]: [session uid=110 pid=18313] Activating via systemd: service name='org.gtk.vfs.Daemon' unit='gvfs-daemon.service' requested by ':1.2' (uid=110 pid=18314 comm="/usr/lib/at-spi2-core/at-spi-bus-launcher " label="unconfined")
Dec 11 08:18:35 andrej-inspiron-7720 systemd[18293]: Starting Virtual filesystem service...
Dec 11 08:18:35 andrej-inspiron-7720 dbus-daemon[18313]: [session uid=110 pid=18313] Successfully activated service 'org.gtk.vfs.Daemon'
Dec 11 08:18:35 andrej-inspiron-7720 systemd[18293]: Started Virtual filesystem service.
Dec 11 08:18:35 andrej-inspiron-7720 dbus-daemon[18313]: [session uid=110 pid=18313] Successfully activated service 'org.a11y.Bus'
Dec 11 08:18:35 andrej-inspiron-7720 systemd[18293]: Started Accessibility services bus.
Dec 11 08:18:35 andrej-inspiron-7720 at-spi-bus-launcher[18314]: dbus-daemon[18325]: Activating service name='org.a11y.atspi.Registry' requested by ':1.0' (uid=110 pid=18311 comm="/usr/sbin/lightdm-gtk-greeter " label="unconfined")
Dec 11 08:18:35 andrej-inspiron-7720 at-spi-bus-launcher[18314]: dbus-daemon[18325]: Successfully activated service 'org.a11y.atspi.Registry'
Dec 11 08:18:35 andrej-inspiron-7720 at-spi-bus-launcher[18314]: SpiRegistry daemon is running with well-known name - org.a11y.atspi.Registry
Dec 11 08:18:39 andrej-inspiron-7720 systemd[1]: session-c4.scope: Killing process 18269 (lightdm) with signal SIGTERM.
Dec 11 08:18:39 andrej-inspiron-7720 systemd[1]: session-c4.scope: Killing process 18307 (gnome-keyring-d) with signal SIGTERM.
Dec 11 08:18:39 andrej-inspiron-7720 systemd[1]: session-c4.scope: Killing process 18310 (lightdm-greeter) with signal SIGTERM.
Dec 11 08:18:39 andrej-inspiron-7720 systemd[1]: session-c4.scope: Killing process 18311 (lightdm-gtk-gre) with signal SIGTERM.
Dec 11 08:18:39 andrej-inspiron-7720 systemd[1]: Stopping Session c4 of user lightdm.
Dec 11 08:18:39 andrej-inspiron-7720 systemd[1]: Stopped Session c4 of user lightdm.
Dec 11 08:18:39 andrej-inspiron-7720 systemd[1]: Stopping User Manager for UID 110...
Dec 11 08:18:39 andrej-inspiron-7720 systemd[18293]: Stopping D-Bus User Message Bus...
Dec 11 08:18:39 andrej-inspiron-7720 systemd[18293]: Stopped target Default.
Dec 11 08:18:39 andrej-inspiron-7720 systemd[18293]: Stopping Accessibility services bus...
Dec 11 08:18:39 andrej-inspiron-7720 systemd[18293]: Stopping Virtual filesystem service...
Dec 11 08:18:39 andrej-inspiron-7720 systemd[18293]: Stopped D-Bus User Message Bus.
Dec 11 08:18:39 andrej-inspiron-7720 systemd[18293]: Stopped Accessibility services bus.
Dec 11 08:18:39 andrej-inspiron-7720 systemd[18293]: Stopped Virtual filesystem service.
Dec 11 08:18:39 andrej-inspiron-7720 systemd[18293]: Stopped target Basic System.
Dec 11 08:18:39 andrej-inspiron-7720 systemd[18293]: Stopped target Paths.
Dec 11 08:18:39 andrej-inspiron-7720 systemd[18293]: Stopped target Timers.
Dec 11 08:18:39 andrej-inspiron-7720 systemd[18293]: Stopped target Sockets.
Dec 11 08:18:39 andrej-inspiron-7720 systemd[18293]: Closed GnuPG cryptographic agent (ssh-agent emulation).
Dec 11 08:18:39 andrej-inspiron-7720 systemd[18293]: Closed GnuPG cryptographic agent and passphrase cache.
Dec 11 08:18:39 andrej-inspiron-7720 systemd[18293]: Closed GnuPG network certificate management daemon.
Dec 11 08:18:39 andrej-inspiron-7720 systemd[18293]: Closed GnuPG cryptographic agent and passphrase cache (access for web browsers).
Dec 11 08:18:39 andrej-inspiron-7720 systemd[18293]: Closed GnuPG cryptographic agent and passphrase cache (restricted).
Dec 11 08:18:39 andrej-inspiron-7720 systemd[18293]: Closed REST API socket for snapd user session agent.
Dec 11 08:18:39 andrej-inspiron-7720 systemd[18293]: Closed D-Bus User Message Bus Socket.
Dec 11 08:18:39 andrej-inspiron-7720 systemd[18293]: Reached target Shutdown.
Dec 11 08:18:39 andrej-inspiron-7720 systemd[18293]: Starting Exit the Session...
Dec 11 08:18:39 andrej-inspiron-7720 systemd[18293]: Received SIGRTMIN+24 from PID 18365 (kill).
Dec 11 08:18:40 andrej-inspiron-7720 systemd[1]: Stopped User Manager for UID 110.
Dec 11 08:18:40 andrej-inspiron-7720 systemd[1]: Removed slice User Slice of lightdm.
Dec 11 08:18:40 andrej-inspiron-7720 acpid: client 18216[0:0] has disconnected
Dec 11 08:18:40 andrej-inspiron-7720 acpid: client connected from 1147[0:0]
Dec 11 08:18:40 andrej-inspiron-7720 acpid: 1 client rule loaded
Dec 11 08:18:54 andrej-inspiron-7720 dbus-daemon[1453]: apparmor="DENIED" operation="dbus_method_call"  bus="session" path="/org/freedesktop/secrets" interface="org.freedesktop.DBus.Properties" member="GetAll" mask="send" name="org.freedesktop.secrets" pid=18515 label="snap.opera.opera" peer_pid=1435 peer_label="unconfined"
Dec 11 08:18:57 andrej-inspiron-7720 dbus-daemon[1453]: [session uid=1000 pid=1453] Activating service name='io.snapcraft.Settings' requested by ':1.352' (uid=1000 pid=18542 comm="dbus-send --print-reply=literal --session --dest=i" label="snap.opera.opera (enforce)")
Dec 11 08:18:57 andrej-inspiron-7720 dbus-daemon[1453]: [session uid=1000 pid=1453] Successfully activated service 'io.snapcraft.Settings'
Dec 11 08:18:57 andrej-inspiron-7720 io.snapcraft.Settings[1453]: userd.go:98: Starting snap userd
Dec 11 08:19:01 andrej-inspiron-7720 kernel: [16454.038107] kauditd_printk_skb: 26 callbacks suppressed
Dec 11 08:19:01 andrej-inspiron-7720 kernel: [16454.038109] audit: type=1400 audit(1576052341.557:38): apparmor="DENIED" operation="open" profile="snap.opera.opera" name="/run/udev/data/c238:0" pid=18391 comm="ThreadPoolForeg" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
Dec 11 08:19:02 andrej-inspiron-7720 kernel: [16455.444719] audit: type=1400 audit(1576052342.961:39): apparmor="DENIED" operation="file_lock" profile="snap.opera.opera" name="/snap/opera/59/usr/lib/x86_64-linux-gnu/opera/opera_autoupdate" pid=18391 comm="opera" requested_mask="w" denied_mask="w" fsuid=1000 ouid=0
Dec 11 08:19:03 andrej-inspiron-7720 kernel: [16455.847579] audit: type=1400 audit(1576052343.365:40): apparmor="DENIED" operation="file_lock" profile="snap.opera.opera" name="/snap/opera/59/usr/lib/x86_64-linux-gnu/opera/opera_autoupdate" pid=18953 comm="opera_autoupdat" requested_mask="w" denied_mask="w" fsuid=1000 ouid=0
Dec 11 08:19:04 andrej-inspiron-7720 kernel: [16457.052283] perf: interrupt took too long (3143 > 3135), lowering kernel.perf_event_max_sample_rate to 63500

```

---

### Post by Holger_Gehrke on 2019-12-11
Those messages starting at 'Dec 11 08:18:39' look like a controlled shutdown to me with systemd reaching the target shutdown within a second. What I don't see is a reason for the shutdown ... There might be something more in the journal, but after taking a look in my journal I doubt it. I know why my system shut down the last time it did so, but I don't see the reason (I told it to ...) reflected in the journal. BTW, the command to check the end of the journal I gave was optimistic. The shutdown process produces a lot more than the 100 lines I expected, so 'journalctl -b -1|tail -n 500|less' will probably catch everything related to the end of the last session.

Holger

---

### Post by odee2 on 2019-12-12
Here is an journalctl in attachment, from today morning, after unexpected shutdown, complete was 33.5kb but this forum not allow it so I needed to cut some beginnings
[ATTACH]284607[/ATTACH]

---

