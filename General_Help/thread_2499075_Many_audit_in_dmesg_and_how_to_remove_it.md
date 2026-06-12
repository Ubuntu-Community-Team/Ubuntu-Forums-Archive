---
title: "Many audit in dmesg and how to remove it"
date: 2024-07-10
forum: General Help
---

### Post by sz3bbyla on 2024-07-10
[B]I don't know where are from this messages, if must be supressed , and how to do it

[/B].....................................

4.816140] audit: type=1400 audit(1720643905.991:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="buildah" pid=914 comm="apparmor_parser"
[    4.816146] audit: type=1400 audit(1720643905.991:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="QtWebEngineProcess" pid=912 comm="apparmor_parser"
[    4.816148] audit: type=1400 audit(1720643905.991:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="brave" pid=913 comm="apparmor_parser"
[    4.816150] audit: type=1400 audit(1720643905.991:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="1password" pid=909 comm="apparmor_parser"
[    4.816152] audit: type=1400 audit(1720643905.991:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="busybox" pid=915 comm="apparmor_parser"
[    4.816153] audit: type=1400 audit(1720643905.991:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="cam" pid=916 comm="apparmor_parser"
[    4.816155] audit: type=1400 audit(1720643905.991:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name=4D6F6E676F444220436F6D70617373 pid=911 comm="apparmor_parser"
[    4.816156] audit: type=1400 audit(1720643905.991:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="Discord" pid=910 comm="apparmor_parser"
[    4.817133] audit: type=1400 audit(1720643905.993:10): apparmor="STATUS" operation="profile_load" profile="unconfined" name="ch-checkns" pid=918 comm="apparmor_parser"

..........................

[    5.279659] audit: type=1400 audit(1720643906.455:208): apparmor="STATUS" operation="profile_replace" info="same as current profile, skipping" profile="unconfined" name="rsyslogd" pid=1312 comm="apparmor_parser"
[    5.376026] audit: type=1400 audit(1720643906.552:209): apparmor="ALLOWED" operation="capable" class="cap" profile="/usr/sbin/sssd" pid=1300 comm="sssd" capability=12  capname="net_admin"
[    5.387844] block nvme0n1: No UUID available providing old NGUID
[    5.400047] audit: type=1400 audit(1720643906.576:210): apparmor="ALLOWED" operation="capable" class="cap" profile="/usr/sbin/sssd" pid=1427 comm="sssd_be" capability=12  capname="net_admin"
[    5.418922] audit: type=1400 audit(1720643906.595:211): apparmor="ALLOWED" operation="capable" class="cap" profile="/usr/sbin/sssd" pid=1300 comm="sssd" capability=12  capname="net_admin"

...........................
6.465748] audit: type=1400 audit(1720643907.642:214): apparmor="DENIED" operation="capable" class="cap" profile="/usr/lib/snapd/snap-confine" pid=1645 comm="snap-confine" capability=12  capname="net_admin"
[    6.465851] audit: type=1400 audit(1720643907.642:215): apparmor="DENIED" operation="capable" class="cap" profile="/usr/lib/snapd/snap-confine" pid=1645 comm="snap-confine" capability=38  capname="perfmon"
[    6.533014] audit: type=1400 audit(1720643907.709:216): apparmor="DENIED" operation="open" class="file" profile="snap-update-ns.canonical-livepatch" name="/usr/local/" pid=1701 comm="5" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
[    6.573291] audit: type=1400 audit(1720643907.749:217): apparmor="DENIED" operation="capable" class="cap" profile="/usr/lib/snapd/snap-confine" pid=1647 comm="snap-confine" capability=12  capname="net_admin"

.........................

[   13.417568] kauditd_printk_skb: 8 callbacks suppressed
[   13.417570] audit: type=1400 audit(1720643914.593:226): apparmor="DENIED" operation="capable" class="cap" profile="/usr/lib/snapd/snap-confine" pid=2385 comm="snap-confine" capability=12  capname="net_admin"
[   13.417574] audit: type=1400 audit(1720643914.593:227): apparmor="DENIED" operation="capable" class="cap" profile="/usr/lib/snapd/snap-confine" pid=2385 comm="snap-confine" capability=38  capname="perfmon"
[   13.420726] audit: type=1400 audit(1720643914.597:228): apparmor="DENIED" operation="open" class="file" profile="snap-update-ns.snapd-desktop-integration" name="/proc/2457/maps" pid=2457 comm="5" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
[   13.677969] rfkill: input handler enabled
[   16.029684] audit: type=1400 audit(1720643917.205:229): apparmor="DENIED" operation="capable" class="cap" profile="/usr/lib/snapd/snap-confine" pid=2767 comm="snap-confine" capability=12  capname="net_admin"
[   16.029690] audit: type=1400 audit(1720643917.206:230): apparmor="DENIED" operation="capable" class="cap" profile="/usr/lib/snapd/snap-confine" pid=2767 comm="snap-confine" capability=38  capname="perfmon"
[   16.032768] audit: type=1400 audit(1720643917.209:231): apparmor="DENIED" operation="open" class="file" profile="snap-update-ns.snapd-desktop-integration" name="/proc/2789/maps" pid=2789 comm="5" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
[   16.317038] audit: type=1326 audit(1720643917.493:232): auid=1000 uid=1000 gid=1000 ses=3 subj=snap.snapd-desktop-integration.snapd-desktop-integration pid=2823 comm="snapd-desktop-i" exe="/snap/snapd-desktop-integration/157/usr/bin/snapd-desktop-integration" sig=0 arch=c000003e syscall=203 compat=0 ip=0x7730a11de531 code=0x50000
[   16.317045] audit: type=1326 audit(1720643917.493:233): auid=1000 uid=1000 gid=1000 ses=3 subj=snap.snapd-desktop-integration.snapd-desktop-integration pid=2823 comm="snapd-desktop-i" exe="/snap/snapd-desktop-integration/157/usr/bin/snapd-desktop-integration" sig=0 arch=c000003e syscall=141 compat=0 ip=0x7730a125d78b code=0x50000
[   16.318702] audit: type=1326 audit(1720643917.495:234): auid=1000 uid=1000 gid=1000 ses=3 subj=snap.snapd-desktop-integration.snapd-desktop-integration pid=2823 comm="snapd-desktop-i" exe="/snap/snapd-desktop-integration/157/usr/bin/snapd-desktop-integration" sig=0 arch=c000003e syscall=203 compat=0 ip=0x7730a11de531 code=0x50000
[   16.318733] audit: type=1326 audit(1720643917.495:235): auid=1000 uid=1000 gid=1000 ses=3 subj=snap.snapd-desktop-integration.snapd-desktop-integration pid=2823 comm="snapd-desktop-i" exe="/snap/snapd-desktop-integration/157/usr/bin/snapd-desktop-integration" sig=0 arch=c000003e syscall=203 compat=0 ip=0x7730a11de531 code=0x50000

---

### Post by #&amp;thj^% on 2024-07-10
Check this post "Answer "  [https://askubuntu.com/questions/1336845/how-to-stop-apparmor-spew-in-the-logs](https://askubuntu.com/questions/1336845/how-to-stop-apparmor-spew-in-the-logs)

---

### Post by #&amp;thj^% on 2024-07-11
This really is not an easy task: [https://forum.snapcraft.io/t/suppressing-apparmor-denied-messages-on-ubuntu-core/24224](https://forum.snapcraft.io/t/suppressing-apparmor-denied-messages-on-ubuntu-core/24224)

But They are just audit messages. Even if you have installed the audit daemon, the kernel audit module still generates the messages.

However if you really want to suppress them, and I consider this just south of a nuclear approach.

I am not absolutely certain of the exact configuration used, but you might get away with just deleting  audit=1.  To check, you should find the compressed configuration file for the current Kernel at /proc/config.gz. If you open it into  text editor and search for 'audit', you will find which flags have been set.
So in short just add "audit=0" your kernel params via "/etc/default/grub"
ie:
```
sudoedit /etc/default/grub
```
Add just this "audit=0"
```

GRUB_CMDLINE_LINUX_DEFAULT='nowatchdog audit=0 nvme_load=YES zswap.enabled=0 splash quiet splash lo>
GRUB_CMDLINE_LINUX="lsm=landlock,lockdown,yama,integrity,apparmor,bpf nvidia-drm.modeset=1"

```
Now I don't see them anymore, And Please don't add everything you see in mine above just the "audit=0"
```

 sudo dmesg|grep audit
[sudo] password for me: 
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-linux-lts root=UUID=91ed2325-ef36-44cb-a2d1-0a6a42ce4a2b rw lsm=landlock,lockdown,yama,integrity,apparmor,bpf nvidia-drm.modeset=1 nowatchdog audit=0 nvme_load=YES zswap.enabled=0 splash quiet splash loglevel=3
[    0.029452] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-linux-lts root=UUID=91ed2325-ef36-44cb-a2d1-0a6a42ce4a2b rw lsm=landlock,lockdown,yama,integrity,apparmor,bpf nvidia-drm.modeset=1 nowatchdog audit=0 nvme_load=YES zswap.enabled=0 splash quiet splash loglevel=3
[    0.029512] audit: disabled (until reboot)
[   10.427239] systemd-journald[421]: Collecting audit messages is disabled.
```

---

### Post by sz3bbyla on 2024-07-15
I add audit=0 in [COLOR=#000000][FONT=&quot]GRUB_CMDLINE_LINUX_DEFAULT[/FONT][/COLOR] and no message now.
Swear this is ok on system to suppress this

---

### Post by #&amp;thj^% on 2024-07-15
> **sz3bbyla said:**
> I add audit=0 in [COLOR=#000000][FONT=&quot]GRUB_CMDLINE_LINUX_DEFAULT[/FONT][/COLOR] and no message now.
Swear this is ok on system to suppress this
It just stops seeing the messages.

I find seeing "Audits" at times, not always, but helpful in a corner case. 
Logging to /var/log/messages does happen at the same time as /var/log/messages. audit=0 will disable all audit logs. That shouldn't stop auditing though. 
Consider using **"auditctl -e 0"** also. This is the setting I use. **(But first remove "audit=0" from grub)**
Now I can when needed see audits ie:
```
 sudo dmesg|grep audit
[sudo] password for me: 
[    0.219002] audit: initializing netlink subsys (disabled)
[    0.219010] audit: type=2000 audit(1721071360.144:1): state=initialized audit_enabled=0 res=1
[   11.422637] systemd-journald[418]: Collecting audit messages is disabled.

```
That's just a short example on my call to see them.
```
systemctl status auditd
&#9675; auditd.service - Security Audit Logging Service
     Loaded: loaded (/usr/lib/systemd/system/auditd.service; disabled; preset: disabled)
     Active: inactive (dead)
       Docs: man:auditd(8)
             https://github.com/linux-audit/audit-documentation

```
EDIT: This is the last 6 lines of just plain "sudo dmesg"
```
[   35.675016] kauditd_printk_skb: 120 callbacks suppressed
[   35.675018] audit: type=1400 audit(1721074152.511:132): apparmor="DENIED" operation="mkdir" class="file" profile="ssh-agent" name="/tmp/ssh-XXXXXXIGvKBy/" pid=1076 comm="ssh-agent" requested_mask="c" denied_mask="c" fsuid=1000 ouid=1000
[   57.925418] warning: `conky' uses wireless extensions which will stop working for Wi-Fi 7 hardware; use nl80211

```
You may want that option over "audit=0"

---

