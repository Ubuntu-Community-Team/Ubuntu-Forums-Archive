---
title: "Ubuntu 14.04 reboot problem"
date: 2017-07-20
forum: General Help
---

### Post by dove99 on 2017-07-20
I have a DELL Inspiron 15 7000 Series (7559), 128GB SSSD+ 1TB 5400 rpm Hard Drive and 6th Generation Intel Core i7-6700HQ Processor.
Recently we installed ubuntu 14.04, we upgraded it due to the wireless problem. After that it was ok to boot. However once the computer froze, 
we rebooted a few times. Since then, the computer was not able to reboot normally. We have to use grub, choose ubuntu option to reboot sometimes.
Most times we have to use recover mode in order to start the computer. The dmesg file shows some error message.  I copy and paste the error here.
Any suggestions what the problem is??

```
[   20.873369] nouveau E[   PFIFO][0000:02:00.0] SCHED_ERROR [ UNK06 ]
[   20.874427] nouveau E[   PFIFO][0000:02:00.0] SCHED_ERROR [ UNK06 ]
[   20.874846] audit: type=1400 audit(1500551810.630:10): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cups-browsed" pid=1025 comm="apparmor_parser"
[   20.875079] audit: type=1400 audit(1500551810.630:11): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=1021 comm="apparmor_parser"
[   20.875083] audit: type=1400 audit(1500551810.630:12): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1021 comm="apparmor_parser"
[   20.875086] audit: type=1400 audit(1500551810.630:13): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=1021 comm="apparmor_parser"
[   20.875500] nouveau E[   PFIFO][0000:02:00.0] SCHED_ERROR [ UNK06 ]
[   20.875570] audit: type=1400 audit(1500551810.630:14): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=1026 comm="apparmor_parser"
[   20.875575] audit: type=1400 audit(1500551810.630:15): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=1026 comm="apparmor_parser"
[   20.876559] nouveau E[   PFIFO][0000:02:00.0] SCHED_ERROR [ UNK06 ]
[   20.877753] nouveau E[   PFIFO][0000:02:00.0] SCHED_ERROR [ UNK06 ]
[   20.878958] nouveau E[   PFIFO][0000:02:00.0] SCHED_ERROR [ UNK06 ]
[   20.880174] nouveau E[   PFIFO][0000:02:00.0] SCHED_ERROR [ UNK06 ]
[   20.881305] nouveau E[   PFIFO][0000:02:00.0] SCHED_ERROR [ UNK06 ]
[   20.882422] nouveau E[   PFIFO][0000:02:00.0] SCHED_ERROR [ UNK06 ]
[   20.883565] nouveau E[   PFIFO][0000:02:00.0] SCHED_ERROR [ UNK06 ]
[   20.884594] audit: type=1400 audit(1500551810.638:16): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/tcpdump" pid=1028 comm="apparmor_parser"
[   20.884622] nouveau E[   PFIFO][0000:02:00.0] SCHED_ERROR [ UNK06 ]
[   20.885679] nouveau E[   PFIFO][0000:02:00.0] SCHED_ERROR [ UNK06 ]
[   20.885748] audit: type=1400 audit(1500551810.642:17): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=1020 comm="apparmor_parser"
[   20.885751] audit: type=1400 audit(1500551810.642:18): apparmor="STATUS" operation="profile_load" profile="unconfined" name="chromium" pid=1020 comm="apparmor_parser"
[   20.886824] nouveau E[   PFIFO][0000:02:00.0] SCHED_ERROR [ UNK06 ]
[   20.887952] nouveau E[   PFIFO][0000:02:00.0] SCHED_ERROR [ UNK06 ]
[   20.889011] nouveau E[   PFIFO][0000:02:00.0] SCHED_ERROR [ UNK06 ]
[   20.890069] nouveau E[   PFIFO][0000:02:00.0] SCHED_ERROR [ UNK06 ]
[   20.891126] nouveau E[   PFIFO][0000:02:00.0] SCHED_ERROR [ UNK06 ]
[   20.892184] nouveau E[   PFIFO][0000:02:00.0] SCHED_ERROR [ UNK06 ]
[   20.893239] nouveau E[   PFIFO][0000:02:00.0] SCHED_ERROR [ UNK06 ]
[   20.894000] audit: type=1400 audit(1500551810.650:19): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/telepathy/mission-control-5" pid=1024 comm="apparmor_parser"
[   20.894294] nouveau E[   PFIFO][0000:02:00.0] SCHED_ERROR [ UNK06 ]
[   20.895353] nouveau E[   PFIFO][0000:02:00.0] SCHED_ERROR [ UNK06 ]
[   20.896412] nouveau E[   PFIFO][0000:02:00.0] SCHED_ERROR [ UNK06 ]
[   20.897478] nouveau E[   PFIFO][0000:02:00.0] SCHED_ERROR [ UNK06 ]
[   20.898543] nouveau E[   PFIFO][0000:02:00.0] SCHED_ERROR [ UNK06 ]
[   20.899603] nouveau E[   PFIFO][0000:02:00.0] SCHED_ERROR [ UNK06 ]
[   20.900669] nouveau E[   PFIFO][0000:02:00.0] SCHED_ERROR [ UNK06 ]
[   20.901796] nouveau E[   PFIFO][0000:02:00.0] SCHED_ERROR [ UNK06 ]
[   20.902902] nouveau E[   PFIFO][0000:02:00.0] SCHED_ERROR [ UNK06 ]
[   20.903981] nouveau E[   PFIFO][0000:02:00.0] SCHED_ERROR [ UNK06 ]
[   20.905103] nouveau E[   PFIFO][0000:02:00.0] SCHED_ERROR [ UNK06 ]
[   20.906162] nouveau E[   PFIFO][0000:02:00.0] SCHED_ERROR [ UNK06 ]
[   20.907221] nouveau E[   PFIFO][0000:02:00.0] SCHED_ERROR [ UNK06 ]
[   20.908340] nouveau E[   PFIFO][0000:02:00.0] SCHED_ERROR [ UNK06 ]
[   20.909523] nouveau E[   PFIFO][0000:02:00.0] SCHED_ERROR [ UNK06 ]
[   20.910732] nouveau E[   PFIFO][0000:02:00.0] SCHED_ERROR [ UNK06 ]
[   20.911853] nouveau E[   PFIFO][0000:02:00.0] SCHED_ERROR [ UNK06 ]
[   20.912911] nouveau E[   PFIFO][0000:02:00.0] SCHED_ERROR [ UNK06 ]
[   20.914101] nouveau E[   PFIFO][0000:02:00.0] SCHED_ERROR [ UNK06 ]
[   20.915299] nouveau E[   PFIFO][0000:02:00.0] SCHED_ERROR [ UNK06 ]
[   20.916426] nouveau E[   PFIFO][0000:02:00.0] SCHED_ERROR [ UNK06 ]
[   20.917490] nouveau E[   PFIFO][0000:02:00.0] SCHED_ERROR [ UNK06 ]
[   20.918551] nouveau E[   PFIFO][0000:02:00.0] SCHED_ERROR [ UNK06 ]
[   20.919613] nouveau E[   PFIFO][0000:02:00.0] SCHED_ERROR [ UNK06 ]
[   20.920676] nouveau E[   PFIFO][0000:02:00.0] SCHED_ERROR [ UNK06 ]
[   20.921734] nouveau E[   PFIFO][0000:02:00.0] SCHED_ERROR [ UNK06 ]
[   20.922793] nouveau E[   PFIFO][0000:02:00.0] SCHED_ERROR [ UNK06 ]
[   20.923851] nouveau E[   PFIFO][0000:02:00.0] SCHED_ERROR [ UNK06 ]
[   20.924907] nouveau E[   PFIFO][0000:02:00.0] SCHED_ERROR [ UNK06 ]
[   20.925962] nouveau E[   PFIFO][0000:02:00.0] SCHED_ERROR [ UNK06 ]
[   20.927017] nouveau E[   PFIFO][0000:02:00.0] SCHED_ERROR [ UNK06 ]
[   20.928074] nouveau E[   PFIFO][0000:02:00.0] SCHED_ERROR [ UNK06 ]
[   20.928561] wlan0: authenticate with 48:5d:36:3d:42:14
[   20.929202] nouveau E[   PFIFO][0000:02:00.0] SCHED_ERROR [ UNK06 ]
[   20.930267] nouveau E[   PFIFO][0000:02:00.0] SCHED_ERROR [ UNK06 ]
[   20.931523] nouveau E[   PFIFO][0000:02:00.0] SCHED_ERROR [ UNK06 ]
[   20.932602] nouveau E[   PFIFO][0000:02:00.0] SCHED_ERROR [ UNK06 ]
[   20.933659] nouveau E[   PFIFO][0000:02:00.0] SCHED_ERROR [ UNK06 ]
[   20.934801] nouveau E[   PFIFO][0000:02:00.0] SCHED_ERROR [ UNK06 ]
[   20.935875] nouveau E[   PFIFO][0000:02:00.0] SCHED_ERROR [ UNK06 ]
[   20.937024] nouveau E[   PFIFO][0000:02:00.0] SCHED_ERROR [ UNK06 ]
[   20.938082] nouveau E[   PFIFO][0000:02:00.0] SCHED_ERROR [ UNK06 ]
[   20.938779] wlan0: send auth to 48:5d:36:3d:42:14 (try 1/3)
[   20.939140] nouveau E[   PFIFO][0000:02:00.0] SCHED_ERROR [ UNK06 ]
[   20.940199] nouveau E[   PFIFO][0000:02:00.0] SCHED_ERROR [ UNK06 ]
[   20.941324] nouveau E[   PFIFO][0000:02:00.0] SCHED_ERROR [ UNK06 ]
[   20.942450] nouveau E[   PFIFO][0000:02:00.0] SCHED_ERROR [ UNK06 ]
[   20.943563] nouveau E[   PFIFO][0000:02:00.0] SCHED_ERROR [ UNK06 ]
[   20.944702] nouveau E[   PFIFO][0000:02:00.0] SCHED_ERROR [ UNK06 ]
[   20.945830] nouveau E[   PFIFO][0000:02:00.0] SCHED_ERROR [ UNK06 ]
[   20.946958] nouveau E[   PFIFO][0000:02:00.0] SCHED_ERROR [ UNK06 ]
[   20.948086] nouveau E[   PFIFO][0000:02:00.0] SCHED_ERROR [ UNK06 ]
[   20.949220] nouveau E[   PFIFO][0000:02:00.0] SCHED_ERROR [ UNK06 ]
[   20.950346] nouveau E[   PFIFO][0000:02:00.0] SCHED_ERROR [ UNK06 ]
[   20.951403] nouveau E[   PFIFO][0000:02:00.0] SCHED_ERROR [ UNK06 ]
[   20.952462] nouveau E[   PFIFO][0000:02:00.0] SCHED_ERROR [ UNK06 ]
[   20.953520] nouveau E[   PFIFO][0000:02:00.0] SCHED_ERROR [ UNK06 ]
[   20.954578] nouveau E[   PFIFO][0000:02:00.0] SCHED_ERROR [ UNK06 ]
[   20.955637] nouveau E[   PFIFO][0000:02:00.0] SCHED_ERROR [ UNK06 ]
[   20.956695] nouveau E[   PFIFO][0000:02:00.0] SCHED_ERROR [ UNK06 ]
[   20.957765] nouveau E[   PFIFO][0000:02:00.0] SCHED_ERROR [ UNK06 ]
[   20.958880] nouveau E[   PFIFO][0000:02:00.0] SCHED_ERROR [ UNK06 ]
[   20.959938] nouveau E[   PFIFO][0000:02:00.0] SCHED_ERROR [ UNK06 ]
[   20.960996] nouveau E[   PFIFO][0000:02:00.0] SCHED_ERROR [ UNK06 ]
[   20.962055] nouveau E[   PFIFO][0000:02:00.0] SCHED_ERROR [ UNK06 ]
[   20.963113] nouveau E[   PFIFO][0000:02:00.0] SCHED_ERROR [ UNK06 ]
[   20.964187] nouveau E[   PFIFO][0000:02:00.0] SCHED_ERROR [
```

---

### Post by Bashing-om on 2017-07-20
dove99; Hello '

No video card installed ? No graphic's driver loaded ?
Post back the results - Between code tags - of terminal commands:
```

lspci -nnk | grep -iA3 vga
sudo lshw -C display

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
To see what we have to work with .

[INDENT][INDENT]kernel has got to have that interface
[/INDENT][/INDENT]

---

