---
title: "suddenly cannot login to ubuntu anymore and solved mysteriously"
date: 2018-10-15
forum: General Help
---

### Post by monkeybrain20122 on 2018-10-15
Ubuntu 16.04. Something strange happened. Suddenly after a reboot I could no longer log into unity. The only package upgrade before the reboot was libsnmp, bazel and thunderbird, not likely to cause any issue. I tried the usual procedure with no avail : ctrl+alt+F1 to text mode then rename .Xauthority, .profile , .bashrc. 
.xsession-errors reads

```
openConnection: connect: No such file or directory
cannot connect to brltty at :0
upstart: bamfdaemon main process (1666) killed by TERM signal
upstart: hud main process (1862) killed by HUP signal
upstart: unity-settings-daemon main process (1864) killed by HUP signal
upstart: at-spi2-registryd main process (1870) killed by HUP signal
upstart: gnome-session (Unity) main process (1871) killed by HUP signal
upstart: system76-driver-hidpi main process (1883) killed by TERM signal
upstart: unity-panel-service main process (1887) killed by HUP signal
upstart: indicator-messages main process (1924) killed by HUP signal
upstart: indicator-bluetooth main process (1925) killed by TERM signal
upstart: indicator-power main process (1926) killed by TERM signal
upstart: indicator-datetime main process (1927) killed by TERM signal
upstart: indicator-keyboard main process (1930) killed by HUP signal
upstart: indicator-printers main process (1938) killed by TERM signal
upstart: indicator-session main process (1939) killed by TERM signal
upstart: indicator-application main process (1965) killed by TERM signal
upstart: unity7 main process (2049) terminated with status 1
upstart: Disconnected from notified D-Bus bus
```


But I could log into guest session. After logging into guest and logging  out I am able to login to my own user again. I rebooted several times  with no more problem.

The problem started mysteriously and then apparently fixed mysteriously. Any insight to what happened?

Thanks.

---

