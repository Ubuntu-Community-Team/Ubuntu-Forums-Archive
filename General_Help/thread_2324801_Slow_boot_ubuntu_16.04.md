---
title: "Slow boot ubuntu 16.04"
date: 2016-05-16
forum: General Help
---

### Post by Czarny8 on 2016-05-16
Boot ubuntu 16.04 takes me 20-25 seconds, maybe not that much but 2 times longer than 15.04. The problem is probably apparmor. Any suggestions what I can do with it?
systemd-analyze blame:

```

         11.858s apparmor.service
          5.931s NetworkManager-wait-online.service
          1.444s systemd-fsck@dev-disk-by\x2duuid-f1d80aeb\x2d9dc2\x2d4916\x2dab84\x2d840f434f295f.service
          1.049s systemd-fsck@dev-disk-by\x2duuid-074fa7fd\x2d15b5\x2d480b\x2d9247\x2ddd4cfa3f3325.service
           896ms systemd-fsck@dev-disk-by\x2duuid-b844937e\x2d560e\x2d4946\x2dbea0\x2d69a69c57b822.service
           608ms systemd-fsck@dev-disk-by\x2duuid-dc0d52c7\x2d9c0f\x2d4962\x2dbc4b\x2dec0329a69bd9.service
           498ms systemd-fsck@dev-disk-by\x2duuid-ae6ec5bf\x2d9c14\x2d4115\x2d89b0\x2d5e73e6871133.service
	.......



```


dmesg:


```

 4.279696] EXT4-fs (sdb2): mounted filesystem with ordered data mode. Opts: (null)
[    4.673766] EXT4-fs (sdb1): mounted filesystem with ordered data mode. Opts: (null)
[    4.700503] systemd-journald[268]: Received request to flush runtime journal from PID 1
[    5.622772] EXT4-fs (sdb4): mounted filesystem with ordered data mode. Opts: (null)
[    5.936253] EXT4-fs (sdb7): mounted filesystem with ordered data mode. Opts: (null)
[    5.991500] EXT4-fs (sdb6): mounted filesystem with ordered data mode. Opts: (null)
[   17.836097] audit: type=1400 audit(1463414821.669:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/ubuntu-core-launcher" pid=828 comm="apparmor_parser"
[   17.839280] audit: type=1400 audit(1463414821.673:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=825 comm="apparmor_parser"
[   17.839286] audit: type=1400 audit(1463414821.673:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=825 comm="apparmor_parser"
[   17.839290] audit: type=1400 audit(1463414821.673:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-helper" pid=825 comm="apparmor_parser"
[   17.839294] audit: type=1400 audit(1463414821.673:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=825 comm="apparmor_parser"
[   17.841001] audit: type=1400 audit(1463414821.673:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=824 comm="apparmor_parser"
[   17.841005] audit: type=1400 audit(1463414821.673:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session//chromium" pid=824 comm="apparmor_parser"

```


But after that I can't turn off the system, becouse its freeze on splash screen.

---

### Post by Karl_Hungus on 2016-06-10
I am getting very slow boot speeds:( my specs are as follows: 4790k, GTX970, gigabyte mobo, 32 GBs of DDR3 1600mhz, Samsung EVO850 SSD.

While running 14.04 I was booting up and shutting down in 2 seconds flat.:D


if anyone knows any tricks to get this thing booting faster I am all for it.:P

---

### Post by Karl_Hungus on 2016-06-13
slow-boot time got a tiny bit better with an update I am assuming.  (Edit: This problem came back real crazy after a reboot)




Thanks to everyone who contributes to Ubuntu, Debian, or the Kernel itself. whatever component is responsible for booting up.


**Still shuts down slow** (2 minutes) I will update when I find out what is causing this issue.

---

### Post by Karl_Hungus on 2016-06-20
I solved my 2 minute boot issue with manual driver installation of the most recent Nvidia binary file.

Boots are under 7 seconds now.


Don't enable enable driver the GUI method unless you want slow boots.



Thanks for trying everyone, In the end I solved the issue myself.

(Still long shutdown Ill create a new thread on that one I guess)

---

