---
title: "After Installing Japanese, something crashes and the language layout does not work."
date: 2020-02-14
forum: General Help
---

### Post by babaliaris on 2020-02-14
Hello everyone!

I recently installed Japanese on my laptop **Ubuntu 18.04.4 LTS **and now everytime I log in or sometimes even when I use the layout switch combination shortcut, something crashes.

[COLOR=#006400][SIZE=3]I have 3 layouts, english, greek and japanese at this exact order. If I switch between english and japanese everything works correcty. But if I stwich from greek to japanese, when I type, instead of japanese the computer writes greek characters but with the japanese fonts!!!

[/SIZE][/COLOR][COLOR=#000000][SIZE=3]Here is a video demonstrating the problem:[/SIZE][/COLOR][COLOR=#006400][SIZE=3] [https://www.youtube.com/watch?v=rLzKI6lN_qM](https://www.youtube.com/watch?v=rLzKI6lN_qM)

[/SIZE][/COLOR]**Here is the error:**
```

 unit='dbus-org.freedesktop.nm-dispatcher.service' requested by ':1.12' (uid=0 pid=1055 comm="/usr/sbin/NetworkManager --no-daemon " label="unconfined")
/var/log/syslog:Feb 14 08:47:06 babaliaris-pc systemd[1]: Starting Network Manager Script Dispatcher Service...
/var/log/syslog:Feb 14 08:47:06 babaliaris-pc dbus-daemon[1045]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
/var/log/syslog:Feb 14 08:47:06 babaliaris-pc systemd[1]: Started Network Manager Script Dispatcher Service.
/var/log/syslog:Feb 14 08:47:06 babaliaris-pc nm-dispatcher: req:1 'connectivity-change': new request (1 scripts)
/var/log/syslog:Feb 14 08:47:06 babaliaris-pc nm-dispatcher: req:1 'connectivity-change': start running ordered scripts...
/var/log/syslog:Feb 14 08:47:06 babaliaris-pc whoopsie[1767]: [08:47:06] Cannot reach: https://daisy.ubuntu.com
/var/log/syslog:Feb 14 08:47:06 babaliaris-pc whoopsie[1767]: [08:47:06] The default IPv4 route is: /org/freedesktop/NetworkManager/ActiveConnection/1
/var/log/syslog:Feb 14 08:47:06 babaliaris-pc whoopsie[1767]: [08:47:06] Not a paid data plan: /org/freedesktop/NetworkManager/ActiveConnection/1
/var/log/syslog:Feb 14 08:47:06 babaliaris-pc whoopsie[1767]: [08:47:06] Found usable connection: /org/freedesktop/NetworkManager/ActiveConnection/1
/var/log/syslog:Feb 14 08:47:08 babaliaris-pc whoopsie[1767]: [08:47:08] online
/var/log/syslog:Feb 14 08:47:12 babaliaris-pc anacron[1033]: Job `cron.daily' terminated
/var/log/syslog:Feb 14 08:47:12 babaliaris-pc anacron[1033]: Normal exit (1 job run)
/var/log/syslog:Feb 14 08:49:15 babaliaris-pc org.gnome.Shell.desktop[2598]: [4926:1:0214/084915.510018:ERROR:child_process_sandbox_support_impl_linux.cc(79)] FontService unique font name matching request did not receive a response.
/var/log/syslog:Feb 14 08:49:15 babaliaris-pc org.gnome.Shell.desktop[2598]: [4926:1:0214/084915.510741:ERROR:child_process_sandbox_support_impl_linux.cc(79)] FontService unique font name matching request did not receive a response.
/var/log/syslog:Feb 14 08:52:40 babaliaris-pc org.gnome.Shell.desktop[2598]: [5697:1:0214/085240.716693:ERROR:child_process_sandbox_support_impl_linux.cc(79)] FontService unique font name matching request did not receive a response.
/var/log/syslog:Feb 14 08:52:40 babaliaris-pc org.gnome.Shell.desktop[2598]: [5697:1:0214/085240.717620:ERROR:child_process_sandbox_support_impl_linux.cc(79)] FontService unique font name matching request did not receive a response.
/var/log/syslog:Feb 14 08:55:43 babaliaris-pc org.gnome.Shell.desktop[2598]: [5801:1:0214/085543.411510:ERROR:child_process_sandbox_support_impl_linux.cc(79)] FontService unique font name matching request did not receive a response.
/var/log/syslog:Feb 14 08:55:43 babaliaris-pc org.gnome.Shell.desktop[2598]: [5801:1:0214/085543.412262:ERROR:child_process_sandbox_support_impl_linux.cc(79)] FontService unique font name matching request did not receive a response.
/var/log/syslog:Feb 14 08:55:58 babaliaris-pc org.gnome.Shell.desktop[2598]: [5813:1:0214/085558.612894:ERROR:child_process_sandbox_support_impl_linux.cc(79)] FontService unique font name matching request did not receive a response.
/var/log/syslog:Feb 14 08:55:58 babaliaris-pc org.gnome.Shell.desktop[2598]: [5813:1:0214/085558.613599:ERROR:child_process_sandbox_support_impl_linux.cc(79)] FontService unique font name matching request did not receive a response.
/var/log/syslog:Feb 14 08:56:07 babaliaris-pc org.gnome.Shell.desktop[2598]: [5826:1:0214/085607.310572:ERROR:child_process_sandbox_support_impl_linux.cc(79)] FontService unique font name matching request did not receive a response.
/var/log/syslog:Feb 14 08:56:07 babaliaris-pc org.gnome.Shell.desktop[2598]: [5826:1:0214/085607.311296:ERROR:child_process_sandbox_support_impl_linux.cc(79)] FontService unique font name matching request did not receive a response.

```

---

