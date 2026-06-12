---
title: "Browser problem after upgrades"
date: 2023-07-02
forum: General Help
---

### Post by pankaj13 on 2023-07-02
Hi,

I'm running Ubuntu 22.04.02 LTS and just applied some updates as recommended by the OS. SInce then my Brave browser (& all other browsers) stopped working and would not launch from the sidebar. While inspecting the logs (/var/log/syslog), I noticed following error when brave browser's icon is clicked:

```

Jul  1 22:53:24 192 systemd[2538]: Started Application launched by gnome-shell.
Jul  1 22:53:24 192 kernel: [ 2000.674804] audit: type=1400 audit(1688277204.763:272): apparmor="DENIED" operation="userns_create" class="namespace" info="User namespace creation restricted" error=-13 profile="unconfined" pid=9138 comm="brave" requested="userns_create" denied="userns_create"
Jul  1 22:53:24 192 brave-browser.desktop[9137]: [9138:9138:0701/225324.763612:FATAL:credentials.cc(127)] Check failed: . : Permission denied (13)
Jul  1 22:53:24 192 brave-browser.desktop[9137]: /usr/bin/brave-browser-stable: line 48:  9138 Trace/breakpoint trap   (core dumped) "$HERE/brave" "$@"

```

When I look under /etc/apparmore.d directory, there are no profiles (active or disabled) for Brave, here is the content of this directory:
```

adm@localhost:~# ls /etc/apparmor.d/
abi             local            tunables         usr.bin.tcpdump                          usr.lib.libreoffice.program.xpdfimport  usr.sbin.ippusbxd
abstractions    lsb_release      usr.bin.evince   usr.lib.libreoffice.program.oosplash     usr.lib.snapd.snap-confine.real         usr.sbin.ntpd
disable         nvidia_modprobe  usr.bin.firefox  usr.lib.libreoffice.program.senddoc      usr.sbin.cups-browsed                   usr.sbin.rsyslogd
force-complain  sbin.dhclient    usr.bin.man      usr.lib.libreoffice.program.soffice.bin  usr.sbin.cupsd                          usr.sbin.sssd



```

Any idea/pointers to fix this problem or investigate it further?
Thanks.

---

### Post by andreas-grundler on 2023-07-03
A workaround is the command

```
sudo sysctl -w kernel.apparmor_restrict_unprivileged_userns=0
```

However, this is disabled again after a reboot. This only works permanently if you add it to /etc/sysctl.conf the following line:

```
kernel.apparmor_restrict_unprivileged_userns=0
```

---

### Post by pankaj13 on 2023-07-03
Hi Andreas,

Thank you so much, it fixed the problem and saved me the trouble of re-installing the OS!!
Regards,

---

### Post by andreas-grundler on 2023-07-03
I doubt that a reinstallation would have made a difference. In all likelihood, the developers of Brave will update their packages to include an apparmor profile to fix the problem.

---

