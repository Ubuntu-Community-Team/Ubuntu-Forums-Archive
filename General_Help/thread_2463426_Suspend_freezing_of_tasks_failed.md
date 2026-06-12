---
title: "Suspend: freezing of tasks failed"
date: 2021-06-10
forum: General Help
---

### Post by dorpapst on 2021-06-10
Hello friends,
Sometimes, it is not possible to suspend my Ubuntu 20.04 system, I rather get the error message
```
freezing of tasks failed after 20 seconds
```
it happened two times today.

is there any clever way to peak into a specific log file where I can find out which programme / process is causing that?

Many thanks
Lukas

---

### Post by dorpapst on 2021-06-11
That is the output of /var/log/kern.log from the moment it was failing again some minutes ago

Does anybody have a clue why this happens?
```
Jun 11 19:04:38 mycroft kernel: [15844.542200] PM: suspend entry (deep)
Jun 11 19:04:38 mycroft kernel: [15844.632793] Filesystems sync: 0.090 seconds
Jun 11 19:04:38 mycroft kernel: [15845.325390] rfkill: input handler enabled
Jun 11 19:04:59 mycroft kernel: [15845.789387] Freezing user space processes ... 
Jun 11 19:04:59 mycroft kernel: [15865.787920] Freezing of tasks failed after 20.004 seconds (1 tasks refusing to freeze, wq_busy=0):
Jun 11 19:04:59 mycroft kernel: [15865.787927] fbcon: Taking over console
Jun 11 19:04:59 mycroft kernel: [15865.787957] duplicity       D    0  9126   4697 0x00004004
Jun 11 19:04:59 mycroft kernel: [15865.787959] Call Trace:
Jun 11 19:04:59 mycroft kernel: [15865.787966]  __schedule+0x394/0xa60
Jun 11 19:04:59 mycroft kernel: [15865.787968]  schedule+0x55/0xc0
Jun 11 19:04:59 mycroft kernel: [15865.787971]  request_wait_answer+0xa0/0x210
Jun 11 19:04:59 mycroft kernel: [15865.787974]  ? wait_woken+0x80/0x80
Jun 11 19:04:59 mycroft kernel: [15865.787975]  fuse_simple_request+0x1a5/0x2b0
Jun 11 19:04:59 mycroft kernel: [15865.787977]  fuse_dentry_revalidate+0x167/0x300
Jun 11 19:04:59 mycroft kernel: [15865.787981]  lookup_fast+0xda/0x150
Jun 11 19:04:59 mycroft kernel: [15865.787982]  walk_component+0x43/0x1b0
Jun 11 19:04:59 mycroft kernel: [15865.787984]  link_path_walk.part.0+0x21f/0x350
Jun 11 19:04:59 mycroft kernel: [15865.787985]  ? path_init+0x311/0x3b0
Jun 11 19:04:59 mycroft kernel: [15865.787986]  path_lookupat.isra.0+0x3a/0x150
Jun 11 19:04:59 mycroft kernel: [15865.787988]  filename_lookup+0xae/0x180
Jun 11 19:04:59 mycroft kernel: [15865.787990]  ? __check_object_size+0x13f/0x150
Jun 11 19:04:59 mycroft kernel: [15865.787993]  ? strncpy_from_user+0x4c/0x170
Jun 11 19:04:59 mycroft kernel: [15865.787994]  ? getname_flags+0x6f/0x1f0
Jun 11 19:04:59 mycroft kernel: [15865.787996]  ? list_lru_add+0x94/0x120
Jun 11 19:04:59 mycroft kernel: [15865.787998]  user_path_at_empty+0x3a/0x50
Jun 11 19:04:59 mycroft kernel: [15865.788000]  vfs_statx+0x7b/0x110
Jun 11 19:04:59 mycroft kernel: [15865.788001]  ? __fput+0x16d/0x250
Jun 11 19:04:59 mycroft kernel: [15865.788003]  __do_sys_newlstat+0x3e/0x80
Jun 11 19:04:59 mycroft kernel: [15865.788006]  ? __prepare_exit_to_usermode+0xaf/0x210
Jun 11 19:04:59 mycroft kernel: [15865.788007]  ? __syscall_return_slowpath+0x31/0x160
Jun 11 19:04:59 mycroft kernel: [15865.788009]  __x64_sys_newlstat+0x16/0x20
Jun 11 19:04:59 mycroft kernel: [15865.788011]  do_syscall_64+0x49/0xc0
Jun 11 19:04:59 mycroft kernel: [15865.788012]  entry_SYSCALL_64_after_hwframe+0x44/0xa9
Jun 11 19:04:59 mycroft kernel: [15865.788014] RIP: 0033:0x7fb6c0eb96ea
Jun 11 19:04:59 mycroft kernel: [15865.788015] RSP: 002b:00007fff33516448 EFLAGS: 00000246 ORIG_RAX: 0000000000000006
Jun 11 19:04:59 mycroft kernel: [15865.788016] RAX: ffffffffffffffda RBX: 0000000000000001 RCX: 00007fb6c0eb96ea
Jun 11 19:04:59 mycroft kernel: [15865.788017] RDX: 00007fff33516450 RSI: 00007fff33516450 RDI: 0000000001cd7e00
Jun 11 19:04:59 mycroft kernel: [15865.788017] RBP: 0000000000000000 R08: 0000000000000001 R09: 0000000000000003
Jun 11 19:04:59 mycroft kernel: [15865.788018] R10: 0000000001c8cd98 R11: 0000000000000246 R12: 00007fb6b0010e30
Jun 11 19:04:59 mycroft kernel: [15865.788018] R13: 0000000001cd7e00 R14: 0000000000008180 R15: 00000000018bdef8
Jun 11 19:04:59 mycroft kernel: [15865.788028] OOM killer enabled.
Jun 11 19:04:59 mycroft kernel: [15865.788028] Restarting tasks ... done.
Jun 11 19:04:59 mycroft kernel: [15865.792376] Console: switching to colour frame buffer device 128x48
Jun 11 19:04:59 mycroft kernel: [15865.795106] PM: suspend exit
Jun 11 19:04:59 mycroft kernel: [15865.795167] PM: suspend entry (s2idle)
Jun 11 19:09:51 mycroft kernel: [    0.000000] Linux version 5.8.0-55-generic (buildd@lgw01-amd64-050) (gcc (Ubuntu 9.3.0-17ubuntu1~20.04) 9.3.0, GNU ld (GNU Binutils for Ubuntu) 2.34) #62~20.04.1-Ubuntu SMP Wed Jun 2 08:55:04 UTC 2021 (Ubuntu 5.8.0-55.62~20.04.1-generic 5.8.18)
Jun 11 19:09:51 mycroft kernel: [    0.000000] Command line: BOOT_IMAGE=/@/boot/vmlinuz-5.8.0-55-generic root=UUID=b91dad34-c1b8-4ed2-8e2f-0af70fb3ffed ro rootflags=subvol=@ acpi_osi=Linux quiet splash acpi_backlight=vendor vt.handoff=7
```

