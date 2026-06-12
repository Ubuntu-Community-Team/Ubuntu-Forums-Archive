---
title: "standby no longer works"
date: 2006-11-26
forum: General Help
---

### Post by gts on 2006-11-26
My laptop used to go in standby state without any problem, but since last week when I try to put it in standby state, but the result is only that the screen turns off for a few seconds. This is the output of a sleep.sh execution:

daniele@acer:/etc/acpi$ sudo ./sleep.sh
There is already a pid file /var/run/dhclient.eth1.pid with pid 7416
removed stale PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:04:23:83:49:c1
Sending on   LPF/eth1/00:04:23:83:49:c1
Sending on   Socket/fallback
DHCPRELEASE on eth1 to 172.0.0.1 port 67
 * Shutting down ALSA...                                                                                               [ ok ]
./sleep.sh: line 39: echo: write error: No such device
/etc/acpi/resume.d/15-video-post.sh: line 6:  7623 Floating point exceptionvbetool post
/etc/acpi/resume.d/17-video-restore.sh: line 5: /var/lib/acpi-support/vbestate: No such file or directory
Function not supported
ifup: interface eth1 already configured
 * Setting up ALSA...                                                                                                  [ ok ]
grep: /proc/acpi/fan/*/state: No such file or directory
FATAL: Module acpi_sbs not found.
FATAL: Module acpi_sbs not found.

I think that the problem is here:
"./sleep.sh: line 39: echo: write error: No such device"

line 39 is:

echo -n $ACPI_SLEEP_MODE >/sys/power/state

I've tried these commands:

cat /sys/power/state
mem disk

echo -n standby >/sys/power/state
echo: write error: No such device

Anybody out there with a solution?

thanks

Daniele

---

