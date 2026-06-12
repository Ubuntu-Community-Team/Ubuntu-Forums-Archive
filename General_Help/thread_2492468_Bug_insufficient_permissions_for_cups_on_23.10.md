---
title: "Bug: insufficient permissions for cups on 23.10"
date: 2023-11-12
forum: General Help
---

### Post by kjerome on 2023-11-12
Hi everyone,
While setting up Ubuntu desktops for my co-workers I noticed a difference in behavior between 22.04 and 23.10.

On 22.04 I'm used to getting a popup to setup shared printers, but it doesn't seem to exist on 23.10.

Edit:
After some debugging, I've come to the conclusion that this feature should exist on 23.10, and that this is a permission bug!

What I've found is that the service that does this is called "cups-browsed", and by running it with "--debug" I found that it has insufficient permissions to "bind CUPS Browsing socket":
```

thomas@thomas-desktop:~$ cups-browsed --debug
Mon Nov 13 10:07:34 2023 140653717994240 Reading command line option --debug, turning on debug mode (Log on standard error).
Mon Nov 13 10:07:34 2023 140653717994240 cups-browsed version 2.0rc1 starting.
Mon Nov 13 10:07:34 2023 140653717994240 Reading config: BrowseRemoteProtocols dnssd cups
Mon Nov 13 10:07:34 2023 140653717994240 No "Browse..." line at all, accept all servers ("BrowseOrder Deny,Allow").
Mon Nov 13 10:07:34 2023 140653717994240 main() in THREAD 140653717994240
Mon Nov 13 10:07:34 2023 140653717994240 cups-browsed: Creating http  connection to local CUPS daemon via domain socket: /run/cups/cups.sock
Mon Nov 13 10:07:34 2023 140653717994240 update_netifs() in THREAD 140653717994240
Mon Nov 13 10:07:34 2023 140653717994240 Network interfaces: lo  (127.0.0.1, localhost), eth0 (192.168.0.48, thomas-desktop,  192.168.0.48*), lo (::1, ip6-localhost)
Mon Nov 13 10:07:34 2023 140653717994240 cups-browsed [BrowsePoll /run/cups/cups.sock:0]: IPP-Create-Subscription
Mon Nov 13 10:07:34 2023 140653717994240 cups-browsed [BrowsePoll /run/cups/cups.sock:0]: subscription ID=33
Mon Nov 13 10:07:34 2023 140653717994240 cups-browsed (): cupsEnumDests
Mon Nov 13 10:07:34 2023 140653717994240 Could not determine system default printer!
Mon Nov 13 10:07:34 2023 140653717994240 Using signal handler SIGACTION
Mon Nov 13 10:07:34 2023 140653717994240 Avahi server connection got available, setting up service browsers.
Mon Nov 13 10:07:34 2023 140653717994240 failed to bind CUPS Browsing socket: Permission denied
Mon Nov 13 10:07:34 2023 140653717994240 listening
Mon Nov 13 10:07:34 2023 140653717994240 browse_callback() in THREAD 140653717994240
Mon Nov 13 10:07:34 2023 140653717994240 Avahi Browser: CACHE_EXHAUSTED
Mon Nov 13 10:07:34 2023 140653717994240 browse_callback() in THREAD 140653717994240
Mon Nov 13 10:07:34 2023 140653717994240 Avahi Browser: ALL_FOR_NOW
Mon Nov 13 10:07:34 2023 140653717994240 browse_callback() in THREAD 140653717994240
Mon Nov 13 10:07:34 2023 140653717994240 Avahi Browser: CACHE_EXHAUSTED
Mon Nov 13 10:07:34 2023 140653717994240 browse_callback() in THREAD 140653717994240
Mon Nov 13 10:07:34 2023 140653717994240 Avahi Browser: ALL_FOR_NOW

```

I tried solving the problem by changing the "/etc/systemd/system/multi-user.target.wants/cups-browsed.service" file to run the service as root (original user was "cups-browsed"):
```

[Unit]
Description=Make remote CUPS printers available locally
Requires=cups.service
After=cups.service avahi-daemon.service network-online.target
Wants=avahi-daemon.service network-online.target

[Service]
ExecStart=/usr/sbin/cups-browsed
User=root

[Install]
WantedBy=multi-user.target

```

After changing this and rebooting I got the popup.

Does anyone have a better solution?
Where should I report this bug?

---

