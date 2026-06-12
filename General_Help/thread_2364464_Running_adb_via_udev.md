---
title: "Running adb via udev"
date: 2017-06-23
forum: General Help
---

### Post by paque on 2017-06-23
Hi Team,

I am writing a bash script that will run upon plugging my Android phone into my Ubuntu 16.04 laptop. I am stuck at the point where the script runs fine when I execute it manually from a terminal session, but it fails when I try to have it automatically run via a udev rule.

The content of /etc/udev/rules.d/99-android.rules is:
```
ACTION=="add", ATTRS{idVendor}=="04e8", ATTRS{idProduct}=="6860", MODE="0666", RUN+="/data/personal/backup/backup_galaxya5_start"
```

The content of /data/personal/backup/backup_galaxya5_start is:
```
#!/bin/bash
sudo -u marc echo /data/personal/backup/backup_galaxya5 | at now
```

The content of /data/personal/backup/backup_galaxya5 is a whole heap of things, but it essentially boils down to:
```
adb start-server
adb push /data/download/rsync4android/rsync.bin /data/local/tmp/rsync >> "$LOGFILE"
adb shell chmod 755 /data/local/tmp/rsync >> "$LOGFILE"
adb shell 'exec >/data/local/tmp/rsyncd.conf && echo address = 127.0.0.1 && echo port = 1873 && echo "[root]" && echo path = / && echo use chroot = false && echo read only = false' >> "$LOGFILE"
adb shell /data/local/tmp/rsync --daemon --no-detach --config=/data/local/tmp/rsyncd.conf --log-file=/proc/self/fd/2 & >> "$LOGFILE"
adb forward tcp:6010 tcp:1873
rsync -av --exclude .thumbnails/ "rsync://localhost:6010/root/sdcard/DCIM/" "$TARGETDIR" > "$RSYNCLOGFILE"
```

As I said, running this when the phone is plugged in from a terminal works without any problems. However, when I plug the phone in to have the script run automatically, the following happens:
1. The udev rule picks up the fact that the phone was plugged in and executes /data/personal/backup/backup_galaxya5_start.
2. That file uses the at command the schedule the actual backup script to run.
3. The actual backup script runs and starts the adb server.
4. The backup script is then unable to copy the rsync.bin file to the phone.
5. The subsequent adb commands are failing as well.

At some point I even changed the script to pickup the failed "adb push" command and then do a "adb kill-server", however this also did not help.

I am probably over-complicating things (as someone has told me in the past) however I would still like to know what I am missing in order to make this work.

Thank you in advance for your suggestions.

Marc.

---

