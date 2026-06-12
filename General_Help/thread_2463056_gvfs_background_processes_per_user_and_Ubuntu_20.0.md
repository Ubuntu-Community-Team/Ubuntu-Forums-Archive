---
title: "gvfs background processes per user and Ubuntu 20.04"
date: 2021-06-02
forum: General Help
---

### Post by c_xy on 2021-06-02
[FONT=arial][COLOR=#000000]Hello,
[/COLOR]
[COLOR=#000000]Recently working on a new system using on Ubuntu 20.04 with  linux. We have multiple users who ssh into the server. Noticed something different that we never experienced previously on 18.04. Reboots usually clear all sessions per user. After reboot on 18.04, you would see the following output from the linux command:
[/COLOR]
[/FONT][COLOR=#000000][FONT=Calibri]
[/FONT][/COLOR]```

[COLOR=#000000][FONT=Calibri]%ps -elf | grep username[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]4 S username       xxxx     1  0  80   0 - xxxxx -      15:20 ?        00:00:00 /lib/systemd/systemd --user 5 S username       xxxx  xxxx  0  80   0 - xxxxx -      15:20 ?        00:00:00 (sd-pam)

[/FONT][/COLOR]
```
[FONT=arial][COLOR=#000000]
[/COLOR]
[COLOR=#000000]However, after reboot on the Ubuntu 20.04 system, I see the following output:[/COLOR][/FONT]
[COLOR=#000000][FONT=Calibri]
[/FONT][/COLOR]```
 

[COLOR=#000000][FONT=Calibri]%ps -elf | grep username[/FONT][/COLOR]

[COLOR=#000000][FONT=Calibri]4 S username XXXX 1 0 80 0 - XXXX - 20:44 ? 0:00:00 /lib/systemd/systemd --user 5 S username XXXX XXXX 0 80 0 - XXXX - 20:44 ? 0:00:00 (sd-pam)
0 S username XXXX XXXX 0 80 0 - XXXX - 20:44 ? 0:00:00 /usr/bin/pulseaudio
0 S username XXXX XXXX 0 99 - - XXXX - 20:44 ? 0:00:00 /usr/libexec/tracker-miner-fs
0  S username XXXX XXXX 0 80 0 - XXXX - 20:44 ? 0:00:00  /usr/bin/dbus-daemon --session --address=systemd: --nofork --nopidfile  --systemd-activation --syslog-only
0 S username XXXX XXXX 0 80 0 - XXXX - 20:44 ? 0:00:00 /usr/libexec/gvfsd 
0 S username XXXX XXXX 0 80 0 - XXXX - 20:44 ? 0:00:00 /usr/libexec/gvfsd-fuse /run/user/1020/gvfs -f -o big_writes
0 S username XXXX XXXX 0 80 0 - XXXX - 20:44 ? 0:00:00 /usr/libexec/gvfs-udisks2-volume-monitor
0 S username XXXX XXXX 0 80 0 - XXXX - 20:44 ? 0:00:00 /usr/libexec/gvfs-gphoto2-volume-monitor
0 S username XXXX XXXX 0 80 0 - XXXX - 20:44 ? 0:00:00 /usr/libexec/gvfs-afc-volume-monitor
0 S username XXXX XXXX 0 80 0 - XXXX - 20:44 ? 0:00:00 /usr/libexec/gvfs-mtp-volume-monitor
0 S username XXXX XXXX 0 80 0 - XXXX - 20:44 ? 0:00:00 /usr/libexec/gvfs-goa-volume-monitor
0 S username XXXX XXXX 0 80 0 - XXXX - 20:44 ? 0:00:00 /usr/libexec/goa-daemon
0 S username XXXX XXXX 0 80 0 - XXXX - 20:44 ? 0:00:00 /usr/libexec/goa-identity-service
[/FONT][/COLOR]
```
[COLOR=#000000][FONT=Calibri]
[/FONT][/COLOR][FONT=arial]
[COLOR=#000000]The  usernames appear in the "top" command output with goa-identity-se  process despite not logging in 'username' for a ssh session after a reboot. Is  there some setting one can change for Ubuntu 20.04, so these  processes aren't running if a person hasn't logged in via an ssh session  after reboot? Is there way to get the same behavior on 20.04 as we experienced previously on 18.04?
[/COLOR]
[COLOR=#000000]
[/COLOR]
[/FONT][COLOR=#000000][FONT=Calibri][FONT=arial]Thanks.

[/FONT]
[/FONT][/COLOR]

---

### Post by TheFu on 2021-06-02
If you don't want GUI stuff running, don't install Ubuntu with a GUI?  Install an Ubuntu Server - without any GUI stuff.  Then we don't get any GVFS stuff and certainly won't have any audio stuff.

---

### Post by c_xy on 2021-06-02
I see. However, we are using a gui. We've used it with 10.04,14.04, 16.04, 18.04, and  now 20.04.

We are just now seeing this issue with 20.04.

Was there a change in 20.04 to where all this stuff runs in the background now? If so, how can we change it?

Thanks.

---

### Post by TheFu on 2021-06-02
Please realize that nobody here works to Canonical ... well - 1 person does, but she doesn't seem to look at these questions much.

Sorry that you don't like my solution.

---

