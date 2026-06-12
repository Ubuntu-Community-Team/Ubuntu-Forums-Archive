---
title: "Login blanks - need to CTRL-ALT-F!"
date: 2023-08-23
forum: General Help
---

### Post by yaminb on 2023-08-23
I have a problem that started in the last month or so.
When I boot
[LIST=1]
[*]It goes to the login screen 
[*]I login (user/pw) 
[*]Screen goes blank 
[*]I have to press ctrl-alt-f1... screen comes back. 
[*]I do my password again 
[*]This time, it logs in properly 
[/LIST]

I suspect this might have something to do with Nvidia/wayland as I have some issues locking/recovering from sleep.
When I look at the logs, I see these important ones.
```

&#8199;8:41:43 AM kernel: [drm:nv_drm_master_set [nvidia_drm]] *ERROR* [nvidia-drm] [GPU ID 0x00000600] Failed to grab modeset ownership
&#8199;8:40:53 AM systemd: Failed to start app-gnome-user\x2ddirs\x2dupdate\x2dgtk-3866.scope - Application launched by gnome-session-binary.
&#8199;8:40:53 AM systemd: Failed to start app-gnome-user\x2ddirs\x2dupdate\x2dgtk-3866.scope - Application launched by gnome-session-binary.
&#8199;8:40:53 AM systemd: Failed to start app-gnome-org.gnome.Software-3841.scope - Application launched by gnome-session-binary.
&#8199;8:40:53 AM systemd: Failed to start app-gnome-im\x2dlaunch-3867.scope - Application launched by gnome-session-binary.
&#8199;8:40:51 AM systemd: Failed to start app-gnome-gnome\x2dkeyring\x2dpkcs11-3500.scope - Application launched by gnome-session-binary.
&#8199;8:40:50 AM gdm-session-wor: gkr-pam: unable to locate daemon control file
&#8199;8:40:42 AM kernel: [drm:nv_drm_master_set [nvidia_drm]] *ERROR* [nvidia-drm] [GPU ID 0x00000600] Failed to grab modeset ownership
&#8199;8:40:42 AM kernel: overlayfs: missing 'lowerdir'
&#8199;8:40:40 AM kernel: [drm:nv_drm_master_set [nvidia_drm]] *ERROR* [nvidia-drm] [GPU ID 0x00000600] Failed to grab modeset ownership
&#8199;8:40:39 AM (uetoothd): src/plugin.c:plugin_init() Failed to init bap plugin
&#8199;8:40:39 AM (uetoothd): src/plugin.c:plugin_init() Failed to init bap plugin
&#8199;8:40:39 AM (uetoothd): src/plugin.c:plugin_init() Failed to init mcp plugin
&#8199;8:40:39 AM (uetoothd): src/plugin.c:plugin_init() Failed to init vcp plugin
&#8199;8:40:37 AM kernel: 
&#8199;8:40:37 AM systemd-udevd: event10: Failed to call EVIOCSKEYCODE with scan code 0x7c, and key code 190: Invalid argument
&#8199;8:40:37 AM systemd-udevd: event10: Failed to call EVIOCSKEYCODE with scan code 0x7c, and key code 190: Invalid argument
&#8199;8:40:37 AM systemd-udevd: event_source: Failed to get device name: No such file or directory
&#8199;8:40:36 AM kernel: blacklist: Problem blacklisting hash (-13)
&#8199;8:40:36 AM kernel: blacklist: Problem blacklisting hash (-13)
&#8199;8:40:36 AM kernel: blacklist: Problem blacklisting hash (-13)
&#8199;8:40:36 AM kernel: blacklist: Problem blacklisting hash (-13)
&#8199;8:40:36 AM kernel: blacklist: Problem blacklisting hash (-13)

```

Should mention. I am running Ubuntu 23.04
Any ideas?

---

### Post by yaminb on 2023-08-24
any ideas?

---