And the /var/log/syslog:
```
Jun 11 19:04:34 mycroft NetworkManager[791]: <info>  [1623431074.7129] manager: sleep: sleep requested (sleeping: no  enabled: yes)
Jun 11 19:04:34 mycroft NetworkManager[791]: <info>  [1623431074.7130] manager: NetworkManager state is now ASLEEP
Jun 11 19:04:34 mycroft whoopsie[1114]: [19:04:34] offline
Jun 11 19:04:34 mycroft deja-dup-monito[4342]: Source ID 311 was not found when attempting to remove it
Jun 11 19:04:35 mycroft rtkit-daemon[1294]: Supervising 6 threads of 4 processes of 1 users.
Jun 11 19:04:35 mycroft rtkit-daemon[1294]: Successfully made thread 24509 of process 1277 owned by '1000' RT at priority 5.
Jun 11 19:04:35 mycroft rtkit-daemon[1294]: Supervising 7 threads of 4 processes of 1 users.
Jun 11 19:04:35 mycroft discord.desktop[20168]: [2021-06-11 19:04:35.567] [20196] (audio_device_generic.cc:62): SetPlayoutDevice: Not supported on this platform
Jun 11 19:04:38 mycroft systemd[1]: Reached target Sleep.
Jun 11 19:04:38 mycroft systemd[1]: Starting Suspend...
Jun 11 19:04:38 mycroft systemd-sleep[24516]: Suspending system...
Jun 11 19:04:38 mycroft kernel: [15844.542200] PM: suspend entry (deep)
Jun 11 19:04:38 mycroft kernel: [15844.632793] Filesystems sync: 0.090 seconds
Jun 11 19:04:38 mycroft rtkit-daemon[1294]: Supervising 6 threads of 4 processes of 1 users.
Jun 11 19:04:38 mycroft rtkit-daemon[1294]: Successfully made thread 24520 of process 1277 owned by '1000' RT at priority 5.
Jun 11 19:04:38 mycroft rtkit-daemon[1294]: Supervising 7 threads of 4 processes of 1 users.
Jun 11 19:04:38 mycroft discord.desktop[20168]: [2021-06-11 19:04:38.568] [20196] (audio_device_generic.cc:62): SetPlayoutDevice: Not supported on this platform
Jun 11 19:04:38 mycroft /usr/lib/gdm3/gdm-x-session[1291]: (**) Option "fd" "25"
Jun 11 19:04:38 mycroft /usr/lib/gdm3/gdm-x-session[1291]: (II) event1  - Power Button: device removed
Jun 11 19:04:38 mycroft /usr/lib/gdm3/gdm-x-session[1291]: (**) Option "fd" "46"
Jun 11 19:04:38 mycroft /usr/lib/gdm3/gdm-x-session[1291]: (II) event0  - Power Button: device removed
Jun 11 19:04:38 mycroft /usr/lib/gdm3/gdm-x-session[1291]: (**) Option "fd" "41"
Jun 11 19:04:38 mycroft /usr/lib/gdm3/gdm-x-session[1291]: (II) event6  - UVC Camera (046d:081b): device removed
Jun 11 19:04:38 mycroft /usr/lib/gdm3/gdm-x-session[1291]: (**) Option "fd" "45"
Jun 11 19:04:38 mycroft /usr/lib/gdm3/gdm-x-session[1291]: (II) event2  - Logitech USB Optical Mouse: device removed
Jun 11 19:04:38 mycroft /usr/lib/gdm3/gdm-x-session[1291]: (**) Option "fd" "44"
Jun 11 19:04:38 mycroft /usr/lib/gdm3/gdm-x-session[1291]: (II) event3  - Logitech USB Keyboard: device removed
Jun 11 19:04:38 mycroft /usr/lib/gdm3/gdm-x-session[1291]: (**) Option "fd" "27"
Jun 11 19:04:38 mycroft /usr/lib/gdm3/gdm-x-session[1291]: (**) Option "fd" "49"
Jun 11 19:04:38 mycroft /usr/lib/gdm3/gdm-x-session[1291]: (II) event5  - Logitech USB Keyboard System Control: device removed
Jun 11 19:04:38 mycroft /usr/lib/gdm3/gdm-x-session[1291]: (**) Option "fd" "28"
Jun 11 19:04:38 mycroft /usr/lib/gdm3/gdm-x-session[1291]: (**) Option "fd" "27"
Jun 11 19:04:38 mycroft /usr/lib/gdm3/gdm-x-session[1291]: (II) event4  - Logitech USB Keyboard Consumer Control: device removed
Jun 11 19:04:38 mycroft /usr/lib/gdm3/gdm-x-session[1291]: (**) Option "fd" "28"
Jun 11 19:04:38 mycroft /usr/lib/gdm3/gdm-x-session[1291]: (II) event18 - LogiOps Virtual Input: device removed
Jun 11 19:04:38 mycroft /usr/lib/gdm3/gdm-x-session[1291]: (**) Option "fd" "69"
Jun 11 19:04:38 mycroft /usr/lib/gdm3/gdm-x-session[1291]: (II) event19 - MX Master 2S Keyboard: device removed
Jun 11 19:04:38 mycroft /usr/lib/gdm3/gdm-x-session[1291]: (**) Option "fd" "70"
Jun 11 19:04:38 mycroft /usr/lib/gdm3/gdm-x-session[1291]: (II) event20 - MX Master 2S Mouse: device removed
Jun 11 19:04:38 mycroft rtkit-daemon[1294]: Supervising 6 threads of 4 processes of 1 users.
Jun 11 19:04:38 mycroft rtkit-daemon[1294]: Successfully made thread 24521 of process 1277 owned by '1000' RT at priority 5.
Jun 11 19:04:38 mycroft rtkit-daemon[1294]: Supervising 7 threads of 4 processes of 1 users.
Jun 11 19:04:38 mycroft rtkit-daemon[1294]: Supervising 6 threads of 4 processes of 1 users.
Jun 11 19:04:38 mycroft rtkit-daemon[1294]: Successfully made thread 24522 of process 1277 owned by '1000' RT at priority 5.
Jun 11 19:04:38 mycroft rtkit-daemon[1294]: Supervising 7 threads of 4 processes of 1 users.
Jun 11 19:04:38 mycroft kernel: [15845.325390] rfkill: input handler enabled
Jun 11 19:04:39 mycroft /usr/lib/gdm3/gdm-x-session[1291]: (II) systemd-logind: got pause for 13:69
Jun 11 19:04:39 mycroft /usr/lib/gdm3/gdm-x-session[1291]: (II) systemd-logind: got pause for 13:65
Jun 11 19:04:39 mycroft /usr/lib/gdm3/gdm-x-session[1291]: (II) systemd-logind: got pause for 13:68
Jun 11 19:04:39 mycroft /usr/lib/gdm3/gdm-x-session[1291]: (II) systemd-logind: got pause for 13:82
Jun 11 19:04:39 mycroft /usr/lib/gdm3/gdm-x-session[1291]: (II) systemd-logind: got pause for 13:70
Jun 11 19:04:39 mycroft /usr/lib/gdm3/gdm-x-session[1291]: (II) systemd-logind: got pause for 13:84
Jun 11 19:04:39 mycroft /usr/lib/gdm3/gdm-x-session[1291]: (II) systemd-logind: got pause for 13:67
Jun 11 19:04:39 mycroft /usr/lib/gdm3/gdm-x-session[1291]: (II) systemd-logind: got pause for 13:66
Jun 11 19:04:39 mycroft /usr/lib/gdm3/gdm-x-session[1291]: (II) systemd-logind: got pause for 13:83
Jun 11 19:04:39 mycroft /usr/lib/gdm3/gdm-x-session[1291]: (II) systemd-logind: got pause for 13:64
Jun 11 19:04:39 mycroft gnome-shell[1486]: g_dbus_connection_emit_signal: assertion 'G_IS_DBUS_CONNECTION (connection)' failed
Jun 11 19:04:59 mycroft acpid: client 1291[0:0] has disconnected
Jun 11 19:04:59 mycroft kernel: [15845.789387] Freezing user space processes ... 
Jun 11 19:04:59 mycroft kernel: [15865.787920] Freezing of tasks failed after 20.004 seconds (1 tasks refusing to freeze, wq_busy=0):
Jun 11 19:04:59 mycroft kernel: [15865.787927] fbcon: Taking over console
Jun 11 19:04:59 mycroft kernel: [15865.787957] duplicity       D    0  9126   4697 0x00004004
Jun 11 19:04:59 mycroft kernel: [15865.787959] Call Trace:
Jun 11 19:04:59 mycroft kernel: [15865.787966]  __schedule+0x394/0xa60
Jun 11 19:04:59 mycroft kernel: [15865.787968]  schedule+0x55/0xc0
Jun 11 19:04:59 mycroft kernel: [15865.787971]  request_wait_answer+0xa0/0x210
Jun 11 19:04:59 mycroft kernel: [15865.787974]  ? wait_woken+0x80/0x80
Jun 11 19:04:59 mycroft kernel: [15865.787975]  fuse_simple_request+0x1a5/0x2b0
Jun 11 19:04:59 mycroft kernel: [15865.787977]  fuse_dentry_revalidate+0x167/0x300
Jun 11 19:04:59 mycroft kernel: [15865.787981]  lookup_fast+0xda/0x150
Jun 11 19:04:59 mycroft kernel: [15865.787982]  walk_component+0x43/0x1b0
Jun 11 19:04:59 mycroft kernel: [15865.787984]  link_path_walk.part.0+0x21f/0x350
Jun 11 19:04:59 mycroft kernel: [15865.787985]  ? path_init+0x311/0x3b0
Jun 11 19:04:59 mycroft kernel: [15865.787986]  path_lookupat.isra.0+0x3a/0x150
Jun 11 19:04:59 mycroft kernel: [15865.787988]  filename_lookup+0xae/0x180
Jun 11 19:04:59 mycroft kernel: [15865.787990]  ? __check_object_size+0x13f/0x150
Jun 11 19:04:59 mycroft kernel: [15865.787993]  ? strncpy_from_user+0x4c/0x170
Jun 11 19:04:59 mycroft kernel: [15865.787994]  ? getname_flags+0x6f/0x1f0
Jun 11 19:04:59 mycroft kernel: [15865.787996]  ? list_lru_add+0x94/0x120
Jun 11 19:04:59 mycroft kernel: [15865.787998]  user_path_at_empty+0x3a/0x50
Jun 11 19:04:59 mycroft kernel: [15865.788000]  vfs_statx+0x7b/0x110
Jun 11 19:04:59 mycroft kernel: [15865.788001]  ? __fput+0x16d/0x250
Jun 11 19:04:59 mycroft kernel: [15865.788003]  __do_sys_newlstat+0x3e/0x80
Jun 11 19:04:59 mycroft kernel: [15865.788006]  ? __prepare_exit_to_usermode+0xaf/0x210
Jun 11 19:04:59 mycroft kernel: [15865.788007]  ? __syscall_return_slowpath+0x31/0x160
Jun 11 19:04:59 mycroft kernel: [15865.788009]  __x64_sys_newlstat+0x16/0x20
Jun 11 19:04:59 mycroft kernel: [15865.788011]  do_syscall_64+0x49/0xc0
Jun 11 19:04:59 mycroft kernel: [15865.788012]  entry_SYSCALL_64_after_hwframe+0x44/0xa9
Jun 11 19:04:59 mycroft kernel: [15865.788014] RIP: 0033:0x7fb6c0eb96ea
Jun 11 19:04:59 mycroft kernel: [15865.788015] RSP: 002b:00007fff33516448 EFLAGS: 00000246 ORIG_RAX: 0000000000000006
Jun 11 19:04:59 mycroft kernel: [15865.788016] RAX: ffffffffffffffda RBX: 0000000000000001 RCX: 00007fb6c0eb96ea
Jun 11 19:04:59 mycroft kernel: [15865.788017] RDX: 00007fff33516450 RSI: 00007fff33516450 RDI: 0000000001cd7e00
Jun 11 19:04:59 mycroft kernel: [15865.788017] RBP: 0000000000000000 R08: 0000000000000001 R09: 0000000000000003
Jun 11 19:04:59 mycroft kernel: [15865.788018] R10: 0000000001c8cd98 R11: 0000000000000246 R12: 00007fb6b0010e30
Jun 11 19:04:59 mycroft kernel: [15865.788018] R13: 0000000001cd7e00 R14: 0000000000008180 R15: 00000000018bdef8
Jun 11 19:04:59 mycroft kernel: [15865.788028] OOM killer enabled.
Jun 11 19:04:59 mycroft kernel: [15865.788028] Restarting tasks ... done.
Jun 11 19:04:59 mycroft logid[799]: [WARN] Error ignored on detached thread/task: _readReport read failed: Input/output error
Jun 11 19:04:59 mycroft acpid: input device has been disconnected, fd 24
Jun 11 19:04:59 mycroft rtkit-daemon[1294]: The canary thread is apparently starving. Taking action.
Jun 11 19:04:59 mycroft rtkit-daemon[1294]: Demoting known real-time threads.
Jun 11 19:04:59 mycroft rtkit-daemon[1294]: Successfully demoted thread 21812 of process 3921.
Jun 11 19:04:59 mycroft rtkit-daemon[1294]: Successfully demoted thread 4500 of process 4280.
Jun 11 19:04:59 mycroft rtkit-daemon[1294]: Successfully demoted thread 3896 of process 3788.
Jun 11 19:04:59 mycroft rtkit-daemon[1294]: Successfully demoted thread 24522 of process 1277.
Jun 11 19:04:59 mycroft rtkit-daemon[1294]: Successfully demoted thread 1509 of process 1277.
Jun 11 19:04:59 mycroft rtkit-daemon[1294]: Successfully demoted thread 1460 of process 1277.
Jun 11 19:04:59 mycroft rtkit-daemon[1294]: Successfully demoted thread 1277 of process 1277.
Jun 11 19:04:59 mycroft rtkit-daemon[1294]: Demoted 7 threads.
Jun 11 19:04:59 mycroft /usr/lib/gdm3/gdm-x-session[1291]: (II) config/udev: removing device MX Master 2S Keyboard
Jun 11 19:04:59 mycroft /usr/lib/gdm3/gdm-x-session[1291]: (II) UnloadModule: "libinput"
Jun 11 19:04:59 mycroft /usr/lib/gdm3/gdm-x-session[1291]: (II) systemd-logind: releasing fd for 13:83
Jun 11 19:04:59 mycroft kernel: [15865.792376] Console: switching to colour frame buffer device 128x48
Jun 11 19:04:59 mycroft gdm3: GLib: Source ID 56 was not found when attempting to remove it
Jun 11 19:04:59 mycroft kernel: [15865.795106] PM: suspend exit
Jun 11 19:04:59 mycroft kernel: [15865.795167] PM: suspend entry (s2idle)
```

---

