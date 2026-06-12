---
title: "Ubuntu Started Being Really Slow On Startup And Even After It And Randomly Freezes"
date: 2024-09-14
forum: General Help
---

### Post by sikasevoid on 2024-09-14
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=294233&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=294234&stc=1[/IMG]Today My Ubuntu Del Laptop Started Having New Errors On Startup And Now It Takes Forever To Start It Up Now + The Logging In Takes Longer Too I Noticed And After Logging In There Are Random Freezes  That I Have To Restart Computer To Fix Only Holding Down The Power Button Seemed To Work And Reisub
My Friend Tried To Help And Asked For Logs Using Journalctl -xe 
But Could Not Help Because They Were Not That Familiar With Ubuntu
```
sikase@sikase-Dell-G15-5510:~$ journalctl -xeSep 14 17:31:49 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/64>
Sep 14 17:31:54 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/64>
Sep 14 17:31:54 sikase-Dell-G15-5510 kernel: usb usb1-port5: attempt power cycle
Sep 14 17:31:55 sikase-Dell-G15-5510 kernel: usb 1-5: new high-speed USB device>
Sep 14 17:32:00 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/8,>
Sep 14 17:32:00 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/8,>
Sep 14 17:32:00 sikase-Dell-G15-5510 kernel: usb 1-5: new high-speed USB device>
Sep 14 17:32:05 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/8,>
Sep 14 17:32:05 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/8,>
Sep 14 17:32:05 sikase-Dell-G15-5510 kernel: usb usb1-port5: unable to enumerat>
Sep 14 17:32:06 sikase-Dell-G15-5510 kernel: usb 1-5: new high-speed USB device>
Sep 14 17:32:11 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/64>
Sep 14 17:32:16 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/64>
Sep 14 17:32:16 sikase-Dell-G15-5510 kernel: usb 1-5: new high-speed USB device>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning:>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning:>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning:>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning:>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning:>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning:>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning:>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning:>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning:>
lines 1562-1584/1584 (END)
Sep 14 17:31:49 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/64>
Sep 14 17:31:54 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/64>
Sep 14 17:31:54 sikase-Dell-G15-5510 kernel: usb usb1-port5: attempt power cycle
Sep 14 17:31:55 sikase-Dell-G15-5510 kernel: usb 1-5: new high-speed USB device>
Sep 14 17:32:00 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/8,>
Sep 14 17:32:00 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/8,>
Sep 14 17:32:00 sikase-Dell-G15-5510 kernel: usb 1-5: new high-speed USB device>
Sep 14 17:32:05 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/8,>
Sep 14 17:32:05 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/8,>
Sep 14 17:32:05 sikase-Dell-G15-5510 kernel: usb usb1-port5: unable to enumerat>
Sep 14 17:32:06 sikase-Dell-G15-5510 kernel: usb 1-5: new high-speed USB device>
Sep 14 17:32:11 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/64>
Sep 14 17:32:16 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/64>
Sep 14 17:32:16 sikase-Dell-G15-5510 kernel: usb 1-5: new high-speed USB device>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning:>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning:>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning:>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning:>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning:>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning:>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning:>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning:>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning:>
~
lines 1562-1584/1584 (END)
Sep 14 17:31:49 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/64,>
Sep 14 17:31:54 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/64,>
Sep 14 17:31:54 sikase-Dell-G15-5510 kernel: usb usb1-port5: attempt power cycle
Sep 14 17:31:55 sikase-Dell-G15-5510 kernel: usb 1-5: new high-speed USB device >
Sep 14 17:32:00 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/8, >
Sep 14 17:32:00 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/8, >
Sep 14 17:32:00 sikase-Dell-G15-5510 kernel: usb 1-5: new high-speed USB device >
Sep 14 17:32:05 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/8, >
Sep 14 17:32:05 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/8, >
Sep 14 17:32:05 sikase-Dell-G15-5510 kernel: usb usb1-port5: unable to enumerate>
Sep 14 17:32:06 sikase-Dell-G15-5510 kernel: usb 1-5: new high-speed USB device >
Sep 14 17:32:11 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/64,>
Sep 14 17:32:16 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/64,>
Sep 14 17:32:16 sikase-Dell-G15-5510 kernel: usb 1-5: new high-speed USB device >
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: >
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: >
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: >
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: >
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: >
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: >
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: >
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: >
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: >
~
~
~
lines 1562-1584/1584 (END)






Sep 14 17:31:49 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/64,>
Sep 14 17:31:54 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/64,>
Sep 14 17:31:54 sikase-Dell-G15-5510 kernel: usb usb1-port5: attempt power cycle
Sep 14 17:31:55 sikase-Dell-G15-5510 kernel: usb 1-5: new high-speed USB device >
Sep 14 17:32:00 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/8, >
Sep 14 17:32:00 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/8, >
Sep 14 17:32:00 sikase-Dell-G15-5510 kernel: usb 1-5: new high-speed USB device >
Sep 14 17:32:05 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/8, >
Sep 14 17:32:05 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/8, >
Sep 14 17:32:05 sikase-Dell-G15-5510 kernel: usb usb1-port5: unable to enumerate>
Sep 14 17:32:06 sikase-Dell-G15-5510 kernel: usb 1-5: new high-speed USB device >
Sep 14 17:32:11 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/64,>
Sep 14 17:32:16 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/64,>
Sep 14 17:32:16 sikase-Dell-G15-5510 kernel: usb 1-5: new high-speed USB device >
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: >
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: >
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: >
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: >
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: >
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: >
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: >
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: >
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: >
~
~
~
~
lines 1562-1584/1584 (END)




Sep 14 17:31:49 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/64, >
Sep 14 17:31:54 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/64, >
Sep 14 17:31:54 sikase-Dell-G15-5510 kernel: usb usb1-port5: attempt power cycle
Sep 14 17:31:55 sikase-Dell-G15-5510 kernel: usb 1-5: new high-speed USB device n>
Sep 14 17:32:00 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/8, e>
Sep 14 17:32:00 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/8, e>
Sep 14 17:32:00 sikase-Dell-G15-5510 kernel: usb 1-5: new high-speed USB device n>
Sep 14 17:32:05 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/8, e>
Sep 14 17:32:05 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/8, e>
Sep 14 17:32:05 sikase-Dell-G15-5510 kernel: usb usb1-port5: unable to enumerate >
Sep 14 17:32:06 sikase-Dell-G15-5510 kernel: usb 1-5: new high-speed USB device n>
Sep 14 17:32:11 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/64, >
Sep 14 17:32:16 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/64, >
Sep 14 17:32:16 sikase-Dell-G15-5510 kernel: usb 1-5: new high-speed USB device n>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: O>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: O>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: O>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: O>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: O>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: O>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: O>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: O>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: O>
~
~
~
~
~
~
lines 1562-1584/1584 (END)
Sep 14 17:31:49 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/64, e>
Sep 14 17:31:54 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/64, e>
Sep 14 17:31:54 sikase-Dell-G15-5510 kernel: usb usb1-port5: attempt power cycle
Sep 14 17:31:55 sikase-Dell-G15-5510 kernel: usb 1-5: new high-speed USB device nu>
Sep 14 17:32:00 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/8, er>
Sep 14 17:32:00 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/8, er>
Sep 14 17:32:00 sikase-Dell-G15-5510 kernel: usb 1-5: new high-speed USB device nu>
Sep 14 17:32:05 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/8, er>
Sep 14 17:32:05 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/8, er>
Sep 14 17:32:05 sikase-Dell-G15-5510 kernel: usb usb1-port5: unable to enumerate U>
Sep 14 17:32:06 sikase-Dell-G15-5510 kernel: usb 1-5: new high-speed USB device nu>
Sep 14 17:32:11 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/64, e>
Sep 14 17:32:16 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/64, e>
Sep 14 17:32:16 sikase-Dell-G15-5510 kernel: usb 1-5: new high-speed USB device nu>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: Ov>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: Ov>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: Ov>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: Ov>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: Ov>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: Ov>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: Ov>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: Ov>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: Ov>
~
~
~
~
~
~
~
~
lines 1562-1584/1584 (END)


Sep 14 17:31:49 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/64, er>
Sep 14 17:31:54 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/64, er>
Sep 14 17:31:54 sikase-Dell-G15-5510 kernel: usb usb1-port5: attempt power cycle
Sep 14 17:31:55 sikase-Dell-G15-5510 kernel: usb 1-5: new high-speed USB device num>
Sep 14 17:32:00 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/8, err>
Sep 14 17:32:00 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/8, err>
Sep 14 17:32:00 sikase-Dell-G15-5510 kernel: usb 1-5: new high-speed USB device num>
Sep 14 17:32:05 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/8, err>
Sep 14 17:32:05 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/8, err>
Sep 14 17:32:05 sikase-Dell-G15-5510 kernel: usb usb1-port5: unable to enumerate US>
Sep 14 17:32:06 sikase-Dell-G15-5510 kernel: usb 1-5: new high-speed USB device num>
Sep 14 17:32:11 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/64, er>
Sep 14 17:32:16 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/64, er>
Sep 14 17:32:16 sikase-Dell-G15-5510 kernel: usb 1-5: new high-speed USB device num>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: Ove>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: Ove>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: Ove>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: Ove>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: Ove>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: Ove>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: Ove>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: Ove>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: Ove>
~
~
~
~
~
~
~
~
~
lines 1562-1584/1584 (END)
Sep 14 17:31:49 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/64, erro>
Sep 14 17:31:54 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/64, erro>
Sep 14 17:31:54 sikase-Dell-G15-5510 kernel: usb usb1-port5: attempt power cycle
Sep 14 17:31:55 sikase-Dell-G15-5510 kernel: usb 1-5: new high-speed USB device numbe>
Sep 14 17:32:00 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/8, error>
Sep 14 17:32:00 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/8, error>
Sep 14 17:32:00 sikase-Dell-G15-5510 kernel: usb 1-5: new high-speed USB device numbe>
Sep 14 17:32:05 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/8, error>
Sep 14 17:32:05 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/8, error>
Sep 14 17:32:05 sikase-Dell-G15-5510 kernel: usb usb1-port5: unable to enumerate USB >
Sep 14 17:32:06 sikase-Dell-G15-5510 kernel: usb 1-5: new high-speed USB device numbe>
Sep 14 17:32:11 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/64, erro>
Sep 14 17:32:16 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/64, erro>
Sep 14 17:32:16 sikase-Dell-G15-5510 kernel: usb 1-5: new high-speed USB device numbe>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: Overw>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: Overw>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: Overw>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: Overw>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: Overw>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: Overw>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: Overw>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: Overw>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: Overw>
~
~
~
~
~
~
~
~
~
~
~
lines 1562-1584/1584 (END)


Sep 14 17:31:49 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/64, erro>
Sep 14 17:31:54 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/64, erro>
Sep 14 17:31:54 sikase-Dell-G15-5510 kernel: usb usb1-port5: attempt power cycle
Sep 14 17:31:55 sikase-Dell-G15-5510 kernel: usb 1-5: new high-speed USB device numbe>
Sep 14 17:32:00 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/8, error>
Sep 14 17:32:00 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/8, error>
Sep 14 17:32:00 sikase-Dell-G15-5510 kernel: usb 1-5: new high-speed USB device numbe>
Sep 14 17:32:05 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/8, error>
Sep 14 17:32:05 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/8, error>
Sep 14 17:32:05 sikase-Dell-G15-5510 kernel: usb usb1-port5: unable to enumerate USB >
Sep 14 17:32:06 sikase-Dell-G15-5510 kernel: usb 1-5: new high-speed USB device numbe>
Sep 14 17:32:11 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/64, erro>
Sep 14 17:32:16 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/64, erro>
Sep 14 17:32:16 sikase-Dell-G15-5510 kernel: usb 1-5: new high-speed USB device numbe>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: Overw>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: Overw>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: Overw>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: Overw>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: Overw>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: Overw>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: Overw>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: Overw>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: Overw>
~
~
~
~
~
~
~
~
~
~
~
~
lines 1562-1584/1584 (END)
Sep 14 17:31:49 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/64, error>
Sep 14 17:31:54 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/64, error>
Sep 14 17:31:54 sikase-Dell-G15-5510 kernel: usb usb1-port5: attempt power cycle
Sep 14 17:31:55 sikase-Dell-G15-5510 kernel: usb 1-5: new high-speed USB device number>
Sep 14 17:32:00 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/8, error >
Sep 14 17:32:00 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/8, error >
Sep 14 17:32:00 sikase-Dell-G15-5510 kernel: usb 1-5: new high-speed USB device number>
Sep 14 17:32:05 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/8, error >
Sep 14 17:32:05 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/8, error >
Sep 14 17:32:05 sikase-Dell-G15-5510 kernel: usb usb1-port5: unable to enumerate USB d>
Sep 14 17:32:06 sikase-Dell-G15-5510 kernel: usb 1-5: new high-speed USB device number>
Sep 14 17:32:11 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/64, error>
Sep 14 17:32:16 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/64, error>
Sep 14 17:32:16 sikase-Dell-G15-5510 kernel: usb 1-5: new high-speed USB device number>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: Overwr>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: Overwr>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: Overwr>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: Overwr>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: Overwr>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: Overwr>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: Overwr>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: Overwr>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: Overwr>
~
~
~
~
~
~
~
~
~
~
~
~
~
~
lines 1562-1584/1584 (END)


Sep 14 17:31:49 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/64, error>
Sep 14 17:31:54 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/64, error>
Sep 14 17:31:54 sikase-Dell-G15-5510 kernel: usb usb1-port5: attempt power cycle
Sep 14 17:31:55 sikase-Dell-G15-5510 kernel: usb 1-5: new high-speed USB device number>
Sep 14 17:32:00 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/8, error >
Sep 14 17:32:00 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/8, error >
Sep 14 17:32:00 sikase-Dell-G15-5510 kernel: usb 1-5: new high-speed USB device number>
Sep 14 17:32:05 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/8, error >
Sep 14 17:32:05 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/8, error >
Sep 14 17:32:05 sikase-Dell-G15-5510 kernel: usb usb1-port5: unable to enumerate USB d>
Sep 14 17:32:06 sikase-Dell-G15-5510 kernel: usb 1-5: new high-speed USB device number>
Sep 14 17:32:11 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/64, error>
Sep 14 17:32:16 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/64, error>
Sep 14 17:32:16 sikase-Dell-G15-5510 kernel: usb 1-5: new high-speed USB device number>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: Overwr>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: Overwr>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: Overwr>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: Overwr>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: Overwr>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: Overwr>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: Overwr>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: Overwr>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: Overwr>
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
lines 1562-1584/1584 (END)
Sep 14 17:31:49 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/64, error >
Sep 14 17:31:54 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/64, error >
Sep 14 17:31:54 sikase-Dell-G15-5510 kernel: usb usb1-port5: attempt power cycle
Sep 14 17:31:55 sikase-Dell-G15-5510 kernel: usb 1-5: new high-speed USB device number >
Sep 14 17:32:00 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/8, error ->
Sep 14 17:32:00 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/8, error ->
Sep 14 17:32:00 sikase-Dell-G15-5510 kernel: usb 1-5: new high-speed USB device number >
Sep 14 17:32:05 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/8, error ->
Sep 14 17:32:05 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/8, error ->
Sep 14 17:32:05 sikase-Dell-G15-5510 kernel: usb usb1-port5: unable to enumerate USB de>
Sep 14 17:32:06 sikase-Dell-G15-5510 kernel: usb 1-5: new high-speed USB device number >
Sep 14 17:32:11 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/64, error >
Sep 14 17:32:16 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/64, error >
Sep 14 17:32:16 sikase-Dell-G15-5510 kernel: usb 1-5: new high-speed USB device number >
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: Overwri>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: Overwri>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: Overwri>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: Overwri>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: Overwri>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: Overwri>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: Overwri>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: Overwri>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: Overwri>
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
lines 1562-1584/1584 (END)


Sep 14 17:31:49 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/64, error >
Sep 14 17:31:54 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/64, error >
Sep 14 17:31:54 sikase-Dell-G15-5510 kernel: usb usb1-port5: attempt power cycle
Sep 14 17:31:55 sikase-Dell-G15-5510 kernel: usb 1-5: new high-speed USB device number >
Sep 14 17:32:00 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/8, error ->
Sep 14 17:32:00 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/8, error ->
Sep 14 17:32:00 sikase-Dell-G15-5510 kernel: usb 1-5: new high-speed USB device number >
Sep 14 17:32:05 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/8, error ->
Sep 14 17:32:05 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/8, error ->
Sep 14 17:32:05 sikase-Dell-G15-5510 kernel: usb usb1-port5: unable to enumerate USB de>
Sep 14 17:32:06 sikase-Dell-G15-5510 kernel: usb 1-5: new high-speed USB device number >
Sep 14 17:32:11 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/64, error >
Sep 14 17:32:16 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/64, error >
Sep 14 17:32:16 sikase-Dell-G15-5510 kernel: usb 1-5: new high-speed USB device number >
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: Overwri>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: Overwri>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: Overwri>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: Overwri>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: Overwri>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: Overwri>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: Overwri>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: Overwri>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: Overwri>
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
lines 1562-1584/1584 (END)
Sep 14 17:31:49 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/64, error ->
Sep 14 17:31:54 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/64, error ->
Sep 14 17:31:54 sikase-Dell-G15-5510 kernel: usb usb1-port5: attempt power cycle
Sep 14 17:31:55 sikase-Dell-G15-5510 kernel: usb 1-5: new high-speed USB device number 8>
Sep 14 17:32:00 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/8, error -71
Sep 14 17:32:00 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/8, error -71
Sep 14 17:32:00 sikase-Dell-G15-5510 kernel: usb 1-5: new high-speed USB device number 8>
Sep 14 17:32:05 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/8, error -71
Sep 14 17:32:05 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/8, error -71
Sep 14 17:32:05 sikase-Dell-G15-5510 kernel: usb usb1-port5: unable to enumerate USB dev>
Sep 14 17:32:06 sikase-Dell-G15-5510 kernel: usb 1-5: new high-speed USB device number 8>
Sep 14 17:32:11 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/64, error ->
Sep 14 17:32:16 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/64, error ->
Sep 14 17:32:16 sikase-Dell-G15-5510 kernel: usb 1-5: new high-speed USB device number 8>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: Overwrit>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: Overwrit>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: Overwrit>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: Overwrit>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: Overwrit>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: Overwrit>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: Overwrit>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: Overwrit>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: Overwrit>
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
lines 1562-1584/1584 (END)


Sep 14 17:31:49 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/64, error ->
Sep 14 17:31:54 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/64, error ->
Sep 14 17:31:54 sikase-Dell-G15-5510 kernel: usb usb1-port5: attempt power cycle
Sep 14 17:31:55 sikase-Dell-G15-5510 kernel: usb 1-5: new high-speed USB device number 8>
Sep 14 17:32:00 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/8, error -71
Sep 14 17:32:00 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/8, error -71
Sep 14 17:32:00 sikase-Dell-G15-5510 kernel: usb 1-5: new high-speed USB device number 8>
Sep 14 17:32:05 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/8, error -71
Sep 14 17:32:05 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/8, error -71
Sep 14 17:32:05 sikase-Dell-G15-5510 kernel: usb usb1-port5: unable to enumerate USB dev>
Sep 14 17:32:06 sikase-Dell-G15-5510 kernel: usb 1-5: new high-speed USB device number 8>
Sep 14 17:32:11 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/64, error ->
Sep 14 17:32:16 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/64, error ->
Sep 14 17:32:16 sikase-Dell-G15-5510 kernel: usb 1-5: new high-speed USB device number 8>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: Overwrit>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: Overwrit>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: Overwrit>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: Overwrit>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: Overwrit>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: Overwrit>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: Overwrit>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: Overwrit>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: Overwrit>
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
lines 1562-1584/1584 (END)
Sep 14 17:31:49 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/64, error ->
Sep 14 17:31:54 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/64, error ->
Sep 14 17:31:54 sikase-Dell-G15-5510 kernel: usb usb1-port5: attempt power cycle
Sep 14 17:31:55 sikase-Dell-G15-5510 kernel: usb 1-5: new high-speed USB device number 8>
Sep 14 17:32:00 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/8, error -71
Sep 14 17:32:00 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/8, error -71
Sep 14 17:32:00 sikase-Dell-G15-5510 kernel: usb 1-5: new high-speed USB device number 8>
Sep 14 17:32:05 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/8, error -71
Sep 14 17:32:05 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/8, error -71
Sep 14 17:32:05 sikase-Dell-G15-5510 kernel: usb usb1-port5: unable to enumerate USB dev>
Sep 14 17:32:06 sikase-Dell-G15-5510 kernel: usb 1-5: new high-speed USB device number 8>
Sep 14 17:32:11 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/64, error ->
Sep 14 17:32:16 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/64, error ->
Sep 14 17:32:16 sikase-Dell-G15-5510 kernel: usb 1-5: new high-speed USB device number 8>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: Overwrit>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: Overwrit>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: Overwrit>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: Overwrit>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: Overwrit>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: Overwrit>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: Overwrit>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: Overwrit>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: Overwrit>
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
lines 1562-1584/1584 (END)
Sep 14 17:31:49 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/64, error >
Sep 14 17:31:54 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/64, error >
Sep 14 17:31:54 sikase-Dell-G15-5510 kernel: usb usb1-port5: attempt power cycle
Sep 14 17:31:55 sikase-Dell-G15-5510 kernel: usb 1-5: new high-speed USB device number >
Sep 14 17:32:00 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/8, error ->
Sep 14 17:32:00 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/8, error ->
Sep 14 17:32:00 sikase-Dell-G15-5510 kernel: usb 1-5: new high-speed USB device number >
Sep 14 17:32:05 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/8, error ->
Sep 14 17:32:05 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/8, error ->
Sep 14 17:32:05 sikase-Dell-G15-5510 kernel: usb usb1-port5: unable to enumerate USB de>
Sep 14 17:32:06 sikase-Dell-G15-5510 kernel: usb 1-5: new high-speed USB device number >
Sep 14 17:32:11 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/64, error >
Sep 14 17:32:16 sikase-Dell-G15-5510 kernel: usb 1-5: device descriptor read/64, error >
Sep 14 17:32:16 sikase-Dell-G15-5510 kernel: usb 1-5: new high-speed USB device number >
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: Overwri>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: Overwri>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: Overwri>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: Overwri>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: Overwri>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: Overwri>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: Overwri>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: Overwri>
Sep 14 17:32:18 sikase-Dell-G15-5510 gnome-shell[3141]: Window manager warning: Overwri>
```

---

### Post by coffeecat on 2024-09-15
Not a chat thread. *Thread moved to **General Help**.*

---

### Post by vmpx on 2024-10-31
Against freezing try nomodeset parameter in GRUB.

---

