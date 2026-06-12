---
title: "VNC Crash?"
date: 2008-01-25
forum: General Help
---

### Post by derekaug on 2008-01-25
Okay I was using VNC to connect to my home machine from work, everything was working all fine and dandy until I lose the connection. So I think, just reconnect right, wrong, no response all day when trying to connect. 

So I get home, to find my displays off and pc running like usual, only thing is it is totally unresponsive to anything (mouse, keyboard, power button). And thus I hard reboot it and all is well.

Here are my syslog from the time period from when I would of been connected to the point I lost my connection. The only thing I see is the APIC error which I'm not sure what is causing it.

```

Jan 25 07:46:08 daugustine-desktop hcid[5094]: Default authorization agent (:1.37, /org/bluez/auth) registered
Jan 25 07:46:10 daugustine-desktop NetworkManager: <info>  Updating allowed wireless network lists. 
Jan 25 07:46:10 daugustine-desktop NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
Jan 25 08:00:01 daugustine-desktop kernel: [  957.720318] APIC error on CPU0: 00(40)
Jan 25 08:05:29 daugustine-desktop kernel: [ 1285.521663] APIC error on CPU0: 40(40)
Jan 25 08:07:33 daugustine-desktop kernel: [ 1408.834366] APIC error on CPU0: 40(40)
Jan 25 08:08:17 daugustine-desktop kernel: [ 1452.907122] APIC error on CPU0: 40(40)
Jan 25 08:17:01 daugustine-desktop /USR/SBIN/CRON[6212]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jan 25 08:28:56 daugustine-desktop kernel: [ 2689.550869] APIC error on CPU0: 40(40)
Jan 25 08:44:50 daugustine-desktop -- MARK --
Jan 25 08:49:47 daugustine-desktop kernel: [ 3938.221716] APIC error on CPU0: 40(40)
Jan 25 09:04:50 daugustine-desktop -- MARK --

```

Thanks for the help in advance.

---

