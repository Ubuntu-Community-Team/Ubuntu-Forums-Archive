---
title: "Vino-Server enabled but not listening on 5900"
date: 2014-09-03
forum: General Help
---

### Post by pythonjosh on 2014-09-03
Was working great and solid for a week, then rebooted today for software updates, now all services are up but not port 5900.
I had already changed the encryption setting back to what it was before 14.04 so that it worked again.
I've been googling since it happened and cannot seem to figure it out.

Command Outputs from Putty:
jish@mediadb:~$ sudo /usr/lib/vino/vino-server
error: XDG_RUNTIME_DIR not set in the environment.
Cannot open display:
Run 'vino-server --help' to see a full list of available command line options

jish@mediadb:~$ gconftool-2 -a /desktop/gnome/remote_access
 enabled = true
 alternative_port = 5999
 use_upnp = true
 prompt_enabled = false
 use_alternative_port = false
 vnc_password = ******
 authentication_methods = [vnc]

and in netstat there is no 5900.
What do I do next?

---

