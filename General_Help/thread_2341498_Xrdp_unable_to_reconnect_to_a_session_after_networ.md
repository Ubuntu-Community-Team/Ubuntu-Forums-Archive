---
title: "Xrdp unable to reconnect to a session after network cut off"
date: 2016-10-28
forum: General Help
---

### Post by Vladislav_Roussino on 2016-10-28
[LIST]
[*][FONT=arial]Observed under Ubuntu 14.04.[/FONT]
[*][FONT=arial]X11rdp installed using the X11rdp-o-matic script[/FONT]
[*][FONT=arial]Connect from a Windows 7 or 8 machine through a remote desktop connection[/FONT]
[/LIST]
[FONT=arial]X11rdp stores the session related files into /tmp/.xrdp directory. Once connected several socket files are created in the /tmp/.xrdp directory; once the user disconnects from the session if the sesman.ini is set to keep the session alive for the client to be able to resume working after he reconnects a file named xrdp_chanserv_session_xx is created into the /tmp/.xrdp directory. once the client reconnects to the given xx session this file is removed from the location.
However if the client's internet is cut off even for a second and he doesn't have the possibility to disconnect from the RDP session the mentioned xrdp_chanserv_session_xx file is not created. When the client tries to reconnect he only sees a grey screen. the xrdp session is never "released" automatically and the only way to reconnect to the X11rdp host is to restart either the xrdp service or the host by itself, in this way losing the initially created session.
i'm adding an extract of the xrdp.log showing how the client is trying to connect to the server and after several attempts it gives up due to the missing xrdp_chanserv_session_xx file.

> [20161017-11:08:30] [INFO ] lib_mod_log_peer: xrdp_pid=13421 connected to X11rdp_pid=3102 X11rdp_uid=1000 X11rdp_gid=1000 client_ip=192.168.1.201 client_port=49360
[20161017-11:08:31] [ERROR] xrdp_mm_connect_chansrv: connect failed trying again...
[20161017-11:08:31] [INFO ] An established connection closed to endpoint: NULL:NULL - socket: 13
[20161017-11:08:32] [ERROR] xrdp_mm_connect_chansrv: connect failed trying again...
[20161017-11:08:32] [INFO ] An established connection closed to endpoint: NULL:NULL - socket: 13
[20161017-11:08:33] [ERROR] xrdp_mm_connect_chansrv: connect failed trying again...
[20161017-11:08:33] [INFO ] An established connection closed to endpoint: NULL:NULL - socket: 13
[20161017-11:08:34] [ERROR] xrdp_mm_connect_chansrv: connect failed trying again...
[20161017-11:08:34] [ERROR] xrdp_mm_connect_chansrv: error intrans_connect chan
[20161017-11:08:34] [INFO ] An established connection closed to endpoint: 127.0.0.1:3350 - socket: 11
[20161017-11:08:36] [INFO ] An established connection closed to endpoint: 192.168.1.201:49360 - socket: 8
[20161017-11:08:36] [DEBUG] xrdp_mm_module_cleanup

How can i overcome this issue? Is there a way to forcefully "disconnect" a client in order for the needed socket file to be created?[/FONT]

---

