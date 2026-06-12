---
title: "PolicyKit daemon disconnected from the bus."
date: 2018-06-03
forum: General Help
---

### Post by eternalnight on 2018-06-03
Hello all,

Hopefully this will be a quick fix, but I have been having a consistent error whenever I try and start a service on my 16.04 machine. 

Whether it be ssh, rdp or apache2, whenever i try and launch the service using the basic command service ssh start for example I am greeted by an error message in my terminal saying the following:

PolicyKit daemon disconnected from the bus.
We are no longer a registered authentication agent.
Failed to start ssh.service: Message recipient disconnected from message bus without replying
See system logs and 'systemctl status ssh.service' for details.

Running the command with a "sudo" in front of it seems to fix this issue for ssh, and it seems to "work" at first for the other services on my machine. However upon trying to connect to my webserver or my remote desktop service I am simply unable to connect to them. 

Also upon rebooting i am also greeted by a system program problem prompt, and i am not told any information about the error.

I am fairly new to ubuntu so i am unsure as to what may be causing this issue. if anyone can give me advice I would greatly appreciate it.

Thanks!

[B]EDIT: 
I decided to dive into the system logs to see if that could shed some light on what is happening, this is what i found:

[I]Jun  3 17:12:26 xxxspermmonkey420xxx kernel: [ 1402.059083] polkitd[5560]: segfault at 8 ip 00007f6c77c88e36 sp 00007ffc95a7a5a0 error 4 in libpolkit-backend-1.so.0.0.0[7f6c77c79000+18000]
Jun  3 17:12:26 xxxspermmonkey420xxx systemd[1]: polkitd.service: Main process exited, code=dumped, status=11/SEGV
Jun  3 17:12:26 xxxspermmonkey420xxx gnome-session[4459]: PolicyKit daemon disconnected from the bus.
Jun  3 17:12:26 xxxspermmonkey420xxx gnome-session[4459]: We are no longer a registered authentication agent.
Jun  3 17:12:26 xxxspermmonkey420xxx systemd[1]: polkitd.service: Unit entered failed state.
Jun  3 17:12:26 xxxspermmonkey420xxx systemd[1]: polkitd.service: Failed with result 'core-dump'.
Jun  3 17:12:26 xxxspermmonkey420xxx NetworkManager[1083]: <warn>  [1528060346.4188] error requesting auth for org.freedesktop.NetworkManager.reload: Authorization check failed: Message recipient disconnected from message bus without replying
Jun  3 17:12:26 xxxspermmonkey420xxx NetworkManager[1083]: <warn>  [1528060346.4189] error requesting auth for org.freedesktop.NetworkManager.settings.modify.hostname: Authorization check failed: Message recipient disconnected from message bus without replying
Jun  3 17:12:26 xxxspermmonkey420xxx NetworkManager[1083]: <warn>  [1528060346.4190] error requesting auth for org.freedesktop.NetworkManager.settings.modify.own: Authorization check failed: Message recipient disconnected from message bus without replying
Jun  3 17:12:26 xxxspermmonkey420xxx NetworkManager[1083]: <warn>  [1528060346.4191] error requesting auth for org.freedesktop.NetworkManager.settings.modify.system: Authorization check failed: Message recipient disconnected from message bus without replying
Jun  3 17:12:26 xxxspermmonkey420xxx NetworkManager[1083]: <warn>  [1528060346.4191] error requesting auth for org.freedesktop.NetworkManager.wifi.share.open: Authorization check failed: Message recipient disconnected from message bus without replying
Jun  3 17:12:26 xxxspermmonkey420xxx NetworkManager[1083]: <warn>  [1528060346.4192] error requesting auth for org.freedesktop.NetworkManager.wifi.share.protected: Authorization check failed: Message recipient disconnected from message bus without replying
Jun  3 17:12:26 xxxspermmonkey420xxx NetworkManager[1083]: <warn>  [1528060346.4193] error requesting auth for org.freedesktop.NetworkManager.network-control: Authorization check failed: Message recipient disconnected from message bus without replying
Jun  3 17:12:26 xxxspermmonkey420xxx NetworkManager[1083]: <warn>  [1528060346.4194] error requesting auth for org.freedesktop.NetworkManager.enable-disable-wimax: Authorization check failed: Message recipient disconnected from message bus without replying
Jun  3 17:12:26 xxxspermmonkey420xxx NetworkManager[1083]: <warn>  [1528060346.4194] error requesting auth for org.freedesktop.NetworkManager.enable-disable-wwan: Authorization check failed: Message recipient disconnected from message bus without replying
Jun  3 17:12:26 xxxspermmonkey420xxx NetworkManager[1083]: <warn>  [1528060346.4196] error requesting auth for org.freedesktop.NetworkManager.enable-disable-wifi: Authorization check failed: Message recipient disconnected from message bus without replying
Jun  3 17:12:26 xxxspermmonkey420xxx NetworkManager[1083]: <warn>  [1528060346.4196] error requesting auth for org.freedesktop.NetworkManager.sleep-wake: Authorization check failed: Message recipient disconnected from message bus without replying
Jun  3 17:12:26 xxxspermmonkey420xxx dbus[1056]: [system] Activating via systemd: service name='org.freedesktop.PolicyKit1' unit='polkitd.service'
Jun  3 17:12:26 xxxspermmonkey420xxx NetworkManager[1083]: <warn>  [1528060346.4197] error requesting auth for org.freedesktop.NetworkManager.enable-disable-network: Authorization check failed: Message recipient disconnected from message bus without replying
Jun  3 17:12:26 xxxspermmonkey420xxx systemd[1]: Starting Authenticate and Authorize Users to Run Privileged Tasks...
Jun  3 17:12:26 xxxspermmonkey420xxx polkitd[5609]: started daemon version 0.105 using authority implementation `local' version `0.105'
Jun  3 17:12:26 xxxspermmonkey420xxx dbus[1056]: [system] Successfully activated service 'org.freedesktop.PolicyKit1'
Jun  3 17:12:26 xxxspermmonkey420xxx systemd[1]: Started Authenticate and Authorize Users to Run Privileged Tasks.
Jun  3 17:12:26 xxxspermmonkey420xxx gnome-session[4459]: PolicyKit daemon reconnected to bus.
Jun  3 17:12:26 xxxspermmonkey420xxx gnome-session[4459]: Attempting to re-register as an authentication agent.
Jun  3 17:12:26 xxxspermmonkey420xxx gnome-session[4459]: We are now a registered authentication agent.[/I]

Hopefully this can help narrow it down.

[/B]

---

