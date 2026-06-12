---
title: "Script in udev not working correct"
date: 2019-01-10
forum: General Help
---

### Post by nchizhov on 2019-01-10
Ubuntu 18.04 Server

Have udev rule:
```
[COLOR=#000000][FONT=&quot]ACTION=="add", KERNEL=="sd[a-z][0-9]", SUBSYSTEM=="block", SUBSYSTEMS=="usb", RUN+="/opt/dw/scripts/connect.sh %k %E{ID_SERIAL_SHORT} %E{ID_FS_TYPE}"[/FONT][/COLOR]
```

Script connect.sh:
```
[COLOR=#000000][FONT=&quot]#!/bin/bash[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]echo "$1:$2:$3" > /opt/dw/scripts/log.txt[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]echo -e -n "connect:$1:$2:$3" > /dev/tcp/127.0.0.1/35000[/FONT][/COLOR]
```

I have daemon on this server, which listening tcp port 35000. If I run this script in console - all working fine, but when trying udev - part with `echo` writing correct to file, but echo to socket not executed at all (Script stops by timeout).

Same rule and script working correctly in Fedora

---

