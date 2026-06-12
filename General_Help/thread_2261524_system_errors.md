---
title: "system errors"
date: 2015-01-19
forum: General Help
---

### Post by Seth-666 on 2015-01-19
i fiinded some errors that i don t understand ... can i resolve them ?

> kernel: [    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009ebff] usable
Jan 19 14:29:22 Seth-666 kernel: [    0.000000] BIOS-e820: [mem 0x000000000009ec00-0x000000000009ffff] reserved
Jan 19 14:29:22 Seth-666 kernel: [    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
Jan 19 14:29:22 Seth-666 kernel: [    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000deff4fff] usable
Jan 19 14:29:22 Seth-666 kernel: [    0.000000] BIOS-e820: [mem 0x00000000deff5000-0x00000000df07ffff] ACPI NVS
Jan 19 14:29:22 Seth-666 kernel: [    0.000000] BIOS-e820: [mem 0x00000000df080000-0x00000000df15afff] reserved
Jan 19 14:29:22 Seth-666 kernel: [    0.000000] BIOS-e820: [mem 0x00000000df15b000-0x00000000df162fff] ACPI data
Jan 19 14:29:22 Seth-666 kernel: [    0.000000] BIOS-e820: [mem 0x00000000df163000-0x00000000df2b5fff] reserved
Jan 19 14:29:22 Seth-666 kernel: [    0.000000] BIOS-e820: [mem 0x00000000df2b6000-0x00000000df2b6fff] ACPI NVS
Jan 19 14:29:22 Seth-666 kernel: [    0.000000] BIOS-e820: [mem 0x00000000df2b7000-0x00000000df2c6fff] reserved
Jan 19 14:29:22 Seth-666 kernel: [    0.000000] BIOS-e820: [mem 0x00000000df2c7000-0x00000000df2cdfff] ACPI NVS
Jan 19 14:29:22 Seth-666 kernel: [    0.000000] BIOS-e820: [mem 0x00000000df2ce000-0x00000000df2f4fff] reserved
Jan 19 14:29:22 Seth-666 kernel: [    0.000000] BIOS-e820: [mem 0x00000000df2f5000-0x00000000df4f7fff] ACPI NVS
Jan 19 14:29:22 Seth-666 kernel: [    0.000000] BIOS-e820: [mem 0x00000000df4f8000-0x00000000df783fff] usable
Jan 19 14:29:22 Seth-666 kernel: [    0.000000] BIOS-e820: [mem 0x00000000df784000-0x00000000dfef5fff] reserved
Jan 19 14:29:22 Seth-666 kernel: [    0.000000] BIOS-e820: [mem 0x00000000dfef6000-0x00000000dfefffff] usable
Jan 19 14:29:22 Seth-666 kernel: [    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
Jan 19 14:29:22 Seth-666 kernel: [    0.000000] BIOS-e820: [mem 0x00000000fec10000-0x00000000fec10fff] reserved
Jan 19 14:29:22 Seth-666 kernel: [    0.000000] BIOS-e820: [mem 0x00000000fec20000-0x00000000fec20fff] reserved
Jan 19 14:29:22 Seth-666 kernel: [    0.000000] BIOS-e820: [mem 0x00000000fed00000-0x00000000fed00fff] reserved
Jan 19 14:29:22 Seth-666 kernel: [    0.000000] BIOS-e820: [mem 0x00000000fed61000-0x00000000fed70fff] reserved
Jan 19 14:29:22 Seth-666 kernel: [    0.000000] BIOS-e820: [mem 0x00000000fed80000-0x00000000fed8ffff] reserved
Jan 19 14:29:22 Seth-666 kernel: [    0.000000] BIOS-e820: [mem 0x00000000fef00000-0x00000000ffffffff] reserved
Jan 19 14:29:22 Seth-666 kernel: [    0.000000] BIOS-e820: [mem 0x0000000100001000-0x000000021effffff] usable


s> ystemd-logind[32134]: New session c1 of user seth.
Jan 19 14:39:41 Seth-666 systemd-logind[32134]: Linked /tmp/.X11-unix/X0 to /run/user/1000/X11-display.
**Jan 19 14:42:41 Seth-666 compiz: PAM unable to dlopen(pam_kwallet.so): /lib/security/pam_kwallet.so: cannot open shared object file: No such file or directory**
Jan 19 14:42:41 Seth-666 compiz: PAM adding faulty module: pam_kwallet.so
Jan 19 14:42:41 Seth-666 compiz: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "seth"
Jan 19 14:42:45 Seth-666 pkexec: pam_unix(polkit-1:session): session opened for user root by (uid=1000)
Jan 19 14:42:45 Seth-666 pkexec[5685]: seth: Executing command [USER=root] [TTY=unknown] [CWD=/home/seth] [COMMAND=/usr/lib/update-notifier/package-system-locked]
Jan 19 14:48:29 Seth-666 compiz: gkr-pam: unlocked login keyring
Jan 19 14:48:34 Seth-666 polkitd(authority=local): Unregistered Authentication Agent for unix-session:c1 (system bus name :1.47, object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_US.UTF-8) (disconnected from bus)
Jan 19 14:48:34 Seth-666 systemd-logind[32134]: System is rebooting.

> systemd-logind[804]: New session c1 of user seth.
Jan 19 14:49:12 Seth-666 systemd-logind[804]: Linked /tmp/.X11-unix/X0 to /run/user/1000/X11-display.
Jan 19 14:49:14 Seth-666 gnome-keyring-daemon[1392]: **couldn't set environment variable in session: The name org.gnome.SessionManager was not provided by any .service files**
Jan 19 14:49:14 Seth-666 gnome-keyring-daemon[1392]: **message repeated 2 times: [ couldn't set environment variable in session: The name org.gnome.SessionManager was not provided by any .service files]**
Jan 19 14:49:17 Seth-666 gnome-keyring-daemon[1392]: The PKCS#11 component was already initialized
Jan 19 14:49:17 Seth-666 gnome-keyring-daemon[1392]: The GPG agent was already initialized
Jan 19 14:49:17 Seth-666 gnome-keyring-daemon[1392]: The SSH agent was already initialized
Jan 19 14:49:17 Seth-666 gnome-keyring-daemon[1392]: *_The Secret Service was already initialized_*


what is "The Secret Service was already initialized" ? i cant fiind out alone :(

Seth-666 kernel: [    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009ebff] usable
> Jan 19 14:29:22 Seth-666 kernel: [    0.000000] BIOS-e820: [mem 0x000000000009ec00-0x000000000009ffff] reserved
Jan 19 14:29:22 Seth-666 kernel: [    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
Jan 19 14:29:22 Seth-666 kernel: [    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000deff4fff] usable
Jan 19 14:29:22 Seth-666 kernel: [    0.000000] BIOS-e820: [mem 0x00000000deff5000-0x00000000df07ffff] ACPI NVS
Jan 19 14:29:22 Seth-666 kernel: [    0.000000] BIOS-e820: [mem 0x00000000df080000-0x00000000df15afff] reserved
Jan 19 14:29:22 Seth-666 kernel: [    0.000000] BIOS-e820: [mem 0x00000000df15b000-0x00000000df162fff] ACPI data
Jan 19 14:29:22 Seth-666 kernel: [    0.000000] BIOS-e820: [mem 0x00000000df163000-0x00000000df2b5fff] reserved
Jan 19 14:29:22 Seth-666 kernel: [    0.000000] BIOS-e820: [mem 0x00000000df2b6000-0x00000000df2b6fff] ACPI NVS
Jan 19 14:29:22 Seth-666 kernel: [    0.000000] BIOS-e820: [mem 0x00000000df2b7000-0x00000000df2c6fff] reserved
Jan 19 14:29:22 Seth-666 kernel: [    0.000000] BIOS-e820: [mem 0x00000000df2c7000-0x00000000df2cdfff] ACPI NVS
Jan 19 14:29:22 Seth-666 kernel: [    0.000000] BIOS-e820: [mem 0x00000000df2ce000-0x00000000df2f4fff] reserved
Jan 19 14:29:22 Seth-666 kernel: [    0.000000] BIOS-e820: [mem 0x00000000df2f5000-0x00000000df4f7fff] ACPI NVS
Jan 19 14:29:22 Seth-666 kernel: [    0.000000] BIOS-e820: [mem 0x00000000df4f8000-0x00000000df783fff] usable
Jan 19 14:29:22 Seth-666 kernel: [    0.000000] BIOS-e820: [mem 0x00000000df784000-0x00000000dfef5fff] reserved
Jan 19 14:29:22 Seth-666 kernel: [    0.000000] BIOS-e820: [mem 0x00000000dfef6000-0x00000000dfefffff] usable
Jan 19 14:29:22 Seth-666 kernel: [    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
Jan 19 14:29:22 Seth-666 kernel: [    0.000000] BIOS-e820: [mem 0x00000000fec10000-0x00000000fec10fff] reserved
Jan 19 14:29:22 Seth-666 kernel: [    0.000000] BIOS-e820: [mem 0x00000000fec20000-0x00000000fec20fff] reserved
Jan 19 14:29:22 Seth-666 kernel: [    0.000000] BIOS-e820: [mem 0x00000000fed00000-0x00000000fed00fff] reserved
Jan 19 14:29:22 Seth-666 kernel: [    0.000000] BIOS-e820: [mem 0x00000000fed61000-0x00000000fed70fff] reserved
Jan 19 14:29:22 Seth-666 kernel: [    0.000000] BIOS-e820: [mem 0x00000000fed80000-0x00000000fed8ffff] reserved
Jan 19 14:29:22 Seth-666 kernel: [    0.000000] BIOS-e820: [mem 0x00000000fef00000-0x00000000ffffffff] reserved
Jan 19 14:29:22 Seth-666 kernel: [    0.000000] BIOS-e820: [mem 0x0000000100001000-0x000000021effffff] usable

is this ok ? 

> Jan 19 19:26:56 Seth-666 NetworkManager[1072]: <info> (eth0): device state change: ip-config -> secondaries (reason 'none') [70 90 0]
Jan 19 19:26:56 Seth-666 NetworkManager[1072]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) complete.
Jan 19 19:26:56 Seth-666 NetworkManager[1072]: <info> (eth0): device state change: secondaries -> activated (reason 'none') [90 100 0]
Jan 19 19:26:56 Seth-666 NetworkManager[1072]: <info> NetworkManager state is now CONNECTED_GLOBAL
Jan 19 19:26:56 Seth-666 NetworkManager[1072]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Jan 19 19:26:56 Seth-666 NetworkManager[1072]: <info> DNS: starting dnsmasq...
Jan 19 19:26:56 Seth-666 NetworkManager[1072]: <warn> dnsmasq not available on the bus, can't update servers.
Jan 19 19:26:56 Seth-666 NetworkManager[1072]: <error> **[1421688416.652641] [nm-dns-dnsmasq.c:396] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name**
Jan 19 19:26:56 Seth-666 NetworkManager[1072]: <warn> DNS: plugin dnsmasq update failed
Jan 19 19:26:56 Seth-666 NetworkManager[1072]: <info> Writing DNS information to /sbin/resolvconf
Jan 19 19:26:56 Seth-666 dnsmasq[1153]: started, version 2.68 cache disabled


I am a new user :( pls help me understand

---

### Post by Holger_Gehrke on 2015-01-19
> 
[B]Jan 19 14:42:41 Seth-666 compiz: PAM unable to  dlopen(pam_kwallet.so): /lib/security/pam_kwallet.so: cannot open shared  object file: No such file or directory
[/B]
PAM = Plugable Authentication Module : A framework for checking identities. It's trying to load the KDE password safe and fails, probably because it is not installed.

> 
an 19 14:49:14 Seth-666 gnome-keyring-daemon[1392]: **couldn't set environment variable in session: The name org.gnome.SessionManager was not provided by any .service files**
Jan 19 14:49:14 Seth-666 gnome-keyring-daemon[1392]: **message repeated  2 times: [ couldn't set environment variable in session: The name  org.gnome.SessionManager was not provided by any .service files]**

The gnome-keyring-daemon is to gnome as kwallet is to KDE. It's trying to connect through dbus to the session manager, but nobody seems to be at home. If it had found the session manager, it would have set an environment-variable (so it could save itself the lookup on dbus if it needed it's services). Since I get that message all over my logs all the time and it's never the only thing wrong before something breaks, I'd say that's not a problem.

> 
Jan 19 14:49:17 Seth-666 gnome-keyring-daemon[1392]: *_The Secret Service was already initialized_*

The "Secret Service" is part of gnome-keyring. It stores passwords or other secret things in encrypted form. 

> 
Jan 19 19:26:56 Seth-666 NetworkManager[1072]: <error> [1421688416.652641] [nm-dns-dnsmasq.c:396] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name

The network manager is trying to start dnsmasq (a local dns-server and cache for dns-information) or connect to it (to tell it where to get dns-information to cache) but can't find it on dbus. Depending on whether or not dnsmasque is installed and / or configured this could be bad or not. At worst it will make looking up ip-adresses for names on the net a few ms slower.

So, all in all that's not too bad. Linux programs just love to complain about all the things that are not set up the way their authors think is the right one and will fill up one log file after the next. Unless something doesn't work at all or way to slow or gives obvious false results, I would not pay attention to any of these. Unless of course you are looking for a project to work on. Then any of these might be worth investigating and finding out more about them.

---

