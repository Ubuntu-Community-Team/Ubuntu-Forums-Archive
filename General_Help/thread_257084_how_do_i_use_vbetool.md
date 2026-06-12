---
title: "how do i use vbetool?"
date: 2006-09-14
forum: General Help
---

### Post by linuxguiri on 2006-09-14
Problem: Video isn't restored 9/10 times after resume from suspend.

I have a Radeon 7500 video card ("radeon" driver on Dapper). I've already tried several changes to /etc/default/acpi-support to no avail. After reading Pavel Machek's ["Video issues with S3 resume"]("http://kernel.org/git/?p=linux/kernel/git/torvalds/linux-2.6.git;a=blob;h=912bed87c758457b2f42b6decb1964326efce3de;hb=3ee68c4af3fd7228c1be63254b9f884614f9ebb2;f=Documentation/power/video.txt"), I'm thinking I need to use vbetool:
> (6) other radeon systems, where vbetool is enough to bring system back to life. Do vbetool vbestate save > /tmp/delme; echo 3 > /proc/acpi/sleep; vbetool post; vbetool vbestate restore < /tmp/delme; setfont <whatever>, and your video should work.

But I have no idea how to go about using vbetool. What does he mean by "Do vbetool vbestate..." Do what where?

Do I put these in the sleep.sh, resume.sh, etc. scripts?

My current /etc/default/acpi-support:

```
ACPI_SLEEP=true
ACPI_HIBERNATE=true
ACPI_SLEEP_MODE=mem
MODULES=""
MODULES_WHITELIST="radeon"
SAVE_VBE_STATE=true
VBESTATE=/var/lib/acpi-support/vbestate
# POST_VIDEO=false
SAVE_VIDEO_PCI_STATE=true
USE_DPMS=true
# RADEON_LIGHT=true
DOUBLE_CONSOLE_SWITCH=true
HIBERNATE_MODE=shutdown
LOCK_SCREEN=true
# DISABLE_DMA=true
# RESET_DRIVE=true
STOP_SERVICES="mysql "
RESTART_IRDA=false
ENABLE_LAPTOP_MODE=false

```

---

### Post by linuxguiri on 2006-09-14
Ok. I was able to get suspend and resume to work using vbetool commands in two scripts from [here]("http://kernel.org/git/?p=linux/kernel/git/torvalds/linux-2.6.git;a=blob;h=912bed87c758457b2f42b6decb1964326efce3de;hb=3ee68c4af3fd7228c1be63254b9f884614f9ebb2;f=Documentation/power/video.txt") and [here]("http://www.gero-hoffmann.de/mambo/index.php?option=com_content&task=view&id=16&Itemid=2").

EDIT: Scripts no longer work. Video is garbled after resume from suspend.

Now how do I incorporate the commands from these scripts into the acpi scripts in /etc/acpi/ so I can simply press a button and suspend without opening a terminal?

Here are the scripts:
saveVideoState.sh (only has to be run once, creates vbe file  in /root/s3/state):
```
#!/bin/bash
statedir=/root/s3/state
mkdir -p $statedir
chvt 2
sleep 1
vbetool vbestate save >$statedir/vbe
```

suspendToRam.sh:
```
#!/bin/bash
statedir=/root/s3/state
curcons=`fgconsole`
fuser /dev/tty$curcons 2>/dev/null|xargs ps -o comm= -p|grep -q X && chvt 2
sync
echo platform > /sys/power/disk; echo mem > /sys/power/state
sync
vbetool post
vbetool vbestate restore <$statedir/vbe
chvt $[curcons%6+1]
chvt $curcons

```

---

