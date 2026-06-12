---
title: "Ubuntu won't wake up from Suspend on Dell G5 15 5590"
date: 2024-03-07
forum: General Help
---

### Post by deewens on 2024-03-07
Hello,

I am using Ubuntu 22.04 LTS since 2&#8211;3 weeks on my Dell laptop (which came with Windows by default). It is a Dell G5 15 5590 from 2019 with an Intel i7 9750H and GTX 1660 Ti. I upgraded the RAM to 32 Gb, and replaced the default SSD. 

I have an issue regarding system Suspend. My system used *s2idle" by default. It does not work well at all, when the laptop is going to sleep, it wakes up for no reason, then won't go back to sleep automatically, for unknown reason (like something is keeping it alive). So, I switched the sleep mode from "s2idle" to "sleep". Now, it works better, the laptop won't wake up for no reason, and the battery does not wear as quickly as before, other than the fact that it takes longer to wake up.

Today, I had my laptop plugged to an external display using the HDMI port. I put my laptop to "Suspend" then, I unplugged my laptop from the monitor as well as everything else (mouse, external keyboard, Ethernet, headset). I put it in my bag, and 2 hours later, opened the lid again. I pressed the power button to wake the laptop (I did not plugged it to anything, not even the charger), the keyboard's LED turned on, the screen turned on also, but the screen stayed plain black.

It is a recurring problem, I even had this issue on the s2idle mode. I would like to fix it, but I do not really know where to start. My UEFI is up-to-date from latest version from Dell website. The issue does not happens everytime, it is quite random. Usually it works, but here it didn't, which is even more complicated to try and replicate.

I'm not sure what information I can give you, I ran this comand that I found on ask ubuntu. I'm not sure how to parse it.

```
journalctl --grep='sleep|suspend|resume' --no-pager --since='-1day'
```

