---
title: "ink/mtink for network printers (Epson XP-211)"
date: 2015-07-29
forum: General Help
---

### Post by lucas15 on 2015-07-29
Hi , good day everyone!

I'm having troubles trying to install a program to see the ink level for my printer XP-211 in ubuntu 14.04LTS.

Currently , i have installed my printer in the network and working perfectly. (This , is in 192.168.1.100).

But, when i want to install in "ink" or "mtink" i have some troubles:
[LIST=|INDENT=1]
[*]ink: i use the command *ink -b bjnp://192.168.1.100 *and i'm getting this:
[LIST]
[*]CRIT: udp_command: no data received (recv)CRIT: udp_command: no data received (recv)CRIT: udp_command: no data received (recv)Could not read from printer.
[/LIST]
[/LIST]

[LIST=|INDENT=1]
[*]mtink: i run this with sudo, but i'm not sure if this program works with network printers (when you open this program, the only choice is selecting a port -*/dev/lp0*-)
[/LIST]

finally , everything points to you can't see the ink levels for a network printer (hope i'm wrong)
Is any way to see the ink levels for a printer if this is in a network ? Also, i'm doing something wrong?

Thanks so much for the help , everything comment will be appreciated.

---

### Post by howefield on 2015-07-29
Are they shown System Settings > Printers > Right click on printer and properties.. just noticed mine isn't showing the magenta inks.

---

### Post by lucas15 on 2015-07-29
nope, it show this:
[ATTACH=CONFIG]263464[/ATTACH]

---

