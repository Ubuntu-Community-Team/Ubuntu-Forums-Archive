---
title: "problem with remaining kde processes"
date: 2007-05-18
forum: General Help
---

### Post by al3xboya on 2007-05-18
Hello, 
Few days ago i installed kde on my ubuntu 6.10. I didn't like it at all so i removed it.
But there are stil some remaining processes, as pstree shows:
init-+-bonobo-activati---{bonobo-activati}
     |-cron
     |-2*[dbus-daemon]
     |-dbus-launch
     |-events/0
     |-gaim
     |-gconfd-2
     |-gdm---gdm-+-Xorg
     |           `-x-session-manag---ssh-agent
     |-6*[getty]
     |-gnome-keyring-d
     |-gnome-panel
     |-gnome-power-man
     |-gnome-screensav
     |-gnome-settings----{gnome-settings-}
     |-gnome-terminal-+-bash---pstree
     |                |-gnome-pty-helpe
     |                `-{gnome-terminal}
     |-gnome-vfs-daemo
     |-gnome-volume-ma
     |-hald---hald-runner-+-hald-addon-acpi
     |                    |-hald-addon-keyb
     |                    `-hald-addon-stor
     |-khelper
     |-ksoftirqd/0
     |-kswapd0
     |-kthread-+-aio/0
     |         |-kacpi_notify
     |         |-kacpid
     |         |-kblockd/0
     |         |-kgameportd
     |         |-khubd
     |         |-2*[kjournald]
     |         |-kpsmoused
     |         |-kseriod
     |         |-2*[pdflush]
     |         `-shpchpd
     |-logd
     |-mapping-daemon
     |-metacity
     |-migration/0
     |-mixer_applet2
     |-nautilus
     |-nmbd
     |-notification-da
     |-opera---operapluginclea
     |-portmap
     |-preload
     |-rpc.statd
     |-sh---esd
     |-smbd---smbd
     |-syslogd
     |-system-tools-ba---dbus-daemon
     |-trashapplet
     |-udevd
     |-update-notifier
     |-watchdog/0
     `-xmms---4*[{xmms}]

I would apreciate any hint on how do i remove those processes (khelper, kthred and his child processes etc.).

---

