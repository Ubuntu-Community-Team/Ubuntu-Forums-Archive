---
title: "Opening settings gives nouveau errors and goes back to login screen"
date: 2019-03-14
forum: General Help
---

### Post by dennis99 on 2019-03-14
Hi all, i'm in need of some help.
When i do a fresh install of ubuntu budgie all to be fine, until i try to open any setting menu.
when i go i.e to the display settings than something goes wrong and ubuntu doesn't like it.
I've included the log file that i found, but i'm unsure how to fix this problem.
Also i found the other thread like mine, but i decided to post my own because i'm not in a virtual machine, but on a HDD install

```

12:22:04 pulseaudio: [pulseaudio] bluez5-util.c: GetManagedObjects() failed: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
12:21:32 spice-vdagent: Cannot access vdagent virtio channel /dev/virtio-ports/com.redhat.spice.0
12:21:28 systemd: Failed to start BAMF Application Matcher Framework.
12:21:28 lightdm: PAM adding faulty module: pam_kwallet5.so
12:21:28 systemd: Failed to start BAMF Application Matcher Framework.
12:21:27 lightdm: PAM adding faulty module: pam_kwallet5.so
12:21:27 systemd: Failed to start BAMF Application Matcher Framework.
12:21:26 kernel: nouveau 0000:01:00.0: gr: init failed, -16
12:21:26 gnome-session-b: Unrecoverable failure in required component budgie-panel.desktop
12:21:26 kernel: nouveau 0000:01:00.0: gr: init failed, -16
12:19:03 pulseaudio: [pulseaudio] bluez5-util.c: GetManagedObjects() failed: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
12:18:35 spice-vdagent: Cannot access vdagent virtio channel /dev/virtio-ports/com.redhat.spice.0
12:18:30 lightdm: PAM adding faulty module: pam_kwallet5.so
12:18:29 kernel: nouveau 0000:01:00.0: gr: init failed, -16
12:18:22 systemd: Failed to start BAMF Application Matcher Framework.
12:18:21 kernel: nouveau 0000:01:00.0: gr: init failed, -16
12:18:21 systemd: Failed to start BAMF Application Matcher Framework.
12:18:20 kernel: nouveau 0000:01:00.0: gr: init failed, -16
12:18:20 systemd: Failed to start BAMF Application Matcher Framework.
12:18:20 gnome-session-b: CRITICAL: We failed, but the fail whale is dead. Sorry....
12:18:14 kernel: nouveau 0000:01:00.0: gr: init failed, -16
12:18:01 pulseaudio: [pulseaudio] bluez5-util.c: GetManagedObjects() failed: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
12:17:32 spice-vdagent: Cannot access vdagent virtio channel /dev/virtio-ports/com.redhat.spice.0
12:17:15 lightdm: PAM adding faulty module: pam_kwallet5.so
12:16:57 kernel: nouveau 0000:01:00.0: gr: init failed, -16
12:16:29 kernel: ldm_parse_tocblock(): Cannot find TOCBLOCK, database may be corrupt.
12:16:29 kernel: ACPI Error: Method parse/execution failed \_SB.PCI0.SAT0.SPT1._GTF, AE_NOT_FOUND (20180531/psparse-516)
```

---

### Post by Autodave on 2019-03-14
My first guess is that your download was corrupted.   You might want to try downloading it again and trying.

Please give us some info on your system: that could also be causing problems.

---

### Post by dennis99 on 2019-03-14
I7 3770
Gtx 1070ti 
24gb ram
Gigabyte-ga-z77x-d3h MB

I'm not sure what other info is needed

---

