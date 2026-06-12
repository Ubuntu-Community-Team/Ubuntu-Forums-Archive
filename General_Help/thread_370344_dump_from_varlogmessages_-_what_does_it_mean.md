---
title: "dump from /var/log/messages - what does it mean ?"
date: 2007-02-25
forum: General Help
---

### Post by almax00 on 2007-02-25
```
from: /var/log/messages -
Feb 25 12:41:02 black-box kernel: [16965.219538] bd:e5:6c:db:0f:c9:d4:11:f9:3b:94:1a:76:c2:c4:74:
Feb 25 12:41:02 black-box kernel: [16965.219557] e6:4d:37:8b:ef:3d:89:17:
Feb 25 12:41:02 black-box kernel: [16965.219565] 25:7b:56:d1:b4:1b:78:31:
Feb 25 12:46:05 black-box kernel: [17267.972501] 12:11:54:24:39:22:b8:3a:b3:bf:86:d7:74:b9:f6:61:
Feb 25 12:46:05 black-box kernel: [17267.972518] 48:6c:73:24:db:7d:b1:2e:
Feb 25 12:46:05 black-box kernel: [17267.972526] e5:f5:d5:98:e6:3a:06:4a:
Feb 25 12:48:42 black-box kernel: [17568.680337] b2:d1:38:df:28:a1:58:83:e4:3a:61:ee:e7:75:98:d7:
Feb 25 12:48:42 black-box kernel: [17568.680357] 8b:c4:99:e1:c3:58:12:80:
Feb 25 12:48:42 black-box kernel: [17568.680365] 0b:fc:94:05:88:d8:f5:bd:
Feb 25 12:48:52 black-box kernel: [17871.464286] 95:e0:67:81:25:70:7f:0b:be:21:59:00:2d:11:3d:da:
Feb 25 12:48:52 black-box kernel: [17871.464306] 2d:61:4b:c7:6f:e9:2f:2b:
Feb 25 12:48:52 black-box kernel: [17871.464314] f8:31:a0:9f:41:40:7b:1f:
Feb 25 12:49:03 black-box kernel: [18174.217281] e9:8a:fa:d5:96:bf:df:ce:db:50:28:19:9b:53:cd:67:
Feb 25 12:49:03 black-box kernel: [18174.217301] bd:4e:29:3f:bf:74:a9:af:
Feb 25 12:49:03 black-box kernel: [18174.217309] c2:81:98:d1:bf:73:12:f3:
Feb 25 12:49:13 black-box kernel: [18476.960277] 27:21:1e:ac:1d:3d:27:51:07:55:25:6a:68:f9:77:9c:
Feb 25 12:49:13 black-box kernel: [18476.960297] 46:d4:57:1b:51:9e:fc:0e:
Feb 25 12:49:13 black-box kernel: [18476.960305] 13:48:98:8d:b4:ad:fc:4a:
Feb 25 12:49:23 black-box kernel: [18779.713691] 61:06:ea:94:0c:4c:f4:ae:25:87:61:d0:28:5c:0c:4d:
Feb 25 12:49:23 black-box kernel: [18779.713711] 0a:a1:1e:47:69:81:39:5c:
Feb 25 12:49:23 black-box kernel: [18779.713719] 21:4f:35:14:49:3b:85:58:
Feb 25 12:49:33 black-box kernel: [19082.466840] 68:bb:2b:3c:c6:d9:ae:e7:4b:12:70:42:2e:6e:a7:82:
Feb 25 12:49:33 black-box kernel: [19082.466859] 9f:4d:1e:25:e8:52:1d:74:
Feb 25 12:49:33 black-box kernel: [19082.466867] e1:ec:6f:cb:95:c9:d8:7c:
Feb 25 12:49:43 black-box kernel: [19385.230390] f4:eb:e0:11:fa:14:9d:ff:76:23:82:e8:c5:03:c9:5a:
Feb 25 12:49:43 black-box kernel: [19385.230410] 7f:f8:23:e8:fa:de:a5:88:
Feb 25 12:49:43 black-box kernel: [19385.230418] be:66:35:b9:27:f9:6f:8e:
Feb 25 12:49:53 black-box kernel: [19687.983864] 67:10:67:88:00:20:39:78:72:30:6c:55:06:e4:f6:71:
Feb 25 12:49:53 black-box kernel: [19687.983883] 84:31:1d:19:ff:84:5f:4a:
Feb 25 12:49:53 black-box kernel: [19687.983891] 00:a7:64:22:99:1a:cf:a3:
Feb 25 12:50:03 black-box kernel: [19990.747393] 62:87:69:da:00:a9:4c:41:51:35:bc:2f:4f:cd:2f:78:
Feb 25 12:50:03 black-box kernel: [19990.747413] 9f:8c:53:77:5c:c6:39:8d:
Feb 25 12:50:03 black-box kernel: [19990.747421] 28:71:42:47:6e:15:c5:05:
Feb 25 12:50:14 black-box kernel: [20291.455040] fa:6b:7f:8a:bb:6d:83:0c:c6:da:5d:5c:d7:12:a8:af:
Feb 25 12:50:14 black-box kernel: [20291.455060] 57:a0:01:64:83:b9:31:15:
Feb 25 12:50:14 black-box kernel: [20291.455068] 9d:a5:a4:81:5f:6c:4d:18:
Feb 25 12:50:24 black-box kernel: [20594.218504] 61:ca:e2:47:a7:33:12:45:02:ed:f7:8c:70:05:c9:a3:
Feb 25 12:50:24 black-box kernel: [20594.218523] 42:12:cd:5a:92:db:ad:f2:
Feb 25 12:50:24 black-box kernel: [20594.218532] 3a:0e:40:9e:42:32:e7:78:
Feb 25 12:50:32 black-box kernel: [20896.961694] 67:19:d6:aa:7d:62:d0:f1:cb:f9:a3:74:5f:f2:35:f4:
Feb 25 12:50:32 black-box kernel: [20896.961713] 64:80:12:3c:77:f4:99:49:
Feb 25 12:50:32 black-box kernel: [20896.961722] 77:fe:37:0a:95:69:7f:af:
Feb 25 12:50:44 black-box kernel: [21199.735456] 0a:14:fc:46:be:66:1a:3a:44:0a:56:b8:25:36:c5:eb:
Feb 25 12:50:44 black-box kernel: [21199.735476] 14:4a:60:53:7e:f9:32:cc:
Feb 25 12:50:44 black-box kernel: [21199.735484] 31:df:fb:e0:21:85:72:61:
Feb 25 12:50:54 black-box kernel: [21502.488695] 01:40:f4:35:a6:71:14:d0:14:ed:e6:9b:3a:54:db:3b:
Feb 25 12:50:54 black-box kernel: [21502.488714] 55:ff:fb:a3:32:c5:b7:04:
Feb 25 12:50:54 black-box kernel: [21502.488723] 7d:81:8d:1e:29:ce:fb:18:
Feb 25 12:51:02 black-box kernel: [21805.252139] 09:88:78:25:3f:67:ef:7a:11:1f:69:a8:2f:3d:76:88:
Feb 25 12:51:02 black-box kernel: [21805.252157] 69:08:5a:02:be:dc:c5:9e:
Feb 25 12:51:02 black-box kernel: [21805.252166] f7:8e:a8:2c:42:20:53:9b:
Feb 25 12:51:14 black-box kernel: [22108.005664] e2:40:43:f8:91:f2:67:0a:73:ed:47:cd:ab:3b:f4:d8:
Feb 25 12:51:14 black-box kernel: [22108.005682] 73:d0:6b:3b:0a:52:ba:0d:
Feb 25 12:51:14 black-box kernel: [22108.005690] 7c:cf:50:04:61:92:94:20:
Feb 25 12:51:25 black-box kernel: [22410.769078] 7c:4f:ca:6a:cb:0d:7d:e4:33:7d:73:8b:64:4a:d8:64:
Feb 25 12:51:25 black-box kernel: [22410.769097] 32:56:09:90:f8:01:42:f5:
Feb 25 12:51:25 black-box kernel: [22410.769105] d7:a6:55:66:76:2d:97:d0:
Feb 25 12:51:33 black-box kernel: [22711.466491] 2c:af:3c:0a:7d:b6:e4:8a:6c:2d:df:72:24:33:7a:cd:
Feb 25 12:51:33 black-box kernel: [22711.466510] 1e:2b:d5:dd:5a:fb:ca:7e:
Feb 25 12:51:33 black-box kernel: [22711.466518] 37:cf:3b:37:68:9e:d2:19:
Feb 25 12:51:43 black-box kernel: [23012.194821] 55:01:d3:c3:e5:4c:9d:0f:bd:81:3b:1e:39:92:fb:72:
Feb 25 12:51:43 black-box kernel: [23012.194839] 76:e9:95:1a:6c:4c:e6:0f:
Feb 25 12:51:43 black-box kernel: [23012.194847] 38:2a:a2:9a:7b:f4:1d:52:
Feb 25 12:51:55 black-box kernel: [23314.948007] 3b:93:50:1f:a4:42:36:29:c9:37:68:5e:0c:87:0c:69:
Feb 25 12:51:55 black-box kernel: [23314.948026] 53:6b:07:26:3d:b2:eb:67:
Feb 25 12:51:55 black-box kernel: [23314.948034] 1c:bf:87:fb:52:0a:dd:2d:
Feb 25 12:52:05 black-box kernel: [23617.711488] 69:5f:df:18:a6:29:f5:68:5a:bc:56:b3:8b:1d:31:33:
Feb 25 12:52:05 black-box kernel: [23617.711506] 4a:2a:e0:9b:c6:ce:a5:f5:
Feb 25 12:52:05 black-box kernel: [23617.711515] 70:e6:c8:94:ef:f8:3c:81:
Feb 25 12:52:13 black-box kernel: [23920.465047] ef:4c:ed:30:79:a6:87:3f:03:9c:cb:04:14:d0:eb:7f:
Feb 25 12:52:13 black-box kernel: [23920.465065] 26:26:40:44:47:af:ef:af:
Feb 25 12:52:13 black-box kernel: [23920.465074] 9e:f1:d3:d2:73:87:17:93:
Feb 25 12:56:59 black-box kernel: [24223.228498] 27:c9:74:37:93:33:a8:f5:f5:0b:2c:7a:70:ee:22:ee:
Feb 25 12:56:59 black-box kernel: [24223.228517] 56:1b:78:5e:90:34:a0:6a:
Feb 25 12:56:59 black-box kernel: [24223.228525] ca:ae:c5:8f:2d:80:b1:8d:
Feb 25 13:02:12 black-box kernel: [24525.982173] 7e:2f:dd:cb:bc:7d:60:d7:ed:f9:91:16:4c:40:32:1e:
Feb 25 13:02:12 black-box kernel: [24525.982191] 0a:dd:f4:7e:66:0e:ae:71:
Feb 25 13:02:12 black-box kernel: [24525.982200] 35:6c:ba:46:1d:a6:51:83:
Feb 25 14:52:29 black-box kernel: [24828.746063] f0:e7:d1:db:a3:86:cf:e6:79:de:68:d1:3a:72:9c:12:
Feb 25 14:52:29 black-box kernel: [24828.746080] f5:96:ae:2b:83:4d:26:bc:
Feb 25 14:52:29 black-box kernel: [24828.746089] 42:09:4d:f2:de:c9:74:2a:
Feb 25 14:57:42 black-box kernel: [25131.498469] 36:1e:fa:85:17:10:7a:f1:e8:0e:05:36:6a:5c:36:00:
Feb 25 14:57:42 black-box kernel: [25131.498488] 6b:0f:b7:27:73:d2:f2:5a:
Feb 25 14:57:42 black-box kernel: [25131.498496] b1:f9:82:23:99:8c:f9:f8:
```

