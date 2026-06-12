---
title: "Ubuntu Lock-Up Completely (randomly)"
date: 2007-08-02
forum: General Help
---

### Post by PeTiNgA on 2007-08-02
Hi,
I'm using Ubuntu and sometimes (twice a week at least) my computer completely locks up, even the caps-lock won't turn on, only a hard reboot does the trick.

My specs are:

Abit NF7-S (nforce 2 chipset)
AMD Athlon (Thunderbird) 1400 MHz
Ralink RT2500 based wireless card
Gainward GF4 MX440

After some searching here in the forums, I though the problem could be my wireless card, so I removed it physically from my tower, but crashes still occur.

Tried with and without nvidia restricted drivers, it still crashes.

Windows XP works rock solid, I keep it running for months without a single crash.
Using diagnostic tools (memtest, s.m.a.r.t.) etc, all OK. CPU temp under 50º, and motherboard chipset under 40º under full load.

These are my logs (/etc/logs/syslog) before my last 2 system crashes)


```

**1st Log**

Jul 31 07:17:01 petinga-desktop /USR/SBIN/CRON[27828]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul 31 07:30:02 petinga-desktop /USR/SBIN/CRON[28144]: (root) CMD (test -x /etc/init.d/anacron && /usr/sbin/invoke-rc.d anacron start >/dev/null)
Jul 31 07:30:02 petinga-desktop anacron[28168]: Anacron 2.3 started on 2007-07-31
Jul 31 07:30:02 petinga-desktop anacron[28168]: Will run job `cron.daily' in 5 min.
Jul 31 07:30:02 petinga-desktop anacron[28168]: Jobs will be executed sequentially
Jul 31 07:35:02 petinga-desktop anacron[28168]: Job `cron.daily' started
Jul 31 07:35:02 petinga-desktop anacron[28295]: Updated timestamp for job `cron.daily' to 2007-07-31

**2nd Log**
Aug  2 23:43:15 petinga-desktop NetworkManager: <information>^IActivation (eth1) Stage 5 of 5 (IP Configure Commit) started... 
Aug  2 23:43:15 petinga-desktop avahi-daemon[4773]: Withdrawing address record for 192.168.1.64 on eth1.
Aug  2 23:43:15 petinga-desktop avahi-daemon[4773]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.1.64.
Aug  2 23:43:15 petinga-desktop avahi-daemon[4773]: Interface eth1.IPv4 no longer relevant for mDNS.
Aug  2 23:43:15 petinga-desktop avahi-daemon[4773]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.1.64.
Aug  2 23:43:15 petinga-desktop avahi-daemon[4773]: New relevant interface eth1.IPv4 for mDNS.
Aug  2 23:43:15 petinga-desktop avahi-daemon[4773]: Registering new address record for 192.168.1.64 on eth1.IPv4.
Aug  2 23:43:16 petinga-desktop NetworkManager: <information>^IClearing nscd hosts cache. 
Aug  2 23:43:16 petinga-desktop NetworkManager: <WARNING>^I nm_spawn_process (): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Aug  2 23:43:16 petinga-desktop NetworkManager: <information>^IActivation (eth1) successful, device activated. 
Aug  2 23:43:16 petinga-desktop NetworkManager: <information>^IActivation (eth1) Finish handler scheduled. 
Aug  2 23:43:16 petinga-desktop NetworkManager: <information>^IActivation (eth1) Stage 5 of 5 (IP Configure Commit) complete. 
Aug  2 23:43:17 petinga-desktop avahi-daemon[4773]: Registering new address record for fe80::248:54ff:fe81:82cb on eth1.*.
Aug  2 23:43:07 petinga-desktop ntpdate[6173]: step time server 82.211.81.145 offset -11.135784 sec
Aug  2 23:43:15 petinga-desktop kernel: [  541.118881] eth1: no IPv6 routers present
Aug  2 23:43:18 petinga-desktop gconfd (root-6194): starting (version 2.18.0.1), pid 6194 user 'root'
Aug  2 23:43:18 petinga-desktop gconfd (root-6194): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Aug  2 23:43:18 petinga-desktop gconfd (root-6194): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
Aug  2 23:43:18 petinga-desktop gconfd (root-6194): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Aug  2 23:43:18 petinga-desktop gconfd (root-6194): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Aug  2 23:43:18 petinga-desktop gconfd (root-6194): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Aug  2 23:43:48 petinga-desktop gconfd (root-6194): SIGHUP received, reloading all databases
Aug  2 23:43:48 petinga-desktop gconfd (root-6194): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Aug  2 23:43:48 petinga-desktop gconfd (root-6194): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
Aug  2 23:43:48 petinga-desktop gconfd (root-6194): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Aug  2 23:43:48 petinga-desktop gconfd (root-6194): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Aug  2 23:43:48 petinga-desktop gconfd (root-6194): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Aug  2 23:43:48 petinga-desktop gconfd (root-6194): GConf server is not in use, shutting down.
Aug  2 23:43:48 petinga-desktop gconfd (root-6194): Exiting
Aug  2 23:44:17 petinga-desktop gconfd (petinga-5120): Failed to send buffer

```

Any help would be appreciated, I really want to remove Windows from that computer and use Linux only, but so far I don't have the reliability I need.

Thanks in advance
;-)

---

### Post by fredj on 2007-08-02
When your computer locks up can you still move the cursor around or is that frozen as well.?
I have Linux installed on the same motherboard with an Athlon 2800 processor and it never freezes.

---

### Post by WastingBody on 2007-08-02
Thats happened to me once and thats it. Firefox used to crash like that in Windows for me. Is there anything that you are doing when it happens; such as were you using Firefox, listening to music, etc at the time of the crash?

---

### Post by PeTiNgA on 2007-08-02
Thanks for your promptly replies.

To fredj:
The cursor is frozen as well, network is down (can't ping, ssh etc).
But since you also have the same motherboard, I think I can rule that out.

To WastingBody:
I think that when using firefox, it's more likely to crash, but it could be only my imagination.
This week I left the computer without anything running, and It still crash.

Ruling everything out, It could be some problem with my gfx card, but still very hard to believe since it works OK in windows.

I've also tried Fedora and Debian before, and both of them crashed, Fedora much more though, at least once a day, Debian it's as stable as Ubuntu (as expected I think, since Ubuntu is debian based).
So the problem should lie on hardware or some drivers already included in kernel.

PS: I've reinstalled Ubuntu after removed my wireless card, to be sure that those drivers weren't loaded.

---

### Post by daniel_victoria on 2007-09-21
I'm seeing similar problems with my machine and prior to a crash I get the same gconfd resolved address message in syslog that PeTiNgA showed. Has anyone figured out what is going on?

---

