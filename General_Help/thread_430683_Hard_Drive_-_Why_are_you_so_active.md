---
title: "Hard Drive - Why are you so active?"
date: 2007-05-02
forum: General Help
---

### Post by verevi on 2007-05-02
My Hard Drive is going to town randomly (like Windows sometimes does).  I looked at 'top' and noticed a 'dd' command.  Is this the culprit?  And what is this doing?

/bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg

Also, syslogd is taking up a lot of CPU cycles right now.  Maybe its just a log rotation?  But, man, the HD is going crazy!

Thanks for the help....

---

### Post by mbeierl on 2007-05-02
Something is generating tons of system event logs.  Try doing this:
```
tail -f /var/log/messages
```
and see if that sheds any light on what's going on.

---

### Post by verevi on 2007-05-02
ah... lots of this while trying to play a DVD.  I think I have it working now (I installed what I needed to play the DVD.  So so automatic as everything else is in Fiesty).

```
May  2 10:19:12 xxxxx-desktop kernel: [37312.552000] end_request: I/O error, dev hdc, sector 6683264
May  2 10:19:12 xxxxx-desktop kernel: [37312.604000] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
May  2 10:19:12 xxxxx-desktop kernel: [37312.604000] hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
May  2 10:19:12 xxxxx-desktop kernel: [37312.604000] ide: failed opcode was: unknown
```I guess its not a problem now.  Thanks for clearing that mystery up!

---