```

Mar 06 19:20:36 g5-5590 cups.cups-browsed[2358]: + sleep 3600
Mar 06 20:20:36 g5-5590 cups.cups-browsed[2358]: + sleep 3600
Mar 06 20:28:06 g5-5590 audit[1165]: USER_AVC pid=1165 uid=102 auid=4294967295 ses=4294967295 subj=unconfined msg='apparmor="DENIED" operation="dbus_signal"  bus="system" path="/org/freedesktop/login1" interface="org.freedesktop.login1.Manager" member="PrepareForSleep" name=":1.25" mask="receive" pid=3987 label="snap.bitwarden.bitwarden" peer_pid=1275 peer_label="unconfined"
                                      exe="/usr/bin/dbus-daemon" sauid=102 hostname=? addr=? terminal=?'
Mar 06 20:28:06 g5-5590 audit[1165]: USER_AVC pid=1165 uid=102 auid=4294967295 ses=4294967295 subj=unconfined msg='apparmor="DENIED" operation="dbus_signal"  bus="system" path="/org/freedesktop/login1" interface="org.freedesktop.login1.Manager" member="PrepareForSleep" name=":1.25" mask="receive" pid=47850 label="snap.discord.discord" peer_pid=1275 peer_label="unconfined"
                                      exe="/usr/bin/dbus-daemon" sauid=102 hostname=? addr=? terminal=?'
Mar 06 20:28:06 g5-5590 NetworkManager[1173]: <info>  [1709753286.6512] manager: sleep: sleep requested (sleeping: no  enabled: yes)
Mar 06 20:28:06 g5-5590 NetworkManager[1173]: <info>  [1709753286.6514] device (p2p-dev-wlo1): state change: disconnected -> unmanaged (reason 'sleeping', sys-iface-state: 'managed')
Mar 06 20:28:06 g5-5590 ModemManager[1325]: <info>  [sleep-monitor-systemd] system is about to suspend
Mar 06 20:28:06 g5-5590 NetworkManager[1173]: <info>  [1709753286.6517] manager: NetworkManager state is now ASLEEP
Mar 06 20:28:06 g5-5590 NetworkManager[1173]: <info>  [1709753286.6519] device (enp60s0): state change: activated -> deactivating (reason 'sleeping', sys-iface-state: 'managed')
Mar 06 20:28:06 g5-5590 NetworkManager[1173]: <info>  [1709753286.6527] device (wlo1): state change: activated -> deactivating (reason 'sleeping', sys-iface-state: 'managed')
Mar 06 20:28:06 g5-5590 NetworkManager[1173]: <info>  [1709753286.7019] device (enp60s0): state change: deactivating -> disconnected (reason 'sleeping', sys-iface-state: 'managed')
Mar 06 20:28:06 g5-5590 NetworkManager[1173]: <info>  [1709753286.7576] device (enp60s0): state change: disconnected -> unmanaged (reason 'sleeping', sys-iface-state: 'managed')
Mar 06 20:28:06 g5-5590 NetworkManager[1173]: <info>  [1709753286.9257] device (wlo1): state change: deactivating -> disconnected (reason 'sleeping', sys-iface-state: 'managed')
Mar 06 20:28:06 g5-5590 NetworkManager[1173]: <info>  [1709753286.9452] device (wlo1): state change: disconnected -> unmanaged (reason 'sleeping', sys-iface-state: 'managed')
Mar 06 20:28:07 g5-5590 systemd[1]: Reached target Sleep.
Mar 06 20:28:07 g5-5590 systemd[1]: Starting NVIDIA system suspend actions...
Mar 06 20:28:07 g5-5590 suspend[52208]: nvidia-suspend.service
Mar 06 20:28:07 g5-5590 logger[52208]: <13>Mar  6 20:28:07 suspend: nvidia-suspend.service
Mar 06 20:28:07 g5-5590 /usr/libexec/gdm-x-session[3247]: (II) event2  - Sleep Button: device removed
Mar 06 20:28:07 g5-5590 /usr/libexec/gdm-x-session[3247]: (II) AIGLX: Suspending AIGLX clients for VT switch
Mar 06 20:28:07 g5-5590 systemd[1]: nvidia-suspend.service: Deactivated successfully.
Mar 06 20:28:07 g5-5590 systemd[1]: Finished NVIDIA system suspend actions.
Mar 06 20:28:07 g5-5590 systemd[1]: Starting System Suspend...
Mar 06 20:28:07 g5-5590 systemd-sleep[52224]: Entering sleep state 'suspend'...
Mar 06 20:28:07 g5-5590 kernel: PM: suspend entry (deep)
Mar 06 20:41:12 g5-5590 kernel: printk: Suspending console(s) (use no_console_suspend to debug)
Mar 06 20:41:12 g5-5590 kernel: ACPI: PM: Preparing to enter system sleep state S3
Mar 06 20:41:12 g5-5590 kernel: ACPI: PM: Low-level resume complete
Mar 06 20:41:12 g5-5590 kernel: ACPI: PM: Waking up from system sleep state S3
Mar 06 20:41:12 g5-5590 kernel: xhci_hcd 0000:3a:00.0: xHC error in resume, USBSTS 0x401, Reinit
Mar 06 20:41:12 g5-5590 kernel: xhci_hcd 0000:01:00.2: xHC error in resume, USBSTS 0x401, Reinit
Mar 06 20:41:12 g5-5590 systemd-sleep[52224]: System returned from sleep state.
Mar 06 20:41:12 g5-5590 bluetoothd[1478]: Controller resume with wake event 0x0
Mar 06 20:41:12 g5-5590 kernel: PM: suspend exit
Mar 06 20:41:12 g5-5590 systemd[1]: systemd-suspend.service: Deactivated successfully.
Mar 06 20:41:12 g5-5590 systemd[1]: Finished System Suspend.
Mar 06 20:41:12 g5-5590 systemd[1]: systemd-suspend.service: Consumed 1.020s CPU time.
Mar 06 20:41:12 g5-5590 systemd[1]: Stopped target Sleep.
Mar 06 20:41:12 g5-5590 systemd[1]: Reached target Suspend.
Mar 06 20:41:12 g5-5590 /usr/libexec/gdm-x-session[3247]: (II) systemd-logind: got resume for 13:75
Mar 06 20:41:12 g5-5590 systemd[1]: Starting NVIDIA system resume actions...
Mar 06 20:41:12 g5-5590 systemd[1]: Stopped target Suspend.
Mar 06 20:41:12 g5-5590 suspend[52712]: nvidia-resume.service
Mar 06 20:41:12 g5-5590 logger[52712]: <13>Mar  6 20:41:12 suspend: nvidia-resume.service
Mar 06 20:41:12 g5-5590 systemd[1]: nvidia-resume.service: Deactivated successfully.
Mar 06 20:41:12 g5-5590 systemd[1]: Finished NVIDIA system resume actions.
Mar 06 20:41:12 g5-5590 /usr/libexec/gdm-x-session[3247]: (II) systemd-logind: got resume for 13:84
Mar 06 20:41:12 g5-5590 /usr/libexec/gdm-x-session[3247]: (II) systemd-logind: got resume for 13:72
Mar 06 20:41:12 g5-5590 /usr/libexec/gdm-x-session[3247]: (II) systemd-logind: got resume for 13:65
Mar 06 20:41:12 g5-5590 /usr/libexec/gdm-x-session[3247]: (II) systemd-logind: got resume for 13:78
Mar 06 20:41:12 g5-5590 /usr/libexec/gdm-x-session[3247]: (II) systemd-logind: got resume for 13:86
Mar 06 20:41:12 g5-5590 /usr/libexec/gdm-x-session[3247]: (II) systemd-logind: got resume for 13:87
Mar 06 20:41:12 g5-5590 /usr/libexec/gdm-x-session[3247]: (II) systemd-logind: got resume for 226:0
Mar 06 20:41:13 g5-5590 systemd-logind[1275]: Operation 'sleep' finished.
Mar 06 20:41:13 g5-5590 audit[1165]: USER_AVC pid=1165 uid=102 auid=4294967295 ses=4294967295 subj=unconfined msg='apparmor="DENIED" operation="dbus_signal"  bus="system" path="/org/freedesktop/login1" interface="org.freedesktop.login1.Manager" member="PrepareForSleep" name=":1.25" mask="receive" pid=3987 label="snap.bitwarden.bitwarden" peer_pid=1275 peer_label="unconfined"
                                      exe="/usr/bin/dbus-daemon" sauid=102 hostname=? addr=? terminal=?'
Mar 06 20:41:13 g5-5590 audit[1165]: USER_AVC pid=1165 uid=102 auid=4294967295 ses=4294967295 subj=unconfined msg='apparmor="DENIED" operation="dbus_signal"  bus="system" path="/org/freedesktop/login1" interface="org.freedesktop.login1.Manager" member="PrepareForSleep" name=":1.25" mask="receive" pid=47850 label="snap.discord.discord" peer_pid=1275 peer_label="unconfined"
                                      exe="/usr/bin/dbus-daemon" sauid=102 hostname=? addr=? terminal=?'
Mar 06 20:41:13 g5-5590 ModemManager[1325]: <info>  [sleep-monitor-systemd] system is resuming
Mar 06 20:41:13 g5-5590 NetworkManager[1173]: <info>  [1709754073.1585] manager: sleep: wake requested (sleeping: yes  enabled: yes)
Mar 06 20:41:13 g5-5590 /usr/libexec/gdm-x-session[3247]: (II) systemd-logind: got resume for 13:85
Mar 06 20:41:13 g5-5590 /usr/libexec/gdm-x-session[3247]: (II) systemd-logind: got resume for 13:69
Mar 06 20:41:13 g5-5590 /usr/libexec/gdm-x-session[3247]: (II) systemd-logind: got resume for 13:79
Mar 06 20:41:13 g5-5590 /usr/libexec/gdm-x-session[3247]: (II) systemd-logind: got resume for 13:80
Mar 06 20:41:13 g5-5590 /usr/libexec/gdm-x-session[3247]: (II) systemd-logind: got resume for 13:74
Mar 06 20:41:13 g5-5590 /usr/libexec/gdm-x-session[3247]: (II) systemd-logind: got resume for 13:66
Mar 06 20:41:13 g5-5590 /usr/libexec/gdm-x-session[3247]: (II) event2  - Sleep Button: is tagged by udev as: Keyboard
Mar 06 20:41:13 g5-5590 /usr/libexec/gdm-x-session[3247]: (II) event2  - Sleep Button: device is a keyboard
Mar 06 20:41:13 g5-5590 /usr/libexec/gdm-x-session[3247]: (II) systemd-logind: got resume for 13:73
Mar 06 20:41:13 g5-5590 /usr/libexec/gdm-x-session[3247]: (II) systemd-logind: got resume for 13:71
Mar 06 20:41:13 g5-5590 /usr/libexec/gdm-x-session[3247]: (II) systemd-logind: got resume for 13:76
Mar 06 20:41:13 g5-5590 /usr/libexec/gdm-x-session[3247]: (II) systemd-logind: got resume for 13:77
Mar 06 20:41:13 g5-5590 /usr/libexec/gdm-x-session[3247]: (II) systemd-logind: got resume for 13:67
Mar 06 20:48:10 g5-5590 audit[58284]: AVC apparmor="DENIED" operation="open" class="file" profile="snap.steam.steam" name="/sys/power/suspend_stats/success" pid=58284 comm="IPC:CSteamEngin" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
Mar 06 21:33:36 g5-5590 cups.cups-browsed[2358]: + sleep 3600
Mar 06 21:59:14 g5-5590 audit[1165]: USER_AVC pid=1165 uid=102 auid=4294967295 ses=4294967295 subj=unconfined msg='apparmor="DENIED" operation="dbus_signal"  bus="system" path="/org/freedesktop/login1" interface="org.freedesktop.login1.Manager" member="PrepareForSleep" name=":1.25" mask="receive" pid=3987 label="snap.bitwarden.bitwarden" peer_pid=1275 peer_label="unconfined"
                                      exe="/usr/bin/dbus-daemon" sauid=102 hostname=? addr=? terminal=?'
Mar 06 21:59:14 g5-5590 audit[1165]: USER_AVC pid=1165 uid=102 auid=4294967295 ses=4294967295 subj=unconfined msg='apparmor="DENIED" operation="dbus_signal"  bus="system" path="/org/freedesktop/login1" interface="org.freedesktop.login1.Manager" member="PrepareForSleep" name=":1.25" mask="receive" pid=47850 label="snap.discord.discord" peer_pid=1275 peer_label="unconfined"
                                      exe="/usr/bin/dbus-daemon" sauid=102 hostname=? addr=? terminal=?'
Mar 06 21:59:14 g5-5590 audit[1165]: USER_AVC pid=1165 uid=102 auid=4294967295 ses=4294967295 subj=unconfined msg='apparmor="DENIED" operation="dbus_signal"  bus="system" path="/org/freedesktop/login1" interface="org.freedesktop.login1.Manager" member="PrepareForSleep" name=":1.25" mask="receive" pid=54151 label="snap.firefox.firefox" peer_pid=1275 peer_label="unconfined"
                                      exe="/usr/bin/dbus-daemon" sauid=102 hostname=? addr=? terminal=?'
Mar 06 21:59:14 g5-5590 audit[1165]: USER_AVC pid=1165 uid=102 auid=4294967295 ses=4294967295 subj=unconfined msg='apparmor="DENIED" operation="dbus_signal"  bus="system" path="/org/freedesktop/login1" interface="org.freedesktop.login1.Manager" member="PrepareForSleep" name=":1.25" mask="receive" pid=58284 label="snap.steam.steam" peer_pid=1275 peer_label="unconfined"
                                      exe="/usr/bin/dbus-daemon" sauid=102 hostname=? addr=? terminal=?'
Mar 06 21:59:14 g5-5590 NetworkManager[1173]: <info>  [1709758754.8491] manager: sleep: sleep requested (sleeping: no  enabled: yes)
Mar 06 21:59:14 g5-5590 ModemManager[1325]: <info>  [sleep-monitor-systemd] system is about to suspend
Mar 06 21:59:14 g5-5590 NetworkManager[1173]: <info>  [1709758754.8494] device (p2p-dev-wlo1): state change: disconnected -> unmanaged (reason 'sleeping', sys-iface-state: 'managed')
Mar 06 21:59:14 g5-5590 NetworkManager[1173]: <info>  [1709758754.8503] manager: NetworkManager state is now ASLEEP
Mar 06 21:59:14 g5-5590 NetworkManager[1173]: <info>  [1709758754.8507] device (enp60s0): state change: activated -> deactivating (reason 'sleeping', sys-iface-state: 'managed')
Mar 06 21:59:14 g5-5590 NetworkManager[1173]: <info>  [1709758754.8539] device (wlo1): state change: activated -> deactivating (reason 'sleeping', sys-iface-state: 'managed')
Mar 06 21:59:14 g5-5590 NetworkManager[1173]: <info>  [1709758754.9265] device (enp60s0): state change: deactivating -> disconnected (reason 'sleeping', sys-iface-state: 'managed')
Mar 06 21:59:14 g5-5590 NetworkManager[1173]: <info>  [1709758754.9330] device (enp60s0): state change: disconnected -> unmanaged (reason 'sleeping', sys-iface-state: 'managed')
Mar 06 21:59:15 g5-5590 NetworkManager[1173]: <info>  [1709758755.1282] device (wlo1): state change: deactivating -> disconnected (reason 'sleeping', sys-iface-state: 'managed')
Mar 06 21:59:15 g5-5590 NetworkManager[1173]: <info>  [1709758755.1935] device (wlo1): state change: disconnected -> unmanaged (reason 'sleeping', sys-iface-state: 'managed')
Mar 06 21:59:15 g5-5590 systemd[1]: Reached target Sleep.
Mar 06 21:59:15 g5-5590 systemd[1]: Starting NVIDIA system suspend actions...
Mar 06 21:59:15 g5-5590 suspend[68693]: nvidia-suspend.service
Mar 06 21:59:15 g5-5590 logger[68693]: <13>Mar  6 21:59:15 suspend: nvidia-suspend.service
Mar 06 21:59:15 g5-5590 /usr/libexec/gdm-x-session[3247]: (II) event2  - Sleep Button: device removed
Mar 06 21:59:15 g5-5590 /usr/libexec/gdm-x-session[3247]: (II) AIGLX: Suspending AIGLX clients for VT switch
Mar 06 21:59:16 g5-5590 systemd[1]: nvidia-suspend.service: Deactivated successfully.
Mar 06 21:59:16 g5-5590 systemd[1]: Finished NVIDIA system suspend actions.
Mar 06 21:59:16 g5-5590 systemd[1]: Starting System Suspend...
Mar 06 21:59:16 g5-5590 systemd-sleep[68727]: Entering sleep state 'suspend'...
Mar 06 21:59:16 g5-5590 kernel: PM: suspend entry (deep)
Mar 06 22:56:39 g5-5590 kernel: printk: Suspending console(s) (use no_console_suspend to debug)
Mar 06 22:56:39 g5-5590 kernel: ACPI: PM: Preparing to enter system sleep state S3
Mar 06 22:56:39 g5-5590 kernel: ACPI: PM: Low-level resume complete
Mar 06 22:56:39 g5-5590 kernel: ACPI: PM: Waking up from system sleep state S3
Mar 06 22:56:39 g5-5590 kernel: xhci_hcd 0000:3a:00.0: xHC error in resume, USBSTS 0x401, Reinit
Mar 06 22:56:39 g5-5590 kernel: xhci_hcd 0000:01:00.2: xHC error in resume, USBSTS 0x401, Reinit
Mar 06 22:56:39 g5-5590 systemd-sleep[68727]: System returned from sleep state.
Mar 06 22:56:39 g5-5590 bluetoothd[1478]: Controller resume with wake event 0x0
Mar 06 22:56:39 g5-5590 kernel: PM: suspend exit
Mar 06 22:56:39 g5-5590 systemd[1]: systemd-suspend.service: Deactivated successfully.
Mar 06 22:56:39 g5-5590 systemd[1]: Finished System Suspend.
Mar 06 22:56:39 g5-5590 systemd[1]: systemd-suspend.service: Consumed 1.152s CPU time.
Mar 06 22:56:39 g5-5590 systemd[1]: Stopped target Sleep.
Mar 06 22:56:39 g5-5590 systemd[1]: Reached target Suspend.
Mar 06 22:56:39 g5-5590 systemd[1]: Starting NVIDIA system resume actions...
Mar 06 22:56:39 g5-5590 systemd[1]: Stopped target Suspend.
Mar 06 22:56:39 g5-5590 /usr/libexec/gdm-x-session[3247]: (II) systemd-logind: got resume for 13:75
Mar 06 22:56:39 g5-5590 suspend[69212]: nvidia-resume.service
Mar 06 22:56:39 g5-5590 logger[69212]: <13>Mar  6 22:56:39 suspend: nvidia-resume.service
Mar 06 22:56:39 g5-5590 systemd[1]: nvidia-resume.service: Deactivated successfully.
Mar 06 22:56:39 g5-5590 systemd[1]: Finished NVIDIA system resume actions.
Mar 06 22:56:39 g5-5590 /usr/libexec/gdm-x-session[3247]: (II) systemd-logind: got resume for 13:84
Mar 06 22:56:39 g5-5590 /usr/libexec/gdm-x-session[3247]: (II) systemd-logind: got resume for 13:72
Mar 06 22:56:39 g5-5590 /usr/libexec/gdm-x-session[3247]: (II) systemd-logind: got resume for 13:65
Mar 06 22:56:39 g5-5590 /usr/libexec/gdm-x-session[3247]: (II) systemd-logind: got resume for 13:78
Mar 06 22:56:40 g5-5590 /usr/libexec/gdm-x-session[3247]: (II) systemd-logind: got resume for 13:86
Mar 06 22:56:40 g5-5590 /usr/libexec/gdm-x-session[3247]: (II) systemd-logind: got resume for 13:87
Mar 06 22:56:40 g5-5590 /usr/libexec/gdm-x-session[3247]: (II) systemd-logind: got resume for 226:0
Mar 06 22:56:40 g5-5590 systemd-logind[1275]: Operation 'sleep' finished.
Mar 06 22:56:40 g5-5590 audit[1165]: USER_AVC pid=1165 uid=102 auid=4294967295 ses=4294967295 subj=unconfined msg='apparmor="DENIED" operation="dbus_signal"  bus="system" path="/org/freedesktop/login1" interface="org.freedesktop.login1.Manager" member="PrepareForSleep" name=":1.25" mask="receive" pid=3987 label="snap.bitwarden.bitwarden" peer_pid=1275 peer_label="unconfined"
                                      exe="/usr/bin/dbus-daemon" sauid=102 hostname=? addr=? terminal=?'
Mar 06 22:56:40 g5-5590 audit[1165]: USER_AVC pid=1165 uid=102 auid=4294967295 ses=4294967295 subj=unconfined msg='apparmor="DENIED" operation="dbus_signal"  bus="system" path="/org/freedesktop/login1" interface="org.freedesktop.login1.Manager" member="PrepareForSleep" name=":1.25" mask="receive" pid=47850 label="snap.discord.discord" peer_pid=1275 peer_label="unconfined"
                                      exe="/usr/bin/dbus-daemon" sauid=102 hostname=? addr=? terminal=?'
Mar 06 22:56:40 g5-5590 audit[1165]: USER_AVC pid=1165 uid=102 auid=4294967295 ses=4294967295 subj=unconfined msg='apparmor="DENIED" operation="dbus_signal"  bus="system" path="/org/freedesktop/login1" interface="org.freedesktop.login1.Manager" member="PrepareForSleep" name=":1.25" mask="receive" pid=54151 label="snap.firefox.firefox" peer_pid=1275 peer_label="unconfined"
                                      exe="/usr/bin/dbus-daemon" sauid=102 hostname=? addr=? terminal=?'
Mar 06 22:56:40 g5-5590 audit[1165]: USER_AVC pid=1165 uid=102 auid=4294967295 ses=4294967295 subj=unconfined msg='apparmor="DENIED" operation="dbus_signal"  bus="system" path="/org/freedesktop/login1" interface="org.freedesktop.login1.Manager" member="PrepareForSleep" name=":1.25" mask="receive" pid=58284 label="snap.steam.steam" peer_pid=1275 peer_label="unconfined"
                                      exe="/usr/bin/dbus-daemon" sauid=102 hostname=? addr=? terminal=?'
Mar 06 22:56:40 g5-5590 NetworkManager[1173]: <info>  [1709762200.3173] manager: sleep: wake requested (sleeping: yes  enabled: yes)
Mar 06 22:56:40 g5-5590 ModemManager[1325]: <info>  [sleep-monitor-systemd] system is resuming
Mar 06 22:56:40 g5-5590 /usr/libexec/gdm-x-session[3247]: (II) systemd-logind: got resume for 13:85
Mar 06 22:56:40 g5-5590 /usr/libexec/gdm-x-session[3247]: (II) systemd-logind: got resume for 13:69
Mar 06 22:56:40 g5-5590 /usr/libexec/gdm-x-session[3247]: (II) systemd-logind: got resume for 13:79
Mar 06 22:56:40 g5-5590 /usr/libexec/gdm-x-session[3247]: (II) systemd-logind: got resume for 13:80
Mar 06 22:56:40 g5-5590 /usr/libexec/gdm-x-session[3247]: (II) systemd-logind: got resume for 13:74
Mar 06 22:56:40 g5-5590 /usr/libexec/gdm-x-session[3247]: (II) systemd-logind: got resume for 13:66
Mar 06 22:56:40 g5-5590 /usr/libexec/gdm-x-session[3247]: (II) event2  - Sleep Button: is tagged by udev as: Keyboard
Mar 06 22:56:40 g5-5590 /usr/libexec/gdm-x-session[3247]: (II) event2  - Sleep Button: device is a keyboard
Mar 06 22:56:40 g5-5590 /usr/libexec/gdm-x-session[3247]: (II) systemd-logind: got resume for 13:73
Mar 06 22:56:40 g5-5590 /usr/libexec/gdm-x-session[3247]: (II) systemd-logind: got resume for 13:71
Mar 06 22:56:40 g5-5590 /usr/libexec/gdm-x-session[3247]: (II) systemd-logind: got resume for 13:76
Mar 06 22:56:40 g5-5590 /usr/libexec/gdm-x-session[3247]: (II) systemd-logind: got resume for 13:77
Mar 06 22:56:40 g5-5590 /usr/libexec/gdm-x-session[3247]: (II) systemd-logind: got resume for 13:67
Mar 06 23:30:55 g5-5590 cups.cups-browsed[2358]: + sleep 3600
Mar 06 23:44:44 g5-5590 /usr/libexec/gdm-x-session[3247]: (II) event2  - Sleep Button: device removed
-- Boot de60cfb2d9a44eb3a8d2f6df2d3a800f --
Mar 07 11:04:08 g5-5590 kernel: Command line: BOOT_IMAGE=/boot/vmlinuz-6.5.0-21-generic root=UUID=b1baf06a-11df-4f46-b63d-d2c95c1c40a3 ro quiet splash mem_sleep_default=deep vt.handoff=7
Mar 07 11:04:08 g5-5590 kernel: Kernel command line: BOOT_IMAGE=/boot/vmlinuz-6.5.0-21-generic root=UUID=b1baf06a-11df-4f46-b63d-d2c95c1c40a3 ro quiet splash mem_sleep_default=deep vt.handoff=7
Mar 07 11:04:08 g5-5590 kernel: input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2
Mar 07 11:04:08 g5-5590 kernel: ACPI: button: Sleep Button [SBTN]
Mar 07 11:04:10 g5-5590 systemd-logind[1266]: Watching system buttons on /dev/input/event2 (Sleep Button)
Mar 07 11:04:12 g5-5590 cups.cups-browsed[1391]: + sleep 1
Mar 07 11:04:12 g5-5590 /usr/libexec/gdm-x-session[2274]: Kernel command line: BOOT_IMAGE=/boot/vmlinuz-6.5.0-21-generic root=UUID=b1baf06a-11df-4f46-b63d-d2c95c1c40a3 ro quiet splash mem_sleep_default=deep vt.handoff=7
Mar 07 11:04:13 g5-5590 cups.cups-browsed[2414]: + sleep 3600
Mar 07 11:04:13 g5-5590 /usr/libexec/gdm-x-session[2274]: (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
Mar 07 11:04:13 g5-5590 /usr/libexec/gdm-x-session[2274]: (**) Sleep Button: Applying InputClass "libinput keyboard catchall"
Mar 07 11:04:13 g5-5590 /usr/libexec/gdm-x-session[2274]: (II) Using input driver 'libinput' for 'Sleep Button'
Mar 07 11:04:13 g5-5590 /usr/libexec/gdm-x-session[2274]: (**) Sleep Button: always reports core events
Mar 07 11:04:13 g5-5590 /usr/libexec/gdm-x-session[2274]: (II) event2  - Sleep Button: is tagged by udev as: Keyboard
Mar 07 11:04:13 g5-5590 /usr/libexec/gdm-x-session[2274]: (II) event2  - Sleep Button: device is a keyboard
Mar 07 11:04:13 g5-5590 /usr/libexec/gdm-x-session[2274]: (II) event2  - Sleep Button: device removed
Mar 07 11:04:13 g5-5590 /usr/libexec/gdm-x-session[2274]: (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 9)
Mar 07 11:04:13 g5-5590 /usr/libexec/gdm-x-session[2274]: (II) event2  - Sleep Button: is tagged by udev as: Keyboard
Mar 07 11:04:13 g5-5590 /usr/libexec/gdm-x-session[2274]: (II) event2  - Sleep Button: device is a keyboard
Mar 07 11:05:36 g5-5590 /usr/libexec/gdm-x-session[2274]: (II) event2  - Sleep Button: device removed
Mar 07 11:05:36 g5-5590 /usr/libexec/gdm-x-session[2274]: (II) AIGLX: Suspending AIGLX clients for VT switch
Mar 07 11:05:36 g5-5590 /usr/libexec/gdm-x-session[3361]: Kernel command line: BOOT_IMAGE=/boot/vmlinuz-6.5.0-21-generic root=UUID=b1baf06a-11df-4f46-b63d-d2c95c1c40a3 ro quiet splash mem_sleep_default=deep vt.handoff=7
Mar 07 11:05:37 g5-5590 /usr/libexec/gdm-x-session[3361]: (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
Mar 07 11:05:37 g5-5590 /usr/libexec/gdm-x-session[3361]: (**) Sleep Button: Applying InputClass "libinput keyboard catchall"
Mar 07 11:05:37 g5-5590 /usr/libexec/gdm-x-session[3361]: (II) Using input driver 'libinput' for 'Sleep Button'
Mar 07 11:05:37 g5-5590 /usr/libexec/gdm-x-session[3361]: (**) Sleep Button: always reports core events
Mar 07 11:05:37 g5-5590 /usr/libexec/gdm-x-session[3361]: (II) event2  - Sleep Button: is tagged by udev as: Keyboard
Mar 07 11:05:37 g5-5590 /usr/libexec/gdm-x-session[3361]: (II) event2  - Sleep Button: device is a keyboard
Mar 07 11:05:37 g5-5590 /usr/libexec/gdm-x-session[3361]: (II) event2  - Sleep Button: device removed
Mar 07 11:05:37 g5-5590 /usr/libexec/gdm-x-session[3361]: (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 9)
Mar 07 11:05:37 g5-5590 /usr/libexec/gdm-x-session[3361]: (II) event2  - Sleep Button: is tagged by udev as: Keyboard
Mar 07 11:05:37 g5-5590 /usr/libexec/gdm-x-session[3361]: (II) event2  - Sleep Button: device is a keyboard
Mar 07 11:33:32 g5-5590 systemd[1]: Starting Suspend/Resume Running libvirt Guests...
Mar 07 11:33:32 g5-5590 systemd[1]: Finished Suspend/Resume Running libvirt Guests.
Mar 07 11:38:04 g5-5590 /usr/libexec/gdm-x-session[3361]: (II) event2  - Sleep Button: device removed
Mar 07 11:38:04 g5-5590 systemd[1]: Stopping Suspend/Resume Running libvirt Guests...
Mar 07 11:38:05 g5-5590 systemd[1]: Stopped Suspend/Resume Running libvirt Guests.
-- Boot 87c81da1001945ce8bc5fd0539a55515 --
Mar 07 11:38:32 g5-5590 kernel: Command line: BOOT_IMAGE=/boot/vmlinuz-6.5.0-21-generic root=UUID=b1baf06a-11df-4f46-b63d-d2c95c1c40a3 ro quiet splash mem_sleep_default=deep vt.handoff=7
Mar 07 11:38:32 g5-5590 kernel: Kernel command line: BOOT_IMAGE=/boot/vmlinuz-6.5.0-21-generic root=UUID=b1baf06a-11df-4f46-b63d-d2c95c1c40a3 ro quiet splash mem_sleep_default=deep vt.handoff=7
Mar 07 11:38:32 g5-5590 kernel: input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2
Mar 07 11:38:32 g5-5590 kernel: ACPI: button: Sleep Button [SBTN]
Mar 07 11:38:34 g5-5590 systemd-logind[1241]: Watching system buttons on /dev/input/event2 (Sleep Button)
Mar 07 11:38:34 g5-5590 systemd[1]: Starting Suspend/Resume Running libvirt Guests...
Mar 07 11:38:34 g5-5590 systemd[1]: Finished Suspend/Resume Running libvirt Guests.
Mar 07 11:38:36 g5-5590 cups.cups-browsed[1398]: + sleep 1
Mar 07 11:38:36 g5-5590 /usr/libexec/gdm-x-session[2445]: Kernel command line: BOOT_IMAGE=/boot/vmlinuz-6.5.0-21-generic root=UUID=b1baf06a-11df-4f46-b63d-d2c95c1c40a3 ro quiet splash mem_sleep_default=deep vt.handoff=7
Mar 07 11:38:37 g5-5590 cups.cups-browsed[2574]: sleep
Mar 07 11:38:37 g5-5590 /usr/libexec/gdm-x-session[2445]: (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
Mar 07 11:38:37 g5-5590 /usr/libexec/gdm-x-session[2445]: (**) Sleep Button: Applying InputClass "libinput keyboard catchall"
Mar 07 11:38:37 g5-5590 /usr/libexec/gdm-x-session[2445]: (II) Using input driver 'libinput' for 'Sleep Button'
Mar 07 11:38:37 g5-5590 /usr/libexec/gdm-x-session[2445]: (**) Sleep Button: always reports core events
Mar 07 11:38:37 g5-5590 /usr/libexec/gdm-x-session[2445]: (II) event2  - Sleep Button: is tagged by udev as: Keyboard
Mar 07 11:38:37 g5-5590 /usr/libexec/gdm-x-session[2445]: (II) event2  - Sleep Button: device is a keyboard
Mar 07 11:38:37 g5-5590 /usr/libexec/gdm-x-session[2445]: (II) event2  - Sleep Button: device removed
Mar 07 11:38:37 g5-5590 /usr/libexec/gdm-x-session[2445]: (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 9)
Mar 07 11:38:37 g5-5590 /usr/libexec/gdm-x-session[2445]: (II) event2  - Sleep Button: is tagged by udev as: Keyboard
Mar 07 11:38:37 g5-5590 /usr/libexec/gdm-x-session[2445]: (II) event2  - Sleep Button: device is a keyboard
Mar 07 11:38:48 g5-5590 /usr/libexec/gdm-x-session[2445]: (II) event2  - Sleep Button: device removed
Mar 07 11:38:48 g5-5590 /usr/libexec/gdm-x-session[2445]: (II) AIGLX: Suspending AIGLX clients for VT switch
Mar 07 11:38:48 g5-5590 /usr/libexec/gdm-x-session[3489]: Kernel command line: BOOT_IMAGE=/boot/vmlinuz-6.5.0-21-generic root=UUID=b1baf06a-11df-4f46-b63d-d2c95c1c40a3 ro quiet splash mem_sleep_default=deep vt.handoff=7
Mar 07 11:38:49 g5-5590 /usr/libexec/gdm-x-session[3489]: (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
Mar 07 11:38:49 g5-5590 /usr/libexec/gdm-x-session[3489]: (**) Sleep Button: Applying InputClass "libinput keyboard catchall"
Mar 07 11:38:49 g5-5590 /usr/libexec/gdm-x-session[3489]: (II) Using input driver 'libinput' for 'Sleep Button'
Mar 07 11:38:49 g5-5590 /usr/libexec/gdm-x-session[3489]: (**) Sleep Button: always reports core events
Mar 07 11:38:49 g5-5590 /usr/libexec/gdm-x-session[3489]: (II) event2  - Sleep Button: is tagged by udev as: Keyboard
Mar 07 11:38:49 g5-5590 /usr/libexec/gdm-x-session[3489]: (II) event2  - Sleep Button: device is a keyboard
Mar 07 11:38:49 g5-5590 /usr/libexec/gdm-x-session[3489]: (II) event2  - Sleep Button: device removed
Mar 07 11:38:49 g5-5590 /usr/libexec/gdm-x-session[3489]: (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 9)
Mar 07 11:38:49 g5-5590 /usr/libexec/gdm-x-session[3489]: (II) event2  - Sleep Button: is tagged by udev as: Keyboard
Mar 07 11:38:49 g5-5590 /usr/libexec/gdm-x-session[3489]: (II) event2  - Sleep Button: device is a keyboard
Mar 07 11:54:28 g5-5590 audit[1190]: USER_AVC pid=1190 uid=102 auid=4294967295 ses=4294967295 subj=unconfined msg='apparmor="DENIED" operation="dbus_signal"  bus="system" path="/org/freedesktop/login1" interface="org.freedesktop.login1.Manager" member="PrepareForSleep" name=":1.22" mask="receive" pid=4231 label="snap.bitwarden.bitwarden" peer_pid=1241 peer_label="unconfined"
                                      exe="/usr/bin/dbus-daemon" sauid=102 hostname=? addr=? terminal=?'
Mar 07 11:54:28 g5-5590 NetworkManager[1192]: <info>  [1709808868.2289] manager: sleep: sleep requested (sleeping: no  enabled: yes)
Mar 07 11:54:28 g5-5590 NetworkManager[1192]: <info>  [1709808868.2290] device (p2p-dev-wlo1): state change: disconnected -> unmanaged (reason 'sleeping', sys-iface-state: 'managed')
Mar 07 11:54:28 g5-5590 ModemManager[1336]: <info>  [sleep-monitor-systemd] system is about to suspend
Mar 07 11:54:28 g5-5590 NetworkManager[1192]: <info>  [1709808868.2294] manager: NetworkManager state is now ASLEEP
Mar 07 11:54:28 g5-5590 NetworkManager[1192]: <info>  [1709808868.2295] device (enp60s0): state change: activated -> deactivating (reason 'sleeping', sys-iface-state: 'managed')
Mar 07 11:54:28 g5-5590 kernel: audit: type=1107 audit(1709808868.224:181): pid=1190 uid=102 auid=4294967295 ses=4294967295 subj=unconfined msg='apparmor="DENIED" operation="dbus_signal"  bus="system" path="/org/freedesktop/login1" interface="org.freedesktop.login1.Manager" member="PrepareForSleep" name=":1.22" mask="receive" pid=4231 label="snap.bitwarden.bitwarden" peer_pid=1241 peer_label="unconfined"
                                 exe="/usr/bin/dbus-daemon" sauid=102 hostname=? addr=? terminal=?'
Mar 07 11:54:28 g5-5590 NetworkManager[1192]: <info>  [1709808868.2303] device (wlo1): state change: activated -> deactivating (reason 'sleeping', sys-iface-state: 'managed')
Mar 07 11:54:28 g5-5590 NetworkManager[1192]: <info>  [1709808868.3024] device (enp60s0): state change: deactivating -> disconnected (reason 'sleeping', sys-iface-state: 'managed')
Mar 07 11:54:28 g5-5590 NetworkManager[1192]: <info>  [1709808868.3536] device (enp60s0): state change: disconnected -> unmanaged (reason 'sleeping', sys-iface-state: 'managed')
Mar 07 11:54:28 g5-5590 NetworkManager[1192]: <info>  [1709808868.5384] device (wlo1): state change: deactivating -> disconnected (reason 'sleeping', sys-iface-state: 'managed')
Mar 07 11:54:28 g5-5590 NetworkManager[1192]: <info>  [1709808868.6064] device (wlo1): state change: disconnected -> unmanaged (reason 'sleeping', sys-iface-state: 'managed')
Mar 07 11:54:28 g5-5590 systemd[1]: Reached target Sleep.
Mar 07 11:54:28 g5-5590 systemd[1]: Starting NVIDIA system suspend actions...
Mar 07 11:54:28 g5-5590 suspend[5680]: nvidia-suspend.service
Mar 07 11:54:28 g5-5590 logger[5680]: <13>Mar  7 11:54:28 suspend: nvidia-suspend.service
Mar 07 11:54:30 g5-5590 /usr/libexec/gdm-x-session[3489]: (II) event2  - Sleep Button: device removed
Mar 07 11:54:30 g5-5590 /usr/libexec/gdm-x-session[3489]: (II) AIGLX: Suspending AIGLX clients for VT switch
Mar 07 11:54:30 g5-5590 systemd[1]: nvidia-suspend.service: Deactivated successfully.
Mar 07 11:54:30 g5-5590 systemd[1]: Finished NVIDIA system suspend actions.
Mar 07 11:54:30 g5-5590 systemd[1]: Starting System Suspend...
Mar 07 11:54:30 g5-5590 systemd-sleep[5718]: Entering sleep state 'suspend'...
Mar 07 11:54:30 g5-5590 kernel: PM: suspend entry (deep)
Mar 07 15:33:38 g5-5590 kernel: printk: Suspending console(s) (use no_console_suspend to debug)
Mar 07 15:33:38 g5-5590 kernel: ACPI: PM: Preparing to enter system sleep state S3
Mar 07 15:33:38 g5-5590 kernel: ACPI: PM: Low-level resume complete
Mar 07 15:33:38 g5-5590 kernel: ACPI: PM: Waking up from system sleep state S3
Mar 07 15:33:38 g5-5590 kernel: xhci_hcd 0000:3a:00.0: xHC error in resume, USBSTS 0x401, Reinit
Mar 07 15:33:38 g5-5590 kernel: xhci_hcd 0000:01:00.2: xHC error in resume, USBSTS 0x401, Reinit
Mar 07 15:33:38 g5-5590 systemd-sleep[5718]: System returned from sleep state.
Mar 07 15:33:38 g5-5590 kernel: PM: suspend exit
Mar 07 15:33:38 g5-5590 bluetoothd[1527]: Controller resume with wake event 0x0
Mar 07 15:33:38 g5-5590 systemd[1]: systemd-suspend.service: Deactivated successfully.
Mar 07 15:33:38 g5-5590 systemd[1]: Finished System Suspend.
Mar 07 15:33:38 g5-5590 systemd[1]: systemd-suspend.service: Consumed 1.331s CPU time.
Mar 07 15:33:38 g5-5590 systemd[1]: Stopped target Sleep.
Mar 07 15:33:38 g5-5590 systemd[1]: Reached target Suspend.
Mar 07 15:33:38 g5-5590 systemd[1]: Starting NVIDIA system resume actions...
Mar 07 15:33:38 g5-5590 systemd[1]: Stopped target Suspend.
Mar 07 15:33:38 g5-5590 suspend[6190]: nvidia-resume.service
Mar 07 15:33:38 g5-5590 logger[6190]: <13>Mar  7 15:33:38 suspend: nvidia-resume.service
Mar 07 15:33:38 g5-5590 /usr/libexec/gdm-x-session[3489]: (II) systemd-logind: got resume for 13:87
Mar 07 15:33:38 g5-5590 systemd[1]: nvidia-resume.service: Deactivated successfully.
Mar 07 15:33:38 g5-5590 systemd[1]: Finished NVIDIA system resume actions.
Mar 07 15:33:38 g5-5590 /usr/libexec/gdm-x-session[3489]: (II) systemd-logind: got resume for 13:83
Mar 07 15:33:38 g5-5590 /usr/libexec/gdm-x-session[3489]: (II) systemd-logind: got resume for 13:78
Mar 07 15:33:38 g5-5590 /usr/libexec/gdm-x-session[3489]: (II) systemd-logind: got resume for 13:73
Mar 07 15:33:38 g5-5590 /usr/libexec/gdm-x-session[3489]: (II) systemd-logind: got resume for 13:86
Mar 07 15:33:38 g5-5590 /usr/libexec/gdm-x-session[3489]: (II) systemd-logind: got resume for 13:80
Mar 07 15:33:38 g5-5590 /usr/libexec/gdm-x-session[3489]: (II) systemd-logind: got resume for 13:71
Mar 07 15:33:39 g5-5590 /usr/libexec/gdm-x-session[3489]: (II) systemd-logind: got resume for 13:79
Mar 07 15:33:39 g5-5590 /usr/libexec/gdm-x-session[3489]: (II) systemd-logind: got resume for 13:68
Mar 07 15:33:39 g5-5590 /usr/libexec/gdm-x-session[3489]: (II) systemd-logind: got resume for 13:72
Mar 07 15:33:39 g5-5590 /usr/libexec/gdm-x-session[3489]: (II) systemd-logind: got resume for 13:74
Mar 07 15:33:39 g5-5590 /usr/libexec/gdm-x-session[3489]: (II) systemd-logind: got resume for 13:75
Mar 07 15:33:39 g5-5590 /usr/libexec/gdm-x-session[3489]: (II) systemd-logind: got resume for 13:82
Mar 07 15:33:39 g5-5590 /usr/libexec/gdm-x-session[3489]: (II) systemd-logind: got resume for 13:77
Mar 07 15:33:39 g5-5590 /usr/libexec/gdm-x-session[3489]: (II) systemd-logind: got resume for 13:69
Mar 07 15:33:39 g5-5590 /usr/libexec/gdm-x-session[3489]: (II) systemd-logind: got resume for 13:67
Mar 07 15:33:39 g5-5590 /usr/libexec/gdm-x-session[3489]: (II) systemd-logind: got resume for 13:65
Mar 07 15:33:39 g5-5590 /usr/libexec/gdm-x-session[3489]: (II) systemd-logind: got resume for 13:76
Mar 07 15:33:39 g5-5590 /usr/libexec/gdm-x-session[3489]: (II) systemd-logind: got resume for 13:66
Mar 07 15:33:39 g5-5590 /usr/libexec/gdm-x-session[3489]: (II) systemd-logind: got resume for 226:0
Mar 07 15:33:39 g5-5590 systemd-logind[1241]: Operation 'sleep' finished.
Mar 07 15:33:39 g5-5590 audit[1190]: USER_AVC pid=1190 uid=102 auid=4294967295 ses=4294967295 subj=unconfined msg='apparmor="DENIED" operation="dbus_signal"  bus="system" path="/org/freedesktop/login1" interface="org.freedesktop.login1.Manager" member="PrepareForSleep" name=":1.22" mask="receive" pid=4231 label="snap.bitwarden.bitwarden" peer_pid=1241 peer_label="unconfined"
                                      exe="/usr/bin/dbus-daemon" sauid=102 hostname=? addr=? terminal=?'
Mar 07 15:33:39 g5-5590 ModemManager[1336]: <info>  [sleep-monitor-systemd] system is resuming
Mar 07 15:33:39 g5-5590 NetworkManager[1192]: <info>  [1709822019.2142] manager: sleep: wake requested (sleeping: yes  enabled: yes)
Mar 07 15:33:39 g5-5590 kernel: audit: type=1107 audit(1709822019.211:182): pid=1190 uid=102 auid=4294967295 ses=4294967295 subj=unconfined msg='apparmor="DENIED" operation="dbus_signal"  bus="system" path="/org/freedesktop/login1" interface="org.freedesktop.login1.Manager" member="PrepareForSleep" name=":1.22" mask="receive" pid=4231 label="snap.bitwarden.bitwarden" peer_pid=1241 peer_label="unconfined"
                                 exe="/usr/bin/dbus-daemon" sauid=102 hostname=? addr=? terminal=?'
Mar 07 15:33:39 g5-5590 /usr/libexec/gdm-x-session[3489]: (II) event2  - Sleep Button: is tagged by udev as: Keyboard
Mar 07 15:33:39 g5-5590 /usr/libexec/gdm-x-session[3489]: (II) event2  - Sleep Button: device is a keyboard
Mar 07 15:33:54 g5-5590 audit[1190]: USER_AVC pid=1190 uid=102 auid=4294967295 ses=4294967295 subj=unconfined msg='apparmor="DENIED" operation="dbus_signal"  bus="system" path="/org/freedesktop/login1" interface="org.freedesktop.login1.Manager" member="PrepareForSleep" name=":1.22" mask="receive" pid=4231 label="snap.bitwarden.bitwarden" peer_pid=1241 peer_label="unconfined"
                                      exe="/usr/bin/dbus-daemon" sauid=102 hostname=? addr=? terminal=?'
Mar 07 15:33:54 g5-5590 NetworkManager[1192]: <info>  [1709822034.3580] manager: sleep: sleep requested (sleeping: no  enabled: yes)
Mar 07 15:33:54 g5-5590 NetworkManager[1192]: <info>  [1709822034.3582] device (p2p-dev-wlo1): state change: disconnected -> unmanaged (reason 'sleeping', sys-iface-state: 'managed')
Mar 07 15:33:54 g5-5590 ModemManager[1336]: <info>  [sleep-monitor-systemd] system is about to suspend
Mar 07 15:33:54 g5-5590 NetworkManager[1192]: <info>  [1709822034.3585] manager: NetworkManager state is now ASLEEP
Mar 07 15:33:54 g5-5590 NetworkManager[1192]: <info>  [1709822034.3587] device (enp60s0): state change: activated -> deactivating (reason 'sleeping', sys-iface-state: 'managed')
Mar 07 15:33:54 g5-5590 NetworkManager[1192]: <info>  [1709822034.3595] device (wlo1): state change: activated -> deactivating (reason 'sleeping', sys-iface-state: 'managed')
Mar 07 15:33:54 g5-5590 kernel: audit: type=1107 audit(1709822034.355:183): pid=1190 uid=102 auid=4294967295 ses=4294967295 subj=unconfined msg='apparmor="DENIED" operation="dbus_signal"  bus="system" path="/org/freedesktop/login1" interface="org.freedesktop.login1.Manager" member="PrepareForSleep" name=":1.22" mask="receive" pid=4231 label="snap.bitwarden.bitwarden" peer_pid=1241 peer_label="unconfined"
                                 exe="/usr/bin/dbus-daemon" sauid=102 hostname=? addr=? terminal=?'
Mar 07 15:33:54 g5-5590 NetworkManager[1192]: <info>  [1709822034.3870] device (enp60s0): state change: deactivating -> disconnected (reason 'sleeping', sys-iface-state: 'managed')
Mar 07 15:33:54 g5-5590 NetworkManager[1192]: <info>  [1709822034.4194] device (enp60s0): state change: disconnected -> unmanaged (reason 'sleeping', sys-iface-state: 'managed')
Mar 07 15:33:54 g5-5590 NetworkManager[1192]: <info>  [1709822034.6095] device (wlo1): state change: deactivating -> disconnected (reason 'sleeping', sys-iface-state: 'managed')
Mar 07 15:33:54 g5-5590 NetworkManager[1192]: <info>  [1709822034.6795] device (wlo1): state change: disconnected -> unmanaged (reason 'sleeping', sys-iface-state: 'managed')
Mar 07 15:33:56 g5-5590 systemd[1]: Reached target Sleep.
Mar 07 15:33:56 g5-5590 systemd[1]: Starting NVIDIA system suspend actions...
Mar 07 15:33:56 g5-5590 suspend[6590]: nvidia-suspend.service
Mar 07 15:33:56 g5-5590 logger[6590]: <13>Mar  7 15:33:56 suspend: nvidia-suspend.service
Mar 07 15:33:56 g5-5590 /usr/libexec/gdm-x-session[3489]: (II) event2  - Sleep Button: device removed
Mar 07 15:33:56 g5-5590 /usr/libexec/gdm-x-session[3489]: (II) AIGLX: Suspending AIGLX clients for VT switch
Mar 07 15:33:56 g5-5590 systemd[1]: nvidia-suspend.service: Deactivated successfully.
Mar 07 15:33:56 g5-5590 systemd[1]: Finished NVIDIA system suspend actions.
Mar 07 15:33:56 g5-5590 systemd[1]: Starting System Suspend...
Mar 07 15:33:56 g5-5590 systemd-sleep[6627]: Entering sleep state 'suspend'...
Mar 07 15:33:56 g5-5590 kernel: PM: suspend entry (deep)
Mar 07 19:00:49 g5-5590 kernel: printk: Suspending console(s) (use no_console_suspend to debug)
Mar 07 19:00:49 g5-5590 kernel: ACPI: PM: Preparing to enter system sleep state S3
Mar 07 19:00:49 g5-5590 kernel: ACPI: PM: Low-level resume complete
Mar 07 19:00:49 g5-5590 kernel: ACPI: PM: Waking up from system sleep state S3
Mar 07 19:00:49 g5-5590 kernel: xhci_hcd 0000:3a:00.0: xHC error in resume, USBSTS 0x401, Reinit
Mar 07 19:00:49 g5-5590 kernel: xhci_hcd 0000:01:00.2: xHC error in resume, USBSTS 0x401, Reinit
Mar 07 19:00:50 g5-5590 systemd-sleep[6627]: System returned from sleep state.
Mar 07 19:00:50 g5-5590 bluetoothd[1527]: Controller resume with wake event 0x0
Mar 07 19:00:50 g5-5590 kernel: PM: suspend exit
Mar 07 19:00:50 g5-5590 systemd[1]: systemd-suspend.service: Deactivated successfully.
Mar 07 19:00:50 g5-5590 systemd[1]: Finished System Suspend.
Mar 07 19:00:50 g5-5590 systemd[1]: systemd-suspend.service: Consumed 1.728s CPU time.
Mar 07 19:00:50 g5-5590 systemd[1]: Stopped target Sleep.
Mar 07 19:00:50 g5-5590 systemd[1]: Reached target Suspend.
Mar 07 19:00:50 g5-5590 systemd[1]: Starting NVIDIA system resume actions...
Mar 07 19:00:50 g5-5590 systemd[1]: Stopped target Suspend.
Mar 07 19:00:50 g5-5590 suspend[7020]: nvidia-resume.service
Mar 07 19:00:50 g5-5590 logger[7020]: <13>Mar  7 19:00:50 suspend: nvidia-resume.service
Mar 07 19:00:50 g5-5590 systemd[1]: nvidia-resume.service: Deactivated successfully.
Mar 07 19:00:50 g5-5590 systemd[1]: Finished NVIDIA system resume actions.
Mar 07 19:00:51 g5-5590 systemd-logind[1241]: Operation 'sleep' finished.
Mar 07 19:00:51 g5-5590 audit[1190]: USER_AVC pid=1190 uid=102 auid=4294967295 ses=4294967295 subj=unconfined msg='apparmor="DENIED" operation="dbus_signal"  bus="system" path="/org/freedesktop/login1" interface="org.freedesktop.login1.Manager" member="PrepareForSleep" name=":1.22" mask="receive" pid=4231 label="snap.bitwarden.bitwarden" peer_pid=1241 peer_label="unconfined"
                                      exe="/usr/bin/dbus-daemon" sauid=102 hostname=? addr=? terminal=?'
Mar 07 19:00:51 g5-5590 NetworkManager[1192]: <info>  [1709834451.1310] manager: sleep: wake requested (sleeping: yes  enabled: yes)
Mar 07 19:00:51 g5-5590 ModemManager[1336]: <info>  [sleep-monitor-systemd] system is resuming
Mar 07 19:00:51 g5-5590 kernel: audit: type=1107 audit(1709834451.127:184): pid=1190 uid=102 auid=4294967295 ses=4294967295 subj=unconfined msg='apparmor="DENIED" operation="dbus_signal"  bus="system" path="/org/freedesktop/login1" interface="org.freedesktop.login1.Manager" member="PrepareForSleep" name=":1.22" mask="receive" pid=4231 label="snap.bitwarden.bitwarden" peer_pid=1241 peer_label="unconfined"
                                 exe="/usr/bin/dbus-daemon" sauid=102 hostname=? addr=? terminal=?'
Mar 07 19:02:11 g5-5590 systemd-logind[1241]: Suspend key pressed.
-- Boot c5f485dfcd42487f8c6be644d4882d45 --
Mar 07 19:03:07 g5-5590 kernel: Command line: BOOT_IMAGE=/boot/vmlinuz-6.5.0-21-generic root=UUID=b1baf06a-11df-4f46-b63d-d2c95c1c40a3 ro quiet splash mem_sleep_default=deep vt.handoff=7
Mar 07 19:03:07 g5-5590 kernel: Kernel command line: BOOT_IMAGE=/boot/vmlinuz-6.5.0-21-generic root=UUID=b1baf06a-11df-4f46-b63d-d2c95c1c40a3 ro quiet splash mem_sleep_default=deep vt.handoff=7
Mar 07 19:03:07 g5-5590 kernel: input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2
Mar 07 19:03:07 g5-5590 kernel: ACPI: button: Sleep Button [SBTN]
Mar 07 19:03:11 g5-5590 systemd-logind[1221]: Watching system buttons on /dev/input/event2 (Sleep Button)
Mar 07 19:03:12 g5-5590 systemd[1]: Starting Suspend/Resume Running libvirt Guests...
Mar 07 19:03:13 g5-5590 systemd[1]: Finished Suspend/Resume Running libvirt Guests.
Mar 07 19:03:14 g5-5590 /usr/libexec/gdm-x-session[2125]: Kernel command line: BOOT_IMAGE=/boot/vmlinuz-6.5.0-21-generic root=UUID=b1baf06a-11df-4f46-b63d-d2c95c1c40a3 ro quiet splash mem_sleep_default=deep vt.handoff=7
Mar 07 19:03:15 g5-5590 /usr/libexec/gdm-x-session[2125]: (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
Mar 07 19:03:15 g5-5590 /usr/libexec/gdm-x-session[2125]: (**) Sleep Button: Applying InputClass "libinput keyboard catchall"
Mar 07 19:03:15 g5-5590 /usr/libexec/gdm-x-session[2125]: (II) Using input driver 'libinput' for 'Sleep Button'
Mar 07 19:03:15 g5-5590 /usr/libexec/gdm-x-session[2125]: (**) Sleep Button: always reports core events
Mar 07 19:03:15 g5-5590 /usr/libexec/gdm-x-session[2125]: (II) event2  - Sleep Button: is tagged by udev as: Keyboard
Mar 07 19:03:15 g5-5590 /usr/libexec/gdm-x-session[2125]: (II) event2  - Sleep Button: device is a keyboard
Mar 07 19:03:15 g5-5590 /usr/libexec/gdm-x-session[2125]: (II) event2  - Sleep Button: device removed
Mar 07 19:03:15 g5-5590 /usr/libexec/gdm-x-session[2125]: (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 9)
Mar 07 19:03:15 g5-5590 /usr/libexec/gdm-x-session[2125]: (II) event2  - Sleep Button: is tagged by udev as: Keyboard
Mar 07 19:03:15 g5-5590 /usr/libexec/gdm-x-session[2125]: (II) event2  - Sleep Button: device is a keyboard
Mar 07 19:03:16 g5-5590 cups.cups-browsed[1284]: + sleep 1
Mar 07 19:03:17 g5-5590 cups.cups-browsed[2660]: + sleep 3600
Mar 07 19:03:35 g5-5590 /usr/libexec/gdm-x-session[2125]: (II) event2  - Sleep Button: device removed
Mar 07 19:03:35 g5-5590 /usr/libexec/gdm-x-session[2125]: (II) AIGLX: Suspending AIGLX clients for VT switch
Mar 07 19:03:36 g5-5590 kernel: xhci_hcd 0000:01:00.2: xHC error in resume, USBSTS 0x401, Reinit
Mar 07 19:03:37 g5-5590 /usr/libexec/gdm-x-session[3326]: Kernel command line: BOOT_IMAGE=/boot/vmlinuz-6.5.0-21-generic root=UUID=b1baf06a-11df-4f46-b63d-d2c95c1c40a3 ro quiet splash mem_sleep_default=deep vt.handoff=7
Mar 07 19:03:38 g5-5590 /usr/libexec/gdm-x-session[3326]: (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
Mar 07 19:03:38 g5-5590 /usr/libexec/gdm-x-session[3326]: (**) Sleep Button: Applying InputClass "libinput keyboard catchall"
Mar 07 19:03:38 g5-5590 /usr/libexec/gdm-x-session[3326]: (II) Using input driver 'libinput' for 'Sleep Button'
Mar 07 19:03:38 g5-5590 /usr/libexec/gdm-x-session[3326]: (**) Sleep Button: always reports core events
Mar 07 19:03:38 g5-5590 /usr/libexec/gdm-x-session[3326]: (II) event2  - Sleep Button: is tagged by udev as: Keyboard
Mar 07 19:03:38 g5-5590 /usr/libexec/gdm-x-session[3326]: (II) event2  - Sleep Button: device is a keyboard
Mar 07 19:03:38 g5-5590 /usr/libexec/gdm-x-session[3326]: (II) event2  - Sleep Button: device removed
Mar 07 19:03:38 g5-5590 /usr/libexec/gdm-x-session[3326]: (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 9)
Mar 07 19:03:38 g5-5590 /usr/libexec/gdm-x-session[3326]: (II) event2  - Sleep Button: is tagged by udev as: Keyboard
Mar 07 19:03:38 g5-5590 /usr/libexec/gdm-x-session[3326]: (II) event2  - Sleep Button: device is a keyboard
Mar 07 19:04:06 g5-5590 kernel: xhci_hcd 0000:01:00.2: xHC error in resume, USBSTS 0x401, Reinit
Mar 07 19:05:58 g5-5590 kernel: xhci_hcd 0000:01:00.2: xHC error in resume, USBSTS 0x401, Reinit

```

Thanks for your help,
Adrien!

---

### Post by deewens on 2024-03-11
up!

---

