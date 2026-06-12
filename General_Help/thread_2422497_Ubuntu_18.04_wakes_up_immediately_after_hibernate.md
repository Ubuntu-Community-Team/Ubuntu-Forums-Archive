---
title: "Ubuntu 18.04 wakes up immediately after hibernate"
date: 2019-07-08
forum: General Help
---

### Post by Minilek on 2019-07-08
I followed the directions from Anthony O's answer at [https://askubuntu.com/questions/6769/hibernate-and-resume-from-a-swap-file](https://askubuntu.com/questions/6769/hibernate-and-resume-from-a-swap-file) for enabling hibernation in Ubuntu 18.04. Now when I do `sudo systemctl hibernate`, my system wakes up about a second later. How do I prevent this? I've tried disabling everything except the sleep button in /proc/acpi/wakeup to no avail. Anything else that I could be missing? EDIT: Here is the relevant part of /var/log/syslog:

> Jul  8 14:40:30 minilek-laptop NetworkManager[788]: <info>  [1562622030.9032] manager: sleep: sleep requested (sleeping: no  enabled: yes)
Jul  8 14:40:30 minilek-laptop NetworkManager[788]: <info>  [1562622030.9038] device (wlp2s0): state change: unavailable -> unmanaged (reason 'sleeping', sys-iface-state: 'managed')
Jul  8 14:40:30 minilek-laptop NetworkManager[788]: <info>  [1562622030.9052] manager: NetworkManager state is now ASLEEP
Jul  8 14:40:30 minilek-laptop gnome-shell[991]: Screen lock is locked down, not locking
Jul  8 14:40:30 minilek-laptop whoopsie[1428]: [14:40:30] offline
Jul  8 14:40:30 minilek-laptop gnome-shell[991]: Failed to set power save mode for output eDP-1: Permission denied
Jul  8 14:40:30 minilek-laptop gnome-shell[1421]: Object .Gjs_AppIndicatorIconActor__1 (0x55e30d074720), has been already finalized. Impossible to set any property to it.
Jul  8 14:40:30 minilek-laptop org.gnome.Shell.desktop[1421]: == Stack trace for context 0x55e308876340 ==
Jul  8 14:40:30 minilek-laptop org.gnome.Shell.desktop[1421]: #0 0x7fffc935fe70 I   resource:///org/gnome/gjs/modules/_legacy.js:83 (0x7f381c4b5de0 @ 87)
Jul  8 14:40:30 minilek-laptop org.gnome.Shell.desktop[1421]: #1 0x55e308c0b400 i   /usr/share/gnome-shell/extensions/ubuntu-appindicators@ubuntu.com/indicatorStatusIcon.js:93 (0x7f37f8eca4d8 @ 58)
Jul  8 14:40:30 minilek-laptop org.gnome.Shell.desktop[1421]: #2 0x7fffc9360a50 I   resource:///org/gnome/gjs/modules/_legacy.js:82 (0x7f381c4b5de0 @ 71)
Jul  8 14:40:30 minilek-laptop org.gnome.Shell.desktop[1421]: #3 0x7fffc9360b10 b   self-hosted:916 (0x7f381c4f12b8 @ 367)
Jul  8 14:40:30 minilek-laptop org.gnome.Shell.desktop[1421]: #4 0x7fffc9360c00 b   resource:///org/gnome/gjs/modules/signals.js:128 (0x7f381c4d2230 @ 386)
Jul  8 14:40:30 minilek-laptop org.gnome.Shell.desktop[1421]: #5 0x55e308c0b378 i   /usr/share/gnome-shell/extensions/ubuntu-appindicators@ubuntu.com/appIndicator.js:190 (0x7f37f8ebc1a8 @ 22)
Jul  8 14:40:30 minilek-laptop org.gnome.Shell.desktop[1421]: #6 0x7fffc9361850 I   resource:///org/gnome/gjs/modules/_legacy.js:82 (0x7f381c4b5de0 @ 71)
Jul  8 14:40:30 minilek-laptop org.gnome.Shell.desktop[1421]: #7 0x55e308c0b2d0 i   /usr/share/gnome-shell/extensions/ubuntu-appindicators@ubuntu.com/statusNotifierWatcher.js:219 (0x7f37f8eb6780 @ 225)
Jul  8 14:40:30 minilek-laptop org.gnome.Shell.desktop[1421]: #8 0x7fffc9362430 I   resource:///org/gnome/gjs/modules/_legacy.js:82 (0x7f381c4b5de0 @ 71)
Jul  8 14:40:30 minilek-laptop org.gnome.Shell.desktop[1421]: #9 0x55e308c0b258 i   /usr/share/gnome-shell/extensions/ubuntu-appindicators@ubuntu.com/extension.js:61 (0x7f37f8eafa28 @ 37)
Jul  8 14:40:30 minilek-laptop org.gnome.Shell.desktop[1421]: #10 0x55e308c0b198 i   resource:///org/gnome/shell/ui/extensionSystem.js:83 (0x7f381c2592b8 @ 441)
Jul  8 14:40:30 minilek-laptop org.gnome.Shell.desktop[1421]: #11 0x55e308c0b118 i   resource:///org/gnome/shell/ui/extensionSystem.js:354 (0x7f381c259d58 @ 13)
Jul  8 14:40:30 minilek-laptop org.gnome.Shell.desktop[1421]: #12 0x7fffc9363130 b   self-hosted:251 (0x7f381c4c4ab0 @ 223)
Jul  8 14:40:30 minilek-laptop org.gnome.Shell.desktop[1421]: #13 0x55e308c0b098 i   resource:///org/gnome/shell/ui/extensionSystem.js:353 (0x7f381c259cd0 @ 64)
Jul  8 14:40:30 minilek-laptop org.gnome.Shell.desktop[1421]: #14 0x55e308c0b018 i   resource:///org/gnome/shell/ui/extensionSystem.js:371 (0x7f381c259de0 @ 87)
Jul  8 14:40:30 minilek-laptop org.gnome.Shell.desktop[1421]: #15 0x7fffc9364630 b   resource:///org/gnome/gjs/modules/signals.js:128 (0x7f381c4d2230 @ 386)
Jul  8 14:40:30 minilek-laptop org.gnome.Shell.desktop[1421]: #16 0x7fffc9364e40 b   resource:///org/gnome/shell/ui/sessionMode.js:205 (0x7f37fad70120 @ 254)
Jul  8 14:40:30 minilek-laptop org.gnome.Shell.desktop[1421]: #17 0x7fffc9365b20 I   resource:///org/gnome/gjs/modules/_legacy.js:82 (0x7f381c4b5de0 @ 71)
Jul  8 14:40:30 minilek-laptop org.gnome.Shell.desktop[1421]: #18 0x55e308c0aed8 i   resource:///org/gnome/shell/ui/sessionMode.js:167 (0x7f37fad6ce68 @ 40)
Jul  8 14:40:30 minilek-laptop org.gnome.Shell.desktop[1421]: #19 0x7fffc9366700 I   resource:///org/gnome/gjs/modules/_legacy.js:82 (0x7f381c4b5de0 @ 71)
Jul  8 14:40:30 minilek-laptop org.gnome.Shell.desktop[1421]: #20 0x55e308c0ae30 i   resource:///org/gnome/shell/ui/screenShield.js:1282 (0x7f37fad52670 @ 188)
Jul  8 14:40:30 minilek-laptop org.gnome.Shell.desktop[1421]: #21 0x7fffc93672e0 I   resource:///org/gnome/gjs/modules/_legacy.js:82 (0x7f381c4b5de0 @ 71)
Jul  8 14:40:30 minilek-laptop org.gnome.Shell.desktop[1421]: #22 0x55e308c0ad80 i   resource:///org/gnome/shell/ui/screenShield.js:1331 (0x7f37fad526f8 @ 391)
Jul  8 14:40:30 minilek-laptop org.gnome.Shell.desktop[1421]: #23 0x7fffc9367ec0 I   resource:///org/gnome/gjs/modules/_legacy.js:82 (0x7f381c4b5de0 @ 71)
Jul  8 14:40:30 minilek-laptop org.gnome.Shell.desktop[1421]: #24 0x55e308c0acf8 i   resource:///org/gnome/shell/ui/screenShield.js:734 (0x7f37fad501a8 @ 57)
Jul  8 14:40:30 minilek-laptop org.gnome.Shell.desktop[1421]: #25 0x7fffc9368ab0 I   resource:///org/gnome/gjs/modules/_legacy.js:82 (0x7f381c4b5de0 @ 71)
Jul  8 14:40:30 minilek-laptop org.gnome.Shell.desktop[1421]: #26 0x7fffc9368b80 b   self-hosted:918 (0x7f381c4f12b8 @ 394)
Jul  8 14:40:30 minilek-laptop org.gnome.Shell.desktop[1421]: #27 0x7fffc9368c70 b   resource:///org/gnome/gjs/modules/signals.js:128 (0x7f381c4d2230 @ 386)
Jul  8 14:40:30 minilek-laptop org.gnome.Shell.desktop[1421]: #28 0x55e308c0ac60 i   resource:///org/gnome/shell/misc/loginManager.js:186 (0x7f381c212230 @ 92)
Jul  8 14:40:30 minilek-laptop org.gnome.Shell.desktop[1421]: #29 0x7fffc93698e0 I   resource:///org/gnome/gjs/modules/_legacy.js:82 (0x7f381c4b5de0 @ 71)
Jul  8 14:40:30 minilek-laptop org.gnome.Shell.desktop[1421]: #30 0x7fffc93699c0 b   self-hosted:920 (0x7f381c4f12b8 @ 428)
Jul  8 14:40:30 minilek-laptop org.gnome.Shell.desktop[1421]: #31 0x7fffc9369ac0 b   resource:///org/gnome/gjs/modules/signals.js:128 (0x7f381c4d2230 @ 386)
Jul  8 14:40:30 minilek-laptop org.gnome.Shell.desktop[1421]: #32 0x55e308c0abc0 i   resource:///org/gnome/gjs/modules/overrides/Gio.js:117 (0x7f381c4e0ab0 @ 39)
Jul  8 14:40:30 minilek-laptop gnome-shell[1421]: Object .Gjs_AppIndicatorIconActor__1 (0x55e30c39b340), has been already finalized. Impossible to set any property to it.
Jul  8 14:40:30 minilek-laptop org.gnome.Shell.desktop[1421]: == Stack trace for context 0x55e308876340 ==
Jul  8 14:40:30 minilek-laptop org.gnome.Shell.desktop[1421]: #0 0x7fffc935ff50 I   resource:///org/gnome/gjs/modules/_legacy.js:83 (0x7f381c4b5de0 @ 87)
Jul  8 14:40:30 minilek-laptop org.gnome.Shell.desktop[1421]: #1 0x55e308c0b400 i   /usr/share/gnome-shell/extensions/ubuntu-appindicators@ubuntu.com/indicatorStatusIcon.js:93 (0x7f37f8eca4d8 @ 58)
Jul  8 14:40:30 minilek-laptop org.gnome.Shell.desktop[1421]: #2 0x7fffc9360b30 I   resource:///org/gnome/gjs/modules/_legacy.js:82 (0x7f381c4b5de0 @ 71)
Jul  8 14:40:30 minilek-laptop org.gnome.Shell.desktop[1421]: #3 0x7fffc9360bf0 b   self-hosted:916 (0x7f381c4f12b8 @ 367)
Jul  8 14:40:30 minilek-laptop org.gnome.Shell.desktop[1421]: #4 0x7fffc9360c70 I   resource:///org/gnome/gjs/modules/signals.js:128 (0x7f381c4d2230 @ 386)
Jul  8 14:40:30 minilek-laptop org.gnome.Shell.desktop[1421]: #5 0x55e308c0b378 i   /usr/share/gnome-shell/extensions/ubuntu-appindicators@ubuntu.com/appIndicator.js:190 (0x7f37f8ebc1a8 @ 22)
Jul  8 14:40:30 minilek-laptop org.gnome.Shell.desktop[1421]: #6 0x7fffc9361850 I   resource:///org/gnome/gjs/modules/_legacy.js:82 (0x7f381c4b5de0 @ 71)
Jul  8 14:40:30 minilek-laptop org.gnome.Shell.desktop[1421]: #7 0x55e308c0b2d0 i   /usr/share/gnome-shell/extensions/ubuntu-appindicators@ubuntu.com/statusNotifierWatcher.js:219 (0x7f37f8eb6780 @ 225)
Jul  8 14:40:30 minilek-laptop org.gnome.Shell.desktop[1421]: #8 0x7fffc9362430 I   resource:///org/gnome/gjs/modules/_legacy.js:82 (0x7f381c4b5de0 @ 71)
Jul  8 14:40:30 minilek-laptop org.gnome.Shell.desktop[1421]: #9 0x55e308c0b258 i   /usr/share/gnome-shell/extensions/ubuntu-appindicators@ubuntu.com/extension.js:61 (0x7f37f8eafa28 @ 37)
Jul  8 14:40:30 minilek-laptop org.gnome.Shell.desktop[1421]: #10 0x55e308c0b198 i   resource:///org/gnome/shell/ui/extensionSystem.js:83 (0x7f381c2592b8 @ 441)
Jul  8 14:40:30 minilek-laptop org.gnome.Shell.desktop[1421]: #11 0x55e308c0b118 i   resource:///org/gnome/shell/ui/extensionSystem.js:354 (0x7f381c259d58 @ 13)
Jul  8 14:40:30 minilek-laptop org.gnome.Shell.desktop[1421]: #12 0x7fffc9363130 b   self-hosted:251 (0x7f381c4c4ab0 @ 223)
Jul  8 14:40:30 minilek-laptop org.gnome.Shell.desktop[1421]: #13 0x55e308c0b098 i   resource:///org/gnome/shell/ui/extensionSystem.js:353 (0x7f381c259cd0 @ 64)
Jul  8 14:40:30 minilek-laptop org.gnome.Shell.desktop[1421]: #14 0x55e308c0b018 i   resource:///org/gnome/shell/ui/extensionSystem.js:371 (0x7f381c259de0 @ 87)
Jul  8 14:40:30 minilek-laptop org.gnome.Shell.desktop[1421]: #15 0x7fffc9364630 b   resource:///org/gnome/gjs/modules/signals.js:128 (0x7f381c4d2230 @ 386)
Jul  8 14:40:30 minilek-laptop org.gnome.Shell.desktop[1421]: #16 0x7fffc9364e40 b   resource:///org/gnome/shell/ui/sessionMode.js:205 (0x7f37fad70120 @ 254)
Jul  8 14:40:30 minilek-laptop org.gnome.Shell.desktop[1421]: #17 0x7fffc9365b20 I   resource:///org/gnome/gjs/modules/_legacy.js:82 (0x7f381c4b5de0 @ 71)
Jul  8 14:40:30 minilek-laptop org.gnome.Shell.desktop[1421]: #18 0x55e308c0aed8 i   resource:///org/gnome/shell/ui/sessionMode.js:167 (0x7f37fad6ce68 @ 40)
Jul  8 14:40:30 minilek-laptop org.gnome.Shell.desktop[1421]: #19 0x7fffc9366700 I   resource:///org/gnome/gjs/modules/_legacy.js:82 (0x7f381c4b5de0 @ 71)
Jul  8 14:40:30 minilek-laptop org.gnome.Shell.desktop[1421]: #20 0x55e308c0ae30 i   resource:///org/gnome/shell/ui/screenShield.js:1282 (0x7f37fad52670 @ 188)
Jul  8 14:40:30 minilek-laptop org.gnome.Shell.desktop[1421]: #21 0x7fffc93672e0 I   resource:///org/gnome/gjs/modules/_legacy.js:82 (0x7f381c4b5de0 @ 71)
Jul  8 14:40:30 minilek-laptop org.gnome.Shell.desktop[1421]: #22 0x55e308c0ad80 i   resource:///org/gnome/shell/ui/screenShield.js:1331 (0x7f37fad526f8 @ 391)
Jul  8 14:40:30 minilek-laptop org.gnome.Shell.desktop[1421]: #23 0x7fffc9367ec0 I   resource:///org/gnome/gjs/modules/_legacy.js:82 (0x7f381c4b5de0 @ 71)
Jul  8 14:40:30 minilek-laptop org.gnome.Shell.desktop[1421]: #24 0x55e308c0acf8 i   resource:///org/gnome/shell/ui/screenShield.js:734 (0x7f37fad501a8 @ 57)
Jul  8 14:40:30 minilek-laptop org.gnome.Shell.desktop[1421]: #25 0x7fffc9368ab0 I   resource:///org/gnome/gjs/modules/_legacy.js:82 (0x7f381c4b5de0 @ 71)
Jul  8 14:40:30 minilek-laptop org.gnome.Shell.desktop[1421]: #26 0x7fffc9368b80 b   self-hosted:918 (0x7f381c4f12b8 @ 394)
Jul  8 14:40:30 minilek-laptop org.gnome.Shell.desktop[1421]: #27 0x7fffc9368c70 b   resource:///org/gnome/gjs/modules/signals.js:128 (0x7f381c4d2230 @ 386)
Jul  8 14:40:30 minilek-laptop org.gnome.Shell.desktop[1421]: #28 0x55e308c0ac60 i   resource:///org/gnome/shell/misc/loginManager.js:186 (0x7f381c212230 @ 92)
Jul  8 14:40:30 minilek-laptop org.gnome.Shell.desktop[1421]: #29 0x7fffc93698e0 I   resource:///org/gnome/gjs/modules/_legacy.js:82 (0x7f381c4b5de0 @ 71)
Jul  8 14:40:30 minilek-laptop org.gnome.Shell.desktop[1421]: #30 0x7fffc93699c0 b   self-hosted:920 (0x7f381c4f12b8 @ 428)
Jul  8 14:40:30 minilek-laptop org.gnome.Shell.desktop[1421]: #31 0x7fffc9369ac0 b   resource:///org/gnome/gjs/modules/signals.js:128 (0x7f381c4d2230 @ 386)
Jul  8 14:40:30 minilek-laptop org.gnome.Shell.desktop[1421]: #32 0x55e308c0abc0 i   resource:///org/gnome/gjs/modules/overrides/Gio.js:117 (0x7f381c4e0ab0 @ 39)
Jul  8 14:40:30 minilek-laptop gnome-shell[1421]: Object .Gjs_AppIndicatorIconActor__1 (0x55e30c324de0), has been already finalized. Impossible to set any property to it.
Jul  8 14:40:30 minilek-laptop org.gnome.Shell.desktop[1421]: == Stack trace for context 0x55e308876340 ==
Jul  8 14:40:30 minilek-laptop org.gnome.Shell.desktop[1421]: #0 0x7fffc935ff50 I   resource:///org/gnome/gjs/modules/_legacy.js:83 (0x7f381c4b5de0 @ 87)
Jul  8 14:40:30 minilek-laptop org.gnome.Shell.desktop[1421]: #1 0x55e308c0b400 i   /usr/share/gnome-shell/extensions/ubuntu-appindicators@ubuntu.com/indicatorStatusIcon.js:93 (0x7f37f8eca4d8 @ 58)
Jul  8 14:40:30 minilek-laptop org.gnome.Shell.desktop[1421]: #2 0x7fffc9360b30 I   resource:///org/gnome/gjs/modules/_legacy.js:82 (0x7f381c4b5de0 @ 71)
Jul  8 14:40:30 minilek-laptop org.gnome.Shell.desktop[1421]: #3 0x7fffc9360bf0 b   self-hosted:916 (0x7f381c4f12b8 @ 367)
Jul  8 14:40:30 minilek-laptop org.gnome.Shell.desktop[1421]: #4 0x7fffc9360c70 I   resource:///org/gnome/gjs/modules/signals.js:128 (0x7f381c4d2230 @ 386)
Jul  8 14:40:30 minilek-laptop org.gnome.Shell.desktop[1421]: #5 0x55e308c0b378 i   /usr/share/gnome-shell/extensions/ubuntu-appindicators@ubuntu.com/appIndicator.js:190 (0x7f37f8ebc1a8 @ 22)
Jul  8 14:40:30 minilek-laptop org.gnome.Shell.desktop[1421]: #6 0x7fffc9361850 I   resource:///org/gnome/gjs/modules/_legacy.js:82 (0x7f381c4b5de0 @ 71)
Jul  8 14:40:30 minilek-laptop org.gnome.Shell.desktop[1421]: #7 0x55e308c0b2d0 i   /usr/share/gnome-shell/extensions/ubuntu-appindicators@ubuntu.com/statusNotifierWatcher.js:219 (0x7f37f8eb6780 @ 225)
Jul  8 14:40:30 minilek-laptop org.gnome.Shell.desktop[1421]: #8 0x7fffc9362430 I   resource:///org/gnome/gjs/modules/_legacy.js:82 (0x7f381c4b5de0 @ 71)
Jul  8 14:40:30 minilek-laptop org.gnome.Shell.desktop[1421]: #9 0x55e308c0b258 i   /usr/share/gnome-shell/extensions/ubuntu-appindicators@ubuntu.com/extension.js:61 (0x7f37f8eafa28 @ 37)
Jul  8 14:40:30 minilek-laptop org.gnome.Shell.desktop[1421]: #10 0x55e308c0b198 i   resource:///org/gnome/shell/ui/extensionSystem.js:83 (0x7f381c2592b8 @ 441)
Jul  8 14:40:30 minilek-laptop org.gnome.Shell.desktop[1421]: #11 0x55e308c0b118 i   resource:///org/gnome/shell/ui/extensionSystem.js:354 (0x7f381c259d58 @ 13)
Jul  8 14:40:30 minilek-laptop org.gnome.Shell.desktop[1421]: #12 0x7fffc9363130 b   self-hosted:251 (0x7f381c4c4ab0 @ 223)
Jul  8 14:40:30 minilek-laptop org.gnome.Shell.desktop[1421]: #13 0x55e308c0b098 i   resource:///org/gnome/shell/ui/extensionSystem.js:353 (0x7f381c259cd0 @ 64)
Jul  8 14:40:30 minilek-laptop org.gnome.Shell.desktop[1421]: #14 0x55e308c0b018 i   resource:///org/gnome/shell/ui/extensionSystem.js:371 (0x7f381c259de0 @ 87)
Jul  8 14:40:30 minilek-laptop org.gnome.Shell.desktop[1421]: #15 0x7fffc9364630 b   resource:///org/gnome/gjs/modules/signals.js:128 (0x7f381c4d2230 @ 386)
Jul  8 14:40:30 minilek-laptop org.gnome.Shell.desktop[1421]: #16 0x7fffc9364e40 b   resource:///org/gnome/shell/ui/sessionMode.js:205 (0x7f37fad70120 @ 254)
Jul  8 14:40:30 minilek-laptop org.gnome.Shell.desktop[1421]: #17 0x7fffc9365b20 I   resource:///org/gnome/gjs/modules/_legacy.js:82 (0x7f381c4b5de0 @ 71)
Jul  8 14:40:30 minilek-laptop org.gnome.Shell.desktop[1421]: #18 0x55e308c0aed8 i   resource:///org/gnome/shell/ui/sessionMode.js:167 (0x7f37fad6ce68 @ 40)
Jul  8 14:40:30 minilek-laptop org.gnome.Shell.desktop[1421]: #19 0x7fffc9366700 I   resource:///org/gnome/gjs/modules/_legacy.js:82 (0x7f381c4b5de0 @ 71)
Jul  8 14:40:30 minilek-laptop org.gnome.Shell.desktop[1421]: #20 0x55e308c0ae30 i   resource:///org/gnome/shell/ui/screenShield.js:1282 (0x7f37fad52670 @ 188)
Jul  8 14:40:30 minilek-laptop org.gnome.Shell.desktop[1421]: #21 0x7fffc93672e0 I   resource:///org/gnome/gjs/modules/_legacy.js:82 (0x7f381c4b5de0 @ 71)
Jul  8 14:40:30 minilek-laptop org.gnome.Shell.desktop[1421]: #22 0x55e308c0ad80 i   resource:///org/gnome/shell/ui/screenShield.js:1331 (0x7f37fad526f8 @ 391)
Jul  8 14:40:30 minilek-laptop org.gnome.Shell.desktop[1421]: #23 0x7fffc9367ec0 I   resource:///org/gnome/gjs/modules/_legacy.js:82 (0x7f381c4b5de0 @ 71)
Jul  8 14:40:30 minilek-laptop org.gnome.Shell.desktop[1421]: #24 0x55e308c0acf8 i   resource:///org/gnome/shell/ui/screenShield.js:734 (0x7f37fad501a8 @ 57)
Jul  8 14:40:30 minilek-laptop org.gnome.Shell.desktop[1421]: #25 0x7fffc9368ab0 I   resource:///org/gnome/gjs/modules/_legacy.js:82 (0x7f381c4b5de0 @ 71)
Jul  8 14:40:30 minilek-laptop org.gnome.Shell.desktop[1421]: #26 0x7fffc9368b80 b   self-hosted:918 (0x7f381c4f12b8 @ 394)
Jul  8 14:40:30 minilek-laptop org.gnome.Shell.desktop[1421]: #27 0x7fffc9368c70 b   resource:///org/gnome/gjs/modules/signals.js:128 (0x7f381c4d2230 @ 386)
Jul  8 14:40:30 minilek-laptop org.gnome.Shell.desktop[1421]: #28 0x55e308c0ac60 i   resource:///org/gnome/shell/misc/loginManager.js:186 (0x7f381c212230 @ 92)
Jul  8 14:40:30 minilek-laptop org.gnome.Shell.desktop[1421]: #29 0x7fffc93698e0 I   resource:///org/gnome/gjs/modules/_legacy.js:82 (0x7f381c4b5de0 @ 71)
Jul  8 14:40:30 minilek-laptop org.gnome.Shell.desktop[1421]: #30 0x7fffc93699c0 b   self-hosted:920 (0x7f381c4f12b8 @ 428)
Jul  8 14:40:30 minilek-laptop org.gnome.Shell.desktop[1421]: #31 0x7fffc9369ac0 b   resource:///org/gnome/gjs/modules/signals.js:128 (0x7f381c4d2230 @ 386)
Jul  8 14:40:30 minilek-laptop org.gnome.Shell.desktop[1421]: #32 0x55e308c0abc0 i   resource:///org/gnome/gjs/modules/overrides/Gio.js:117 (0x7f381c4e0ab0 @ 39)
Jul  8 14:40:30 minilek-laptop gnome-software[2751]: no app for changed [email]ubuntu-appindicators@ubuntu.com[/email]
Jul  8 14:40:30 minilek-laptop gnome-software[2751]: no app for changed [email]ubuntu-dock@ubuntu.com[/email]
Jul  8 14:40:31 minilek-laptop gnome-shell[1421]: g_array_unref: assertion 'array' failed
Jul  8 14:40:31 minilek-laptop gnome-shell[1421]: message repeated 2 times: [ g_array_unref: assertion 'array' failed]
Jul  8 14:40:34 minilek-laptop systemd[1]: Reached target Sleep.
Jul  8 14:40:34 minilek-laptop systemd[1]: Starting Hibernate...
Jul  8 14:40:34 minilek-laptop run-parts[7673]: run-parts: executing /lib/systemd/system-sleep/hdparm pre
Jul  8 14:40:34 minilek-laptop run-parts[7673]: run-parts: executing /lib/systemd/system-sleep/unattended-upgrades pre
Jul  8 14:40:34 minilek-laptop s2disk[7676]: s2disk: Could not use the resume device (try swapon -a). Reason: No such device
Jul  8 14:40:34 minilek-laptop kernel: [ 1312.961716] thermal thermal_zone9: failed to read out thermal zone (-61)
Jul  8 14:40:34 minilek-laptop systemd[1]: systemd-hibernate.service: Main process exited, code=exited, status=19/n/a
Jul  8 14:40:34 minilek-laptop systemd[1]: systemd-hibernate.service: Failed with result 'exit-code'.
Jul  8 14:40:34 minilek-laptop systemd[1]: Failed to start Hibernate.
Jul  8 14:40:34 minilek-laptop systemd[1]: Dependency failed for Hibernate.
Jul  8 14:40:34 minilek-laptop systemd[1]: hibernate.target: Job hibernate.target/start failed with result 'dependency'.
Jul  8 14:40:34 minilek-laptop systemd[1]: sleep.target: Unit not needed anymore. Stopping.
Jul  8 14:40:34 minilek-laptop systemd[1]: Stopped target Sleep.
Jul  8 14:40:34 minilek-laptop NetworkManager[788]: <info>  [1562622034.3026] manager: sleep: wake requested (sleeping: yes  enabled: yes)
Jul  8 14:40:34 minilek-laptop NetworkManager[788]: <info>  [1562622034.3027] device (enp0s31f6): state change: unavailable -> unmanaged (reason 'sleeping', sys-iface-state: 'managed')
Jul  8 14:40:34 minilek-laptop gnome-shell[991]: Failed to set power save mode for output eDP-1: Permission denied
Jul  8 14:40:34 minilek-laptop kernel: [ 1313.147100] e1000e: enp0s31f6 NIC Link is Down
Jul  8 14:40:34 minilek-laptop NetworkManager[788]: <info>  [1562622034.4046] device (enx3495db2bdd51): state change: activated -> unmanaged (reason 'sleeping', sys-iface-state: 'managed')
Jul  8 14:40:34 minilek-laptop NetworkManager[788]: <info>  [1562622034.4699] dhcp4 (enx3495db2bdd51): canceled DHCP transaction, DHCP client pid 5998
Jul  8 14:40:34 minilek-laptop NetworkManager[788]: <info>  [1562622034.4700] dhcp4 (enx3495db2bdd51): state changed bound -> done
Jul  8 14:40:34 minilek-laptop avahi-daemon[776]: Withdrawing address record for 128.32.168.41 on enx3495db2bdd51.
Jul  8 14:40:34 minilek-laptop avahi-daemon[776]: Leaving mDNS multicast group on interface enx3495db2bdd51.IPv4 with address 128.32.168.41.
Jul  8 14:40:34 minilek-laptop avahi-daemon[776]: Interface enx3495db2bdd51.IPv4 no longer relevant for mDNS.
Jul  8 14:40:34 minilek-laptop avahi-daemon[776]: Withdrawing address record for fe80::6bc0:9a7b:c38a:554b on enx3495db2bdd51.
Jul  8 14:40:34 minilek-laptop avahi-daemon[776]: Leaving mDNS multicast group on interface enx3495db2bdd51.IPv6 with address fe80::6bc0:9a7b:c38a:554b.
Jul  8 14:40:34 minilek-laptop avahi-daemon[776]: Interface enx3495db2bdd51.IPv6 no longer relevant for mDNS.
Jul  8 14:40:34 minilek-laptop NetworkManager[788]: <info>  [1562622034.4776] manager: NetworkManager state is now CONNECTED_SITE
Jul  8 14:40:34 minilek-laptop NetworkManager[788]: <info>  [1562622034.4800] manager: NetworkManager state is now CONNECTED_LOCAL
Jul  8 14:40:34 minilek-laptop dbus-daemon[772]: [system] Activating via systemd: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service' requested by ':1.13' (uid=0 pid=788 comm="/usr/sbin/NetworkManager --no-daemon " label="unconfined")
Jul  8 14:40:34 minilek-laptop NetworkManager[788]: <info>  [1562622034.4848] manager: NetworkManager state is now DISCONNECTED
Jul  8 14:40:34 minilek-laptop systemd[1]: Starting Network Manager Script Dispatcher Service...
Jul  8 14:40:34 minilek-laptop NetworkManager[788]: <info>  [1562622034.4986] device (enp0s31f6): state change: unmanaged -> unavailable (reason 'managed', sys-iface-state: 'managed')
Jul  8 14:40:34 minilek-laptop kernel: [ 1313.242535] IPv6: ADDRCONF(NETDEV_UP): enp0s31f6: link is not ready
Jul  8 14:40:34 minilek-laptop dbus-daemon[772]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Jul  8 14:40:34 minilek-laptop systemd[1]: Started Network Manager Script Dispatcher Service.
Jul  8 14:40:34 minilek-laptop nm-dispatcher: req:1 'connectivity-change': new request (1 scripts)
Jul  8 14:40:34 minilek-laptop nm-dispatcher: req:1 'connectivity-change': start running ordered scripts...
Jul  8 14:40:34 minilek-laptop nm-dispatcher: req:2 'down' [enx3495db2bdd51]: new request (1 scripts)
Jul  8 14:40:34 minilek-laptop nm-dispatcher: req:2 'down' [enx3495db2bdd51]: start running ordered scripts...
Jul  8 14:40:34 minilek-laptop kernel: [ 1313.396522] [drm] Reducing the compressed framebuffer size. This may lead to less power savings than a non-reduced-size. Try to increase stolen memory size if available in BIOS.
Jul  8 14:40:34 minilek-laptop NetworkManager[788]: <info>  [1562622034.7189] device (enx3495db2bdd51): state change: unmanaged -> unavailable (reason 'managed', sys-iface-state: 'managed')
Jul  8 14:40:34 minilek-laptop kernel: [ 1313.460178] IPv6: ADDRCONF(NETDEV_UP): enp0s31f6: link is not ready
Jul  8 14:40:34 minilek-laptop kernel: [ 1313.462796] IPv6: ADDRCONF(NETDEV_UP): enx3495db2bdd51: link is not ready
Jul  8 14:40:35 minilek-laptop kernel: [ 1313.794342] IPv6: ADDRCONF(NETDEV_UP): enx3495db2bdd51: link is not ready
Jul  8 14:40:35 minilek-laptop NetworkManager[788]: <info>  [1562622035.0529] device (wlp2s0): state change: unmanaged -> unavailable (reason 'managed', sys-iface-state: 'managed')
Jul  8 14:40:35 minilek-laptop kernel: [ 1313.796871] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
Jul  8 14:40:35 minilek-laptop deja-dup-monito[3310]: Source ID 167 was not found when attempting to remove it
Jul  8 14:40:35 minilek-laptop gsd-sharing[1549]: Failed to StopUnit service: GDBus.Error:org.freedesktop.systemd1.NoSuchUnit: Unit gnome-user-share-webdav.service not loaded.
Jul  8 14:40:35 minilek-laptop gsd-sharing[1549]: Failed to StopUnit service: GDBus.Error:org.freedesktop.systemd1.NoSuchUnit: Unit rygel.service not loaded.
Jul  8 14:40:35 minilek-laptop gsd-sharing[1549]: Failed to StopUnit service: GDBus.Error:org.freedesktop.systemd1.NoSuchUnit: Unit gnome-remote-desktop.service not loaded.
Jul  8 14:40:35 minilek-laptop kernel: [ 1313.879878] ax88179_178a 2-2:1.0 enx3495db2bdd51: ax88179 - Link status is: 1
Jul  8 14:40:36 minilek-laptop ModemManager[787]: <info>  Couldn't check support for device '/sys/devices/pci0000:00/0000:00:14.0/usb2/2-2': not supported by any plugin
Jul  8 14:40:36 minilek-laptop ModemManager[787]: <info>  Couldn't check support for device '/sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0': not supported by any plugin
Jul  8 14:40:36 minilek-laptop ModemManager[787]: <info>  Couldn't check support for device '/sys/devices/pci0000:00/0000:00:1f.6': not supported by any plugin
Jul  8 14:40:37 minilek-laptop gnome-software[2751]: no app for changed [email]ubuntu-dock@ubuntu.com[/email]
Jul  8 14:40:37 minilek-laptop gnome-software[2751]: no app for changed [email]ubuntu-appindicators@ubuntu.com[/email]
Jul  8 14:40:37 minilek-laptop gvfsd-metadata[1751]: g_udev_device_has_property: assertion 'G_UDEV_IS_DEVICE (device)' failed
Jul  8 14:40:37 minilek-laptop gvfsd-metadata[1751]: g_udev_device_has_property: assertion 'G_UDEV_IS_DEVICE (device)' failed
Jul  8 14:40:37 minilek-laptop gnome-shell[1421]: [AppIndicatorSupport-DEBUG] Registering StatusNotifierItem :1.79/org/ayatana/NotificationItem/software_update_available
Jul  8 14:40:37 minilek-laptop gnome-shell[1421]: [AppIndicatorSupport-DEBUG] Registering StatusNotifierItem :1.79/org/ayatana/NotificationItem/livepatch
Jul  8 14:40:37 minilek-laptop gnome-shell[1421]: [AppIndicatorSupport-DEBUG] Registering StatusNotifierItem :1.71/org/ayatana/NotificationItem/dropbox_client_1651
Jul  8 14:40:37 minilek-laptop gnome-shell[1421]: [AppIndicatorSupport-WARN] Attempting to re-register :1.71/org/ayatana/NotificationItem/dropbox_client_1651; resetting instead
Jul  8 14:40:37 minilek-laptop gnome-shell[1421]: [AppIndicatorSupport-WARN] Item :1.71/org/ayatana/NotificationItem/dropbox_client_1651 is already registered
Jul  8 14:40:37 minilek-laptop gnome-shell[1421]: [AppIndicatorSupport-WARN] while calling AboutToShow: Gio.IOErrorEnum: Method 'com.canonical.dbusmenu.AboutToShow' returned type '()', but expected '(b)'
Jul  8 14:40:38 minilek-laptop kernel: [ 1317.207638] ax88179_178a 2-2:1.0 enx3495db2bdd51: ax88179 - Link status is: 1
Jul  8 14:40:38 minilek-laptop kernel: [ 1317.215191] IPv6: ADDRCONF(NETDEV_CHANGE): enx3495db2bdd51: link becomes ready
Jul  8 14:40:38 minilek-laptop NetworkManager[788]: <info>  [1562622038.4734] device (enx3495db2bdd51): carrier: link connected
Jul  8 14:40:38 minilek-laptop NetworkManager[788]: <info>  [1562622038.4766] device (enx3495db2bdd51): state change: unavailable -> disconnected (reason 'carrier-changed', sys-iface-state: 'managed')
Jul  8 14:40:38 minilek-laptop NetworkManager[788]: <info>  [1562622038.4789] policy: auto-activating connection 'Wired connection 2'
Jul  8 14:40:38 minilek-laptop NetworkManager[788]: <info>  [1562622038.4820] device (enx3495db2bdd51): Activation: starting connection 'Wired connection 2' (a961a878-d96e-375c-9244-fb03932d5280)
Jul  8 14:40:38 minilek-laptop NetworkManager[788]: <info>  [1562622038.4827] device (enx3495db2bdd51): state change: disconnected -> prepare (reason 'none', sys-iface-state: 'managed')
Jul  8 14:40:38 minilek-laptop NetworkManager[788]: <info>  [1562622038.4832] manager: NetworkManager state is now CONNECTING
Jul  8 14:40:38 minilek-laptop NetworkManager[788]: <info>  [1562622038.4843] device (enx3495db2bdd51): state change: prepare -> config (reason 'none', sys-iface-state: 'managed')
Jul  8 14:40:38 minilek-laptop NetworkManager[788]: <info>  [1562622038.4856] device (enx3495db2bdd51): state change: config -> ip-config (reason 'none', sys-iface-state: 'managed')
Jul  8 14:40:38 minilek-laptop NetworkManager[788]: <info>  [1562622038.4864] dhcp4 (enx3495db2bdd51): activation: beginning transaction (timeout in 45 seconds)
Jul  8 14:40:38 minilek-laptop NetworkManager[788]: <info>  [1562622038.4905] dhcp4 (enx3495db2bdd51): dhclient started with pid 7734
Jul  8 14:40:38 minilek-laptop avahi-daemon[776]: Joining mDNS multicast group on interface enx3495db2bdd51.IPv6 with address fe80::6bc0:9a7b:c38a:554b.
Jul  8 14:40:38 minilek-laptop avahi-daemon[776]: New relevant interface enx3495db2bdd51.IPv6 for mDNS.
Jul  8 14:40:38 minilek-laptop avahi-daemon[776]: Registering new address record for fe80::6bc0:9a7b:c38a:554b on enx3495db2bdd51.*.
Jul  8 14:40:38 minilek-laptop dhclient[7734]: DHCPREQUEST of 128.32.168.41 on enx3495db2bdd51 to 255.255.255.255 port 67 (xid=0x2d20c868)
Jul  8 14:40:38 minilek-laptop dhclient[7734]: DHCPACK of 128.32.168.41 from 169.229.60.65
Jul  8 14:40:38 minilek-laptop NetworkManager[788]: <info>  [1562622038.6075] dhcp4 (enx3495db2bdd51):   address 128.32.168.41
Jul  8 14:40:38 minilek-laptop NetworkManager[788]: <info>  [1562622038.6076] dhcp4 (enx3495db2bdd51):   plen 24 (255.255.255.0)
Jul  8 14:40:38 minilek-laptop NetworkManager[788]: <info>  [1562622038.6076] dhcp4 (enx3495db2bdd51):   gateway 128.32.168.1
Jul  8 14:40:38 minilek-laptop NetworkManager[788]: <info>  [1562622038.6077] dhcp4 (enx3495db2bdd51):   lease time 7200
Jul  8 14:40:38 minilek-laptop NetworkManager[788]: <info>  [1562622038.6077] dhcp4 (enx3495db2bdd51):   nameserver '128.32.168.23'
Jul  8 14:40:38 minilek-laptop NetworkManager[788]: <info>  [1562622038.6077] dhcp4 (enx3495db2bdd51):   nameserver '128.32.168.21'
Jul  8 14:40:38 minilek-laptop NetworkManager[788]: <info>  [1562622038.6078] dhcp4 (enx3495db2bdd51):   nameserver '128.32.206.12'
Jul  8 14:40:38 minilek-laptop NetworkManager[788]: <info>  [1562622038.6078] dhcp4 (enx3495db2bdd51):   domain name 'EECS.Berkeley.EDU'
Jul  8 14:40:38 minilek-laptop NetworkManager[788]: <info>  [1562622038.6078] dhcp (enx3495db2bdd51):   domain search 'EECS.Berkeley.EDU.'
Jul  8 14:40:38 minilek-laptop avahi-daemon[776]: Joining mDNS multicast group on interface enx3495db2bdd51.IPv4 with address 128.32.168.41.
Jul  8 14:40:38 minilek-laptop NetworkManager[788]: <info>  [1562622038.6079] dhcp (enx3495db2bdd51):   domain search 'CS.Berkeley.EDU.'
Jul  8 14:40:38 minilek-laptop NetworkManager[788]: <info>  [1562622038.6079] dhcp (enx3495db2bdd51):   domain search 'Banatao.Berkeley.EDU.'
Jul  8 14:40:38 minilek-laptop NetworkManager[788]: <info>  [1562622038.6079] dhcp (enx3495db2bdd51):   domain search 'Berkeley.EDU.'
Jul  8 14:40:38 minilek-laptop NetworkManager[788]: <info>  [1562622038.6079] dhcp4 (enx3495db2bdd51):   wins '169.229.60.182'
Jul  8 14:40:38 minilek-laptop NetworkManager[788]: <info>  [1562622038.6080] dhcp4 (enx3495db2bdd51):   wins '169.229.60.82'
Jul  8 14:40:38 minilek-laptop NetworkManager[788]: <info>  [1562622038.6080] dhcp4 (enx3495db2bdd51): state changed unknown -> bound
Jul  8 14:40:38 minilek-laptop avahi-daemon[776]: New relevant interface enx3495db2bdd51.IPv4 for mDNS.
Jul  8 14:40:38 minilek-laptop avahi-daemon[776]: Registering new address record for 128.32.168.41 on enx3495db2bdd51.IPv4.
Jul  8 14:40:38 minilek-laptop NetworkManager[788]: <info>  [1562622038.6179] device (enx3495db2bdd51): state change: ip-config -> ip-check (reason 'none', sys-iface-state: 'managed')
Jul  8 14:40:38 minilek-laptop whoopsie[1428]: [14:40:38] Cannot reach: [https://daisy.ubuntu.com](https://daisy.ubuntu.com)
Jul  8 14:40:38 minilek-laptop NetworkManager[788]: <info>  [1562622038.6210] device (enx3495db2bdd51): state change: ip-check -> secondaries (reason 'none', sys-iface-state: 'managed')
Jul  8 14:40:38 minilek-laptop NetworkManager[788]: <info>  [1562622038.6220] device (enx3495db2bdd51): state change: secondaries -> activated (reason 'none', sys-iface-state: 'managed')
Jul  8 14:40:38 minilek-laptop NetworkManager[788]: <info>  [1562622038.6226] manager: NetworkManager state is now CONNECTED_LOCAL
Jul  8 14:40:38 minilek-laptop dhclient[7734]: bound to 128.32.168.41 -- renewal in 3151 seconds.
Jul  8 14:40:38 minilek-laptop NetworkManager[788]: <info>  [1562622038.6300] manager: NetworkManager state is now CONNECTED_SITE
Jul  8 14:40:38 minilek-laptop NetworkManager[788]: <info>  [1562622038.6301] policy: set 'Wired connection 2' (enx3495db2bdd51) as default for IPv4 routing and DNS
Jul  8 14:40:38 minilek-laptop NetworkManager[788]: <info>  [1562622038.6308] device (enx3495db2bdd51): Activation: successful, device activated.
Jul  8 14:40:38 minilek-laptop nm-dispatcher: req:3 'up' [enx3495db2bdd51]: new request (1 scripts)
Jul  8 14:40:38 minilek-laptop nm-dispatcher: req:3 'up' [enx3495db2bdd51]: start running ordered scripts...
Jul  8 14:40:38 minilek-laptop gsd-sharing[1549]: Failed to StopUnit service: GDBus.Error:org.freedesktop.systemd1.NoSuchUnit: Unit gnome-user-share-webdav.service not loaded.
Jul  8 14:40:38 minilek-laptop gsd-sharing[1549]: Failed to StopUnit service: GDBus.Error:org.freedesktop.systemd1.NoSuchUnit: Unit rygel.service not loaded.
Jul  8 14:40:38 minilek-laptop gsd-sharing[1549]: Failed to StopUnit service: GDBus.Error:org.freedesktop.systemd1.NoSuchUnit: Unit gnome-remote-desktop.service not loaded.
Jul  8 14:40:39 minilek-laptop NetworkManager[788]: <info>  [1562622039.7187] manager: NetworkManager state is now CONNECTED_GLOBAL
Jul  8 14:40:39 minilek-laptop nm-dispatcher: req:4 'connectivity-change': new request (1 scripts)
Jul  8 14:40:39 minilek-laptop nm-dispatcher: req:4 'connectivity-change': start running ordered scripts...
Jul  8 14:40:39 minilek-laptop whoopsie[1428]: [14:40:39] The default IPv4 route is: /org/freedesktop/NetworkManager/ActiveConnection/5
Jul  8 14:40:39 minilek-laptop whoopsie[1428]: [14:40:39] Not a paid data plan: /org/freedesktop/NetworkManager/ActiveConnection/5
Jul  8 14:40:39 minilek-laptop whoopsie[1428]: [14:40:39] Found usable connection: /org/freedesktop/NetworkManager/ActiveConnection/5
Jul  8 14:40:41 minilek-laptop systemd-resolved[583]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Jul  8 14:40:41 minilek-laptop systemd-resolved[583]: message repeated 11 times: [ Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.]
Jul  8 14:40:41 minilek-laptop whoopsie[1428]: [14:40:41] online
Jul  8 14:40:43 minilek-laptop systemd-resolved[583]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Jul  8 14:40:43 minilek-laptop systemd-resolved[583]: message repeated 11 times: [ Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.]

This line stands out to me: "Jul 8 14:40:34 minilek-laptop s2disk[7676]: s2disk: Could not use the resume device (try swapon -a). Reason: No such device", but the swapfile is there when I do swapfile -s. I also updated /etc/default/grub and put the resume UUID and resume_offset as in Anthony O's response.

---

