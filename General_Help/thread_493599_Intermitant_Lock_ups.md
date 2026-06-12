---
title: "Intermitant Lock ups"
date: 2007-07-05
forum: General Help
---

### Post by f4hy on 2007-07-05
So my desktop has become unusable due to random lock ups. I they happen more often when under load then when idle. For a long time I thought it was just my video card over heating, but I threw in an extra HD installed XP and it runs cool and stable even under huge load.  So it is something wrong with my ubuntu install.

Here is the tail of /var/log/messages
```
Jul  5 17:34:21 f4hy-desktop gconfd (f4hy-6068): starting (version 2.18.0.1), pid 6068 user 'f4hy'
Jul  5 17:34:21 f4hy-desktop gconfd (f4hy-6068): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Jul  5 17:34:21 f4hy-desktop gconfd (f4hy-6068): Resolved address "xml:readwrite:/home/f4hy/.gconf" to a writable configuration source at position 1
Jul  5 17:34:21 f4hy-desktop gconfd (f4hy-6068): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Jul  5 17:34:21 f4hy-desktop gconfd (f4hy-6068): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Jul  5 17:34:21 f4hy-desktop gconfd (f4hy-6068): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Jul  5 17:34:24 f4hy-desktop gconfd (f4hy-6068): Resolved address "xml:readwrite:/home/f4hy/.gconf" to a writable configuration source at position 0
Jul  5 17:34:28 f4hy-desktop kernel: [ 1650.142650] IN= OUT=vmnet1 SRC=192.168.31.1 DST=192.168.31.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=58 
Jul  5 17:34:28 f4hy-desktop kernel: [ 1650.142870] IN= OUT=vmnet8 SRC=192.168.180.1 DST=192.168.180.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=58 
Jul  5 17:34:29 f4hy-desktop kernel: [ 1651.122649] Unable to identify CD-ROM format.
Jul  5 17:34:33 f4hy-desktop kernel: [ 1655.642433] hdc: packet command error: status=0x51 { DriveReady SeekComplete Error }
Jul  5 17:34:33 f4hy-desktop kernel: [ 1655.642443] hdc: packet command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
Jul  5 17:34:33 f4hy-desktop kernel: [ 1655.642447] ide: failed opcode was: unknown
```

I am not really sure what the .gconf error messages mean. I have read [other threads]("http://ubuntuforums.org/showthread.php?p=2963469") that chalked it up to video cards over heating. I used to think so but now it happens when not doing anything graphical. I am out of ideas so wondering if anyone knows why it would throw those messages.

---