any idea what this means ? i get new lines every 5 minutes...until 13:02 when it was supposed to start the screensaver i think because was away from it and at 14:52 i had to restart the xserver because the time was wrong but the system was not locked because i could move the cursor but couldn't click anything or launch apps. xorg below:

```
Section "Device"
        Identifier      "Radeon 7500"
        Driver          "ati"
        BusID           "PCI:1:0:0"
        Option          "XAANoOffscreenPixmaps"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-64
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Radeon 7500"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Option          "AIGLX" "true"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus" "SendCoreEvents"
        InputDevice     "cursor" "SendCoreEvents"
        InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
        Mode    0666
EndSection

Section "Extensions"
        Option "Composite" "Enable"
```

is it an xorg problem ? or something else ? (that gives the output in /var/log/messages)
edgy ibm netvista 2.0 P4 512 ati 7500 gigabyte pci wifi nic

---

### Post by apjone on 2007-02-25
not sure, but it is definatly hex. have you tried dmesg ? also try running top in a terminal

---

### Post by almax00 on 2007-02-25
apjone: thanks for the reply.

dmesg has the same hex output at the end. the hex starts after the comment about IVv6:

[   39.809261] input: /usr/sbin/thinkpad-keys as /class/input/input3
[   41.957576] NET: Registered protocol family 10
[   41.957716] lo: Disabled Privacy Extensions
[   41.957914] IPv6 over IPv4 tunneling driver                   
[   47.763120] 06:60:3e:5a:58:d4:a8:68:87:ab:e6:eb:62:ad:6f:4a:
[   47.763139] d0:ff:a8:19:88:3d:84:84:
[   47.763147] 88:ce:34:20:19:6f:27:78:

i thought i had disabled IPv6 -- maybe it is still active ??

---

### Post by apjone on 2007-02-26
I really have no idea. Sorry.  Are you having any sort of performance problems. I have had it where you can move the cursor but cant click, I just killed gone-panel and i was able to click and continue.

---

### Post by almax00 on 2007-02-27
no performance problems. i was using the default ati driver and it was causing a "soft" lockup after a period of inactivity but i think it is fixed by installing a different driver.

---

