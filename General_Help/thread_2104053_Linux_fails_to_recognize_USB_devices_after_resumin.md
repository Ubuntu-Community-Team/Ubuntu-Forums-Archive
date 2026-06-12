---
title: "Linux fails to recognize USB devices after resuming a suspended session"
date: 2013-01-11
forum: General Help
---

### Post by dewdrop_world on 2013-01-11
Since a recent system update (I'm not sure exactly which one, but I would guess the upgrade to 3.2.0-35-lowlatency is the most likely culprit), sporadically the system loses contact with my laptop's USB ports after suspending the session. That is:

[LIST=1]
[*]Use the machine, everything is working fine.
[*]Switch off the USB audio interface (M-Audio fast track pro).
[*]Suspend the session.
[*]Later, wake the machine up again. The USB keyboard is not responding. Also, if I turn on the M-Audio, it doesn't appear in lsusb.*
[*]Reboot, and everything works as it should.
[/LIST]

* The USB keyboard and M-Audio are plugged into different physical ports on the laptop. They aren't plugged into an external USB hub. This is why I suspect Linux has lost contact with USB in general, rather than a specific device or one specific port.

If this persists, I might have to check launchpad for bug reports (don't have time to do it now).

But I'm looking for a workaround. I really don't like rebooting -- I don't like the wear on the hard disk, and I don't like quitting all my applications and relaunching them. I used to be able to run Ubuntu for weeks on end with no reboots, but in the last week or so, I have to reboot every other day (if not more often).

Is there a kernel module I could remove and restart using modprobe? I already have to do this to get the m-audio to work:

```
sudo modprobe -r snd-usb-audio
sudo modprobe snd-usb-audio
```

Maybe there is something similar for the entire USB subsystem?

Hardware: MSI A6200
uname -a says: Linux dlm-A6200 3.2.0-35-lowlatency #34-Ubuntu SMP PREEMPT Tue Dec 18 18:12:15 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

TIA,
hjh

---

### Post by dewdrop_world on 2013-01-15
It just happened again.

Some possibly relevant bits from syslog:

```
Jan 16 09:18:41 dlm-A6200 kernel: [19078.814660] ehci_hcd 0000:00:1d.0: port 1 reset error -110
Jan 16 09:18:41 dlm-A6200 kernel: [19078.817150] ehci_hcd 0000:00:1d.0: port 1 reset error -110
Jan 16 09:18:41 dlm-A6200 kernel: [19078.819641] ehci_hcd 0000:00:1d.0: port 1 reset error -110
Jan 16 09:18:41 dlm-A6200 kernel: [19078.822145] ehci_hcd 0000:00:1d.0: port 1 reset error -110
Jan 16 09:18:41 dlm-A6200 kernel: [19078.824633] ehci_hcd 0000:00:1d.0: port 1 reset error -110
Jan 16 09:18:41 dlm-A6200 kernel: [19078.824657] hub 2-0:1.0: hub_port_status failed (err = -32)
```

Any ideas?

TIA-

---

### Post by dewdrop_world on 2013-01-16
And this morning, no problem -- and the ehci errors are not in the syslog. So they seem to be the cause, but I have no idea what they mean or how to prevent them.

Help?

---

