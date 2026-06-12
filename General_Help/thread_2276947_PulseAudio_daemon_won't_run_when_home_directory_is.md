---
title: "PulseAudio daemon won't run when home directory is mounted on network"
date: 2015-05-05
forum: General Help
---

### Post by phu004 on 2015-05-05
Hi guys,

I have my home directory mounted on a windows share via pam mount, but it has casued pulseaudio deamon to not run:

```

phu004@math-test:~$ pacmd
No PulseAudio daemon running, or not running as session daemon.

phu004@math-test:~$ pulseaudio
E: [pulseaudio] core-util.c: Failed to create secure directory (/home/phu004/.config/pulse): Permission denied

```

The mount code i used in pam_mount.conf.xml are
```

<volume fstype="cifs" server="someserver" path="%(USER)/" mountpoint="/home/%(USER)" options="workgroup=uoa,file_mode=0700,dir_mode=0700,directio,nosuid,nosetuids,nodev" />

```

I am using ubuntu 14.04 64bits. Could anyone suggest a way to get around this problem?


Thanks in advance!

---

