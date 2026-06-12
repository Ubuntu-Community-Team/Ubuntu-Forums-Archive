---
title: "help running fsck -y on root partition"
date: 2007-04-06
forum: General Help
---

### Post by inphektion on 2007-04-06
ok i'm getting weird errors on boot on my disk after using gparted.  If I understand correctly it only runs fsck in preen mode on boot.  I want to run it like fsck -y on /dev/sda1 which is my root partition but obviously I can't once the system boots as it is mounted.  How can I tell fsck -y to run at boot instead of just the preen mode?  OR I have the live cd but then couldn't see where or if it mounted my hdd anywhere to run the commands on them.  In the livecd /dev/sda1 seemed to be something else.  
This is feisty fawn latest running inside vmware.

---

### Post by Peti29 on 2007-04-07
I'd like to know this too. How to explicitly trigger a disk check at boot time? It does run automatically every 30th booting, but how to do it in between?

---

### Post by inphektion on 2007-04-07
That's not what I want to know.  I want to run it as fsck -y somehow.  for you just use tune2fs to change how often or not it runs, check out the man page.  

For my issue I believe I can do it somehow from the live cd but not sure.

---

### Post by Herman on 2007-04-07
> ok i'm getting weird errors on boot on my disk after using gparted. If I understand correctly it only runs fsck in preen mode on boot. I want to run it like fsck -y on /dev/sda1 which is my root partition but obviously I can't once the system boots as it is mounted. How can I tell fsck -y to run at boot instead of just the preen mode? OR I have the live cd but then couldn't see where or if it mounted my hdd anywhere to run the commands on them. In the livecd /dev/sda1 seemed to be something else. 
This is feisty fawn latest running inside vmware. Hello inphektion,
I don't know about vmware.
For a regular hard disk installed file system or operating system you just boot the Ubuntu live CD and open a terminal. You don't want to mount anything, you should never run a file system check on a mounted file system. My favorite command is the following one, you could add your -y option to it too if you like,```
 sudo e2fsck -C0 -p -f -v /dev/sda1
