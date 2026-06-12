---
title: "Should I reinstall Ubuntu server or try to fix it?"
date: 2024-11-03
forum: General Help
---

### Post by matelek on 2024-11-03
I recently replaced my asus motherboard and the intel cpu in my server for an asrock b450m-hdv r4.0 and a ryzen 3 3200G.


After that I tried turning the server on, but it can't boot so I can't ssh into it, sometimes it just keeps spitting out "dbus.service". And doesn't start any services. Should I reinstall or try to fix it?


the exact error is

```
[FAILED] Failed to start Unbound DNS server
and when I go to check the status with systemctl this is what I get
```

```

&#10060;unbound.service - Unbound DNS server
    Loaded: loaded (/lib/systemd/unbound.service; enabled)
    Active: failed (Result: exit-code) since Sat 2024-11-02 18:13:39 UTC; 10s ago
    Docs: man:unbound(8)
    Process: 2481 ExecStartPre=/usr/lib/unbound/package-helper chroot_setup (code=exited, status=0/SUCCESS)
    Process: 2484 ExecStartPre=/usr/lib/unbound/package-helper root_trust_anchor_update (code=exited, status=0/SUCCESS)
    Process: 2487 ExecStart=/usr/sbin/unbound -d -p $DAEMON_OPTS (code=exited, status=127)
    Process: 2488 ExecStopPost=/usr/sbin/unbound/package-helper chroot_teardown (code=exited, status=0/SUCCESS)
    Main PID: 2487 (code=exited, status=127)
    CPU: 21ms
Nov 02 18:13:39 snowball systemd[1]: unbound.service: Scheduled restart job, restart counter is at 5.
Nov 02 18:13:39 snowball systemd[1]: Stopped Unbound DNS server.
Nov 02 18:13:39 snowball systemd[1]: unbound.service: Start requested repeated too quickly.
Nov 02 18:13:39 snowball systemd[1]: unbound.service Failed with result 'exit-code'.
Nov 02 18:13:39 snowball systemd[1]: Failed to start Unbound DNS server.
    

```


Thx

---

### Post by aljames2 on 2024-11-03
If you mean, you disconnected your root install media from the old motherboard, and reconnected it to an AMD motherboard/CPU, then expecting your root install to boot is a long-shot.  I personally would not attempt to try to get that to work, others may have had success.  I would suggest to make sure you first have a verified backup on other media somewhere, and then do a fresh install.

---

