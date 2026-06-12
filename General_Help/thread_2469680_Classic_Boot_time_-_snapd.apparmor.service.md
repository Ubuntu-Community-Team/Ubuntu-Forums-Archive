---
title: "Classic Boot time - snapd.apparmor.service"
date: 2021-12-06
forum: General Help
---

### Post by yaminb on 2021-12-06
HI all,

I really want to get to the bottom of my boot time in ubuntu. I'm running 21.10, but this issue has been around for a while.
I recently installed win 11 on it's own ssd and it literally boots up in a few second (to the login).

My Ubuntu install is also on the same kind of SSD.
If I'm reading this right (and please correct me if I'm reading this wrong), the biggest time is here: 
                  &#9492;&#9472;sysinit.target @1min 30.447s
                    &#9492;&#9472;snapd.apparmor.service @1.404s +47ms
                      &#9492;&#9472;apparmor.service @1.295s +107ms

Something is happening between snapd.apparmor.service and sysinit.target that takes over 1 minute and 29 seconds?
Is this the correct way to read this?

```

systemd-analyze critical-chain 
The time when unit became active or started is printed after the "@" character.
The time the unit took to start is printed after the "+" character.

graphical.target @1min 37.805s
&#9492;&#9472;multi-user.target @1min 37.805s
  &#9492;&#9472;plymouth-quit-wait.service @1min 30.907s +6.897s
    &#9492;&#9472;systemd-user-sessions.service @1min 30.899s +3ms
      &#9492;&#9472;network.target @1min 30.870s
        &#9492;&#9472;NetworkManager.service @1min 30.484s +386ms
          &#9492;&#9472;dbus.service @1min 30.481s
            &#9492;&#9472;basic.target @1min 30.473s
              &#9492;&#9472;sockets.target @1min 30.473s
                &#9492;&#9472;cups.socket @1min 30.749s
                  &#9492;&#9472;sysinit.target @1min 30.447s
                    &#9492;&#9472;snapd.apparmor.service @1.404s +47ms
                      &#9492;&#9472;apparmor.service @1.295s +107ms
                        &#9492;&#9472;local-fs.target @1.266s
                          &#9492;&#9472;snap-docker-1125.mount @456ms +809ms
                            &#9492;&#9472;dev-loop15.device @1.266s +33ms

```


```

systemd-analyze blame
6.897s plymouth-quit-wait.service
3.589s NetworkManager-wait-online.service
2.754s snapd.service
2.657s logrotate.service
2.629s kdump-tools.service
2.619s networkd-dispatcher.service
2.595s man-db.service
1.059s fwupd.service
 809ms snap-docker-1125.mount
 719ms snap-gtk\x2dcommon\x2dthemes-1519.mount
 652ms snap-firefox-731.mount
 547ms snap-gtk2\x2dcommon\x2dthemes-13.mount
 543ms udisks2.service
 478ms snap-gnome\x2d3\x2d38\x2d2004-87.mount
 446ms dev-sdc2.device
 444ms snap-gnome\x2d3\x2d28\x2d1804-161.mount
 404ms accounts-daemon.service
 402ms polkit.service
 388ms avahi-daemon.service
 386ms NetworkManager.service
 372ms upower.service
 368ms power-profiles-daemon.service
 356ms switcheroo-control.service
 353ms thermald.service
 353ms wpa_supplicant.service
 352ms systemd-logind.service
 334ms snap-core20-1242.mount
 255ms snap-core18-2253.mount
 250ms systemd-journal-flush.service
 248ms cachefilesd.service
 208ms cups.service
 180ms dev-loop0.device
 145ms dev-loop2.device
 143ms dev-loop3.device


```

---

### Post by yaminb on 2021-12-06
lol. Don't you love it when you literally fix the problem as soon as you post it.
Issue was as I had upgraded my system to use SSDs, the old swap UUID was still being used.

Similar to this issue.
[https://ubuntuhandbook.org/index.php/2019/05/fix-slow-boot-ubuntu-18-04/](https://ubuntuhandbook.org/index.php/2019/05/fix-slow-boot-ubuntu-18-04/)

Problem solved, it boots in seconds now.

Big wait is gone.
> 
systemd-analyze critical-chain 
The time when unit became active or started is printed after the "@" character.
The time the unit took to start is printed after the "+" character.

graphical.target @8.787s
&#9492;&#9472;multi-user.target @8.787s
  &#9492;&#9472;plymouth-quit-wait.service @1.907s +6.879s
    &#9492;&#9472;systemd-user-sessions.service @1.901s +3ms
      &#9492;&#9472;network.target @1.895s
        &#9492;&#9472;wpa_supplicant.service @1.536s +354ms
          &#9492;&#9472;dbus.service @1.510s
            &#9492;&#9472;basic.target @1.506s
              &#9492;&#9472;sockets.target @1.506s
                &#9492;&#9472;snapd.socket @1.505s +458us
                  &#9492;&#9472;sysinit.target @1.500s
                    &#9492;&#9472;snapd.apparmor.service @1.452s +48ms
                      &#9492;&#9472;apparmor.service @1.364s +86ms
                        &#9492;&#9472;local-fs.target @1.336s
                          &#9492;&#9472;snap-dotnet\x2dsdk-146.mount @450ms +885ms
                            &#9492;&#9472;dev-loop15.device @1.335s +36ms




---

### Post by tea for one on 2021-12-06
> **yaminb said:**
> lol. Don't you love it when you literally fix the problem as soon as you post it.

Indeed, I do
Especially, when the fix is published here as a [COLOR="#0000FF"]Solved Thread[/COLOR] for the benefit of other users.
I'm sure this contribution will help somebody soon.

---

