---
title: "Problems launching Startup scripts - Ubuntu 18.04.1 LTS"
date: 2020-11-30
forum: General Help
---

### Post by securitydad on 2020-11-30
I have been reviewing different How To articles on using /etc/rc.local as well as the systemd compatible rc-local.service.  Neither of these are currently providing the service I am hoping for on startup.

The /etc/rc.local file is a  9 line script.  It appears to launch half of the scripts within the file, but does not complete them.  What could interrupt it?  (The /etc/rc.local file excutes flawlessly from the command line, and completes execution.)

The systemd rc-local.service reports the following:

&#9679; rc-local.service - /etc/rc.local Compatibility
   Loaded: loaded (/etc/systemd/system/rc-local.service; enabled-runtime; vendor preset: enabled)
  Drop-In: /lib/systemd/system/rc-local.service.d
           &#9492;&#9472;debian.conf
   Active: active (exited) since Mon 2020-11-30 16:56:00 EST; 33min ago
     Docs: man:systemd-rc-local-generator(8)
  Process: 2774 ExecStart=/etc/rc.local start (code=exited, status=0/SUCCESS)


Nov 30 16:55:59 itssafe-NUC7i5DNHE root[4976]: IPSet: es wget failed.
Nov 30 16:55:59 itssafe-NUC7i5DNHE root[4982]: IPSet: at wget failed.
Nov 30 16:55:59 itssafe-NUC7i5DNHE root[4994]: IPSet: lt wget failed.
...

The Three lines indicate that wget cannot retrieve remote file from the network.  I am using the following configuration:

#  SPDX-License-Identifier: LGPL-2.1+
#
#  This file is part of systemd.
#
#  systemd is free software; you can redistribute it and/or modify it
#  under the terms of the GNU Lesser General Public License as published by
#  the Free Software Foundation; either version 2.1 of the License, or
#  (at your option) any later version.


# This unit gets pulled automatically into multi-user.target by
# systemd-rc-local-generator if /etc/rc.local is executable.
[Unit]
Description=/etc/rc.local Compatibility
Documentation=man:systemd-rc-local-generator(8)
ConditionFileIsExecutable=/etc/rc.local


[Service]
Type=forking
ExecStart=/etc/rc.local start
TimeoutSec=0
RemainAfterExit=yes
GuessMainPID=no


[Install]
WantedBy=multi-user.target


Neither the /etc/rc.local or rc-local.service execute completely (or as in the case for the service,after the network is running).

How do I resolve this problem, and get the startup script to execute as it does after the workspace is available?

---

### Post by securitydad on 2020-11-30
It looks like both the /etc/rc.local and rc-local.service are being executed before the system is fully ready.  I have captured the output of the /etc/rc.local commands into individual log files, and while they have been touched, there is no output in the files.

---