```(Presuming it's an ext3 filesystem)

Or, here's an easier way, if you have a copy of  [GParted -- LiveCD]("http://gparted.sourceforge.net/livecd.php") . You can initiate a filesystem check by booting the GParted LiveCD, right-clicking a partition, and selecting 'check' from the right-click menu, then click 'Apply'. 
       When the operation is finished you should click the '> Details' and then the 'Check and Repair' line, which expands into three subsequent lines.
       These are, 'calibrate', 'check filesystem for errors and (if possible) fix them', and 'grow filesystem to fill partition'.
       When you click on each of these you get more details of what has been done.
       The middle line, 'check filesystem for errors and (if possible) fix them', when clicked, tells you the command GParted LiveCD used for the check, and when you click on the line describing the command, it expands into a report on the state of your file system, which is super cool!

Regards Herman :)

---

### Post by Herman on 2007-04-07
Hello Peti29, 
Try typing the following command into a terminal,
```
sudo touch /forcefsck
``` and then watch closely next time you reboot and you'll see the filesystem check taking place.

inphektion is correct, you can also use tune2fs to change the frequency of the filesystem check taking place.

Regards, Herman :)

---

### Post by inphektion on 2007-04-07
herman, thank you much.  I have both ubuntu live cd and gparted live cd.  It was after using the gparted and growing my root partition from 4gb to 6gb that I then noticed these issues.  So I was hesitant to use gparted to attempt to fix them I wanted to use some other command.

---

### Post by inphektion on 2007-04-07
I dont know. I'm at a complete loss.  I ran the fsck from ubuntu and did the check from gparted live cd.  Still get this on boot:

```
[   51.199581] lp0: using parport0 (interrupt-driven).
[   51.351801] Adding 216836k swap on /dev/disk/by-uuid/6551fee1-4a95-4010-919a-797e781a5fec.  Priority:-1 extents:1 across:216836k
[   51.470874] EXT3 FS on sda1, internal journal
[   52.159054] eth0: link up
[   54.442662] NET: Registered protocol family 17
[   57.136498] NET: Registered protocol family 10
[   57.139492] lo: Disabled Privacy Extensions
[   60.025995] ACPI: AC Adapter [ACAD] (on-line)
[   60.145490] input: Power Button (FF) as /class/input/input4
[   60.145602] ACPI: Power Button (FF) [PWRF]
[   60.188256] Using specific hotkey driver
[   60.248275] No dock devices found.
[   60.333904] ibm_acpi: ec object not found
[   60.620818] pcc_acpi: loading...
[   65.617467] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   65.617535] ata2.00: (BMDMA stat 0x26)
[   65.617549] ata2.00: cmd a0/01:00:00:00:00/00:00:00:00:00/a0 tag 0 cdb 0x43 data 12 in
[   65.617561]          res 51/20:03:00:00:00/00:00:00:00:00/a0 Emask 0x20 (host bus error)
[   65.928340] ata2.00: configured for UDMA/33
[   65.928407] ata2: EH complete
[   65.928766] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   65.928794] ata2.00: (BMDMA stat 0x26)
[   65.928814] ata2.00: cmd a0/01:00:00:00:00/00:00:00:00:00/a0 tag 0 cdb 0x43 data 12 in
[   65.928834]          res 51/20:03:00:00:00/00:00:00:00:00/a0 Emask 0x20 (host bus error)
[   66.239616] ata2.00: configured for UDMA/33
[   66.239678] ata2: EH complete
[   66.239996] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   66.240022] ata2.00: (BMDMA stat 0x26)
[   66.240043] ata2.00: cmd a0/01:00:00:00:00/00:00:00:00:00/a0 tag 0 cdb 0x43 data 12 in
[   66.240063]          res 51/20:03:00:00:00/00:00:00:00:00/a0 Emask 0x20 (host bus error)
[   66.555073] ata2.00: configured for UDMA/33
[   66.555167] ata2: EH complete
[   66.555660] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   66.555698] ata2.00: (BMDMA stat 0x26)
[   66.555726] ata2.00: cmd a0/01:00:00:00:00/00:00:00:00:00/a0 tag 0 cdb 0x43 data 12 in
[   66.555753]          res 51/20:03:00:00:00/00:00:00:00:00/a0 Emask 0x20 (host bus error)
[   66.874538] ata2.00: configured for UDMA/33
[   66.874631] ata2: EH complete
[   66.875180] sr0: CDROM (ioctl) error, command: <6>Read TOC/PMA/ATIP 43 00 00 00 00 00 00 00 0c 40
[   66.875429] sr: Current [descriptor]: sense key: Aborted Command
[   66.877993]     Additional sense: No additional sense information
[   66.882927] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   66.882963] ata2.00: (BMDMA stat 0x26)
[   66.882991] ata2.00: cmd a0/01:00:00:00:00/00:00:00:00:00/a0 tag 0 cdb 0x43 data 12 in
[   66.883018]          res 51/20:03:00:00:00/00:00:00:00:00/a0 Emask 0x20 (host bus error)
[   67.201516] ata2.00: configured for UDMA/33
[   67.201608] ata2: EH complete
[   67.202391] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   67.202427] ata2.00: (BMDMA stat 0x26)
[   67.202455] ata2.00: cmd a0/01:00:00:00:00/00:00:00:00:00/a0 tag 0 cdb 0x43 data 12 in
[   67.202490]          res 51/20:03:00:00:00/00:00:00:00:00/a0 Emask 0x20 (host bus error)
[   67.520792] ata2.00: configured for UDMA/33
[   67.520885] ata2: EH complete
[   67.521761] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   67.521797] ata2.00: (BMDMA stat 0x26)
[   67.521825] ata2.00: cmd a0/01:00:00:00:00/00:00:00:00:00/a0 tag 0 cdb 0x43 data 12 in
[   67.521851]          res 51/20:03:00:00:00/00:00:00:00:00/a0 Emask 0x20 (host bus error)
[   67.791994] eth0: no IPv6 routers present
[   67.840102] ata2.00: configured for UDMA/33
[   67.840193] ata2: EH complete
[   67.841255] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   67.841291] ata2.00: (BMDMA stat 0x26)
[   67.841319] ata2.00: cmd a0/01:00:00:00:00/00:00:00:00:00/a0 tag 0 cdb 0x43 data 12 in
[   67.841345]          res 51/20:03:00:00:00/00:00:00:00:00/a0 Emask 0x20 (host bus error)
[   68.155344] ata2.00: configured for UDMA/33
[   68.156094] ata2: EH complete
[   68.156296] sr0: CDROM (ioctl) error, command: <6>Read TOC/PMA/ATIP 43 00 00 00 00 00 00 00 0c 00
[   68.156322] sr: Current [descriptor]: sense key: Aborted Command
[   68.156401]     Additional sense: No additional sense information
[   68.160428] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   68.160466] ata2.00: (BMDMA stat 0x26)
[   68.160493] ata2.00: cmd a0/01:00:00:00:00/00:00:00:00:00/a0 tag 0 cdb 0x25 data 8 in
[   68.160520]          res 51/20:03:00:00:00/00:00:00:00:00/a0 Emask 0x20 (host bus error)
[   68.474610] ata2.00: configured for UDMA/33
[   68.474702] ata2: EH complete
[   68.475931] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   68.475967] ata2.00: (BMDMA stat 0x26)
[   68.475995] ata2.00: cmd a0/01:00:00:00:00/00:00:00:00:00/a0 tag 0 cdb 0x25 data 8 in
[   68.476022]          res 51/20:03:00:00:00/00:00:00:00:00/a0 Emask 0x20 (host bus error)
[   68.789878] ata2.00: configured for UDMA/33
[   68.789969] ata2: EH complete
[   68.791298] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   68.791335] ata2.00: (BMDMA stat 0x26)
[   68.791362] ata2.00: cmd a0/01:00:00:00:00/00:00:00:00:00/a0 tag 0 cdb 0x25 data 8 in
[   68.791389]          res 51/20:03:00:00:00/00:00:00:00:00/a0 Emask 0x20 (host bus error)
[   69.105166] ata2.00: configured for UDMA/33
[   69.105260] ata2: EH complete
[   69.106725] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   69.106762] ata2.00: (BMDMA stat 0x26)
[   69.106789] ata2.00: cmd a0/01:00:00:00:00/00:00:00:00:00/a0 tag 0 cdb 0x25 data 8 in
[   69.106816]          res 51/20:03:00:00:00/00:00:00:00:00/a0 Emask 0x20 (host bus error)
[   69.420433] ata2.00: configured for UDMA/33
[   69.420536] ata2: EH complete
[   69.424221] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   69.424257] ata2.00: (BMDMA stat 0x26)
[   69.424284] ata2.00: cmd a0/01:00:00:00:00/00:00:00:00:00/a0 tag 0 cdb 0x25 data 8 in
[   69.424353]          res 51/20:03:00:00:00/00:00:00:00:00/a0 Emask 0x20 (host bus error)
[   69.735722] ata2.00: configured for UDMA/33
[   69.735815] ata2: EH complete
[   69.737496] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   69.737532] ata2.00: (BMDMA stat 0x26)
[   69.737570] ata2.00: cmd a0/01:00:00:00:00/00:00:00:00:00/a0 tag 0 cdb 0x25 data 8 in
[   69.737596]          res 51/20:03:00:00:00/00:00:00:00:00/a0 Emask 0x20 (host bus error)
[   70.050997] ata2.00: configured for UDMA/33
[   70.051089] ata2: EH complete
[   70.052865] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   70.052901] ata2.00: (BMDMA stat 0x26)
[   70.052929] ata2.00: cmd a0/01:00:00:00:00/00:00:00:00:00/a0 tag 0 cdb 0x25 data 8 in
[   70.052955]          res 51/20:03:00:00:00/00:00:00:00:00/a0 Emask 0x20 (host bus error)
[   70.366272] ata2.00: configured for UDMA/33
[   70.366332] ata2: EH complete
[   70.366813] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   70.368306] ata2.00: (BMDMA stat 0x26)
[   70.368335] ata2.00: cmd a0/01:00:00:00:00/00:00:00:00:00/a0 tag 0 cdb 0x25 data 8 in
[   70.368361]          res 51/20:03:00:00:00/00:00:00:00:00/a0 Emask 0x20 (host bus error)
[   70.681519] ata2.00: configured for UDMA/33
[   70.681622] ata2: EH complete
[   70.682448] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   70.682483] ata2.00: (BMDMA stat 0x26)
[   70.682509] ata2.00: cmd a0/01:00:00:00:00/00:00:00:00:00/a0 tag 0 cdb 0x25 data 8 in
[   70.682536]          res 51/20:03:00:00:00/00:00:00:00:00/a0 Emask 0x20 (host bus error)
[   70.992934] ata2.00: configured for UDMA/33
[   70.992999] ata2: EH complete
[   70.993560] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   70.993596] ata2.00: (BMDMA stat 0x26)
[   70.993622] ata2.00: cmd a0/01:00:00:00:00/00:00:00:00:00/a0 tag 0 cdb 0x25 data 8 in
[   70.993649]          res 51/20:03:00:00:00/00:00:00:00:00/a0 Emask 0x20 (host bus error)
[   71.304186] ata2.00: configured for UDMA/33
[   71.304244] ata2: EH complete
[   71.304725] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   71.304764] ata2.00: (BMDMA stat 0x26)
[   71.304790] ata2.00: cmd a0/01:00:00:00:00/00:00:00:00:00/a0 tag 0 cdb 0x25 data 8 in
[   71.304817]          res 51/20:03:00:00:00/00:00:00:00:00/a0 Emask 0x20 (host bus error)
[   71.615392] ata2.00: configured for UDMA/33
[   71.615451] ata2: EH complete
[   71.615926] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   71.615963] ata2.00: (BMDMA stat 0x26)
[   71.615990] ata2.00: cmd a0/01:00:00:00:00/00:00:00:00:00/a0 tag 0 cdb 0x25 data 8 in
[   71.616016]          res 51/20:03:00:00:00/00:00:00:00:00/a0 Emask 0x20 (host bus error)
[   71.926643] ata2.00: configured for UDMA/33
[   71.926743] ata2: EH complete
[   71.931860] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   71.931901] ata2.00: (BMDMA stat 0x26)
[   71.931928] ata2.00: cmd a0/01:00:00:00:00/00:00:00:00:00/a0 tag 0 cdb 0x43 data 12 in
[   71.931954]          res 51/20:03:00:00:00/00:00:00:00:00/a0 Emask 0x20 (host bus error)
[   72.241908] ata2.00: configured for UDMA/33
[   72.241959] ata2: EH complete
[   72.242421] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   72.242460] ata2.00: (BMDMA stat 0x26)
[   72.242487] ata2.00: cmd a0/01:00:00:00:00/00:00:00:00:00/a0 tag 0 cdb 0x43 data 12 in
[   72.242513]          res 51/20:03:00:00:00/00:00:00:00:00/a0 Emask 0x20 (host bus error)
[   72.553238] ata2.00: configured for UDMA/33
[   72.553297] ata2: EH complete
[   72.554198] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   72.554238] ata2.00: (BMDMA stat 0x26)
[   72.554265] ata2.00: cmd a0/01:00:00:00:00/00:00:00:00:00/a0 tag 0 cdb 0x43 data 12 in
[   72.554292]          res 51/20:03:00:00:00/00:00:00:00:00/a0 Emask 0x20 (host bus error)
[   72.864520] ata2.00: configured for UDMA/33
[   72.864580] ata2: EH complete
[   72.865114] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   72.865154] ata2.00: (BMDMA stat 0x26)
[   72.865181] ata2.00: cmd a0/01:00:00:00:00/00:00:00:00:00/a0 tag 0 cdb 0x43 data 12 in
[   72.865208]          res 51/20:03:00:00:00/00:00:00:00:00/a0 Emask 0x20 (host bus error)
[   73.175808] ata2.00: configured for UDMA/33
[   73.175880] ata2: EH complete
[   73.176220] sr0: CDROM (ioctl) error, command: <6>Read TOC/PMA/ATIP 43 00 00 00 00 00 00 00 0c 40
[   73.176311] sr: Current [descriptor]: sense key: Aborted Command
[   73.176388]     Additional sense: No additional sense information
[   73.180775] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   73.180809] ata2.00: (BMDMA stat 0x26)
[   73.180836] ata2.00: cmd a0/01:00:00:00:00/00:00:00:00:00/a0 tag 0 cdb 0x43 data 12 in
[   73.180863]          res 51/20:03:00:00:00/00:00:00:00:00/a0 Emask 0x20 (host bus error)
[   73.491208] ata2.00: configured for UDMA/33
[   73.491268] ata2: EH complete
[   73.491789] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   73.491826] ata2.00: (BMDMA stat 0x26)
[   73.491853] ata2.00: cmd a0/01:00:00:00:00/00:00:00:00:00/a0 tag 0 cdb 0x43 data 12 in
[   73.491879]          res 51/20:03:00:00:00/00:00:00:00:00/a0 Emask 0x20 (host bus error)
[   73.806339] ata2.00: configured for UDMA/33
[   73.806397] ata2: EH complete
[   73.806895] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   73.806935] ata2.00: (BMDMA stat 0x26)
[   73.806962] ata2.00: cmd a0/01:00:00:00:00/00:00:00:00:00/a0 tag 0 cdb 0x43 data 12 in
[   73.806988]          res 51/20:03:00:00:00/00:00:00:00:00/a0 Emask 0x20 (host bus error)
[   74.126300] ata2.00: configured for UDMA/33
[   74.126357] ata2: EH complete
[   74.126769] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   74.126804] ata2.00: (BMDMA stat 0x26)
[   74.126830] ata2.00: cmd a0/01:00:00:00:00/00:00:00:00:00/a0 tag 0 cdb 0x43 data 12 in
[   74.126857]          res 51/20:03:00:00:00/00:00:00:00:00/a0 Emask 0x20 (host bus error)
[   74.444897] ata2.00: configured for UDMA/33
[   74.444929] ata2: EH complete
[   74.445470] sr0: CDROM (ioctl) error, command: <6>Read TOC/PMA/ATIP 43 00 00 00 00 00 00 00 0c 00
[   74.445556] sr: Current [descriptor]: sense key: Aborted Command
[   74.445590]     Additional sense: No additional sense information
[   74.447577] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   74.447610] ata2.00: (BMDMA stat 0x26)
[   74.447637] ata2.00: cmd a0/01:00:00:00:00/00:00:00:00:00/a0 tag 0 cdb 0x25 data 8 in
[   74.447663]          res 51/20:03:00:00:00/00:00:00:00:00/a0 Emask 0x20 (host bus error)
[   74.764160] ata2.00: configured for UDMA/33
[   74.764225] ata2: EH complete
[   74.765153] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   74.765195] ata2.00: (BMDMA stat 0x26)
[   74.765222] ata2.00: cmd a0/01:00:00:00:00/00:00:00:00:00/a0 tag 0 cdb 0x25 data 8 in
[   74.765248]          res 51/20:03:00:00:00/00:00:00:00:00/a0 Emask 0x20 (host bus error)
[   75.083452] ata2.00: configured for UDMA/33
[   75.083511] ata2: EH complete
[   75.084512] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   75.084552] ata2.00: (BMDMA stat 0x26)
[   75.084578] ata2.00: cmd a0/01:00:00:00:00/00:00:00:00:00/a0 tag 0 cdb 0x25 data 8 in
[   75.084605]          res 51/20:03:00:00:00/00:00:00:00:00/a0 Emask 0x20 (host bus error)
[   75.398736] ata2.00: configured for UDMA/33
[   75.398795] ata2: EH complete
[   75.399255] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   75.399256] ata2.00: (BMDMA stat 0x26)
[   75.399922] ata2.00: cmd a0/01:00:00:00:00/00:00:00:00:00/a0 tag 0 cdb 0x25 data 8 in
[   75.399949]          res 51/20:03:00:00:00/00:00:00:00:00/a0 Emask 0x20 (host bus error)
[   75.714038] ata2.00: configured for UDMA/33
[   75.714112] ata2: EH complete
[   75.716822] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   75.716860] ata2.00: (BMDMA stat 0x26)
[   75.716887] ata2.00: cmd a0/01:00:00:00:00/00:00:00:00:00/a0 tag 0 cdb 0x25 data 8 in
[   75.716914]          res 51/20:03:00:00:00/00:00:00:00:00/a0 Emask 0x20 (host bus error)
[   76.029143] ata2.00: configured for UDMA/33
[   76.029178] ata2: EH complete
[   76.029438] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   76.029491] ata2.00: (BMDMA stat 0x26)
[   76.029505] ata2.00: cmd a0/01:00:00:00:00/00:00:00:00:00/a0 tag 0 cdb 0x25 data 8 in
[   76.029518]          res 51/20:03:00:00:00/00:00:00:00:00/a0 Emask 0x20 (host bus error)
[   76.452157] ata2.00: configured for UDMA/33
[   76.452193] ata2: EH complete
[   76.452447] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   76.452464] ata2.00: (BMDMA stat 0x26)
[   76.452476] ata2.00: cmd a0/01:00:00:00:00/00:00:00:00:00/a0 tag 0 cdb 0x25 data 8 in
[   76.452492]          res 51/20:03:00:00:00/00:00:00:00:00/a0 Emask 0x20 (host bus error)
[   76.761961] ata2.00: configured for UDMA/33
[   76.761994] ata2: EH complete
[   76.762272] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   76.762289] ata2.00: (BMDMA stat 0x26)
[   76.762302] ata2.00: cmd a0/01:00:00:00:00/00:00:00:00:00/a0 tag 0 cdb 0x25 data 8 in
[   76.762314]          res 51/20:03:00:00:00/00:00:00:00:00/a0 Emask 0x20 (host bus error)
[   77.074787] ata2.00: configured for UDMA/33
[   77.074832] ata2: EH complete
[   77.084092] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   77.084294] ata2.00: (BMDMA stat 0x26)
[   77.084364] ata2.00: cmd a0/01:00:00:00:00/00:00:00:00:00/a0 tag 0 cdb 0x25 data 8 in
[   77.084376]          res 51/20:03:00:00:00/00:00:00:00:00/a0 Emask 0x20 (host bus error)
[   77.508692] ata2.00: configured for UDMA/33
[   77.508731] ata2: EH complete
[   77.508984] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   77.509058] ata2.00: (BMDMA stat 0x26)
[   77.509101] ata2.00: cmd a0/01:00:00:00:00/00:00:00:00:00/a0 tag 0 cdb 0x25 data 8 in
[   77.509113]          res 51/20:03:00:00:00/00:00:00:00:00/a0 Emask 0x20 (host bus error)
[   77.821281] ata2.00: configured for UDMA/33
[   77.821316] ata2: EH complete
[   77.821562] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   77.821636] ata2.00: (BMDMA stat 0x26)
[   77.821679] ata2.00: cmd a0/01:00:00:00:00/00:00:00:00:00/a0 tag 0 cdb 0x25 data 8 in
[   77.821691]          res 51/20:03:00:00:00/00:00:00:00:00/a0 Emask 0x20 (host bus error)
[   78.132336] ata2.00: configured for UDMA/33
[   78.132372] ata2: EH complete
[   78.132626] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   78.132643] ata2.00: (BMDMA stat 0x26)
[   78.132656] ata2.00: cmd a0/01:00:00:00:00/00:00:00:00:00/a0 tag 0 cdb 0x25 data 8 in
[   78.132668]          res 51/20:03:00:00:00/00:00:00:00:00/a0 Emask 0x20 (host bus error)
[   78.443609] ata2.00: configured for UDMA/33
[   78.443653] ata2: EH complete
[   78.793623] mtrr: your processor doesn't support write-combining
[   79.476264] ppdev: user-space parallel port driver
[   83.166020] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   83.166202] apm: disabled - APM is not SMP safe.
[   95.915413] eth0: no IPv6 routers present


```

any ideas, feel free to throw them out there.

oh and in case i never made clear, even after all these weird errors I can still login just fine and use the system with no problems.  I just hate to see this scrollin by on every boot.

---

### Post by pr3@ch3r on 2007-04-14
You don't need a fsck, it won't fix that error. I've had it pop up similarly on various distros that Ive tried. Some do it some don't.

For you it's one of 3 things:

1.) Your UDMA speed is misconfigured in bios (doubt it, bios auto detect is very good at determining proper settings)

2.) Your hardware is going bad (doubt this too, you've probably got a newer system or at least drive)

3.) Your cdrom is tripping out the kernel. (this is common with newer cd/dvd burners)

I'd bet money its the latter. Just recently my dvd/rw couldn't properly load the Mepis 6.5 LiveCD. They don't have the proper module for my dvd drive, and its less than 6 months old (the drive that is).

I wouldn't worry about it bro. But in the case that you are concerned, answer this one question: Do you have ide drives or sata/scsi? If the answer is SATA/SCSI then this is for sure a CD/DVD Drive issue as UDMA is not used for SATA/SCSI. In fact, UDMA/33 is ONLY used by cd/dvd drives in this day and age.

---

