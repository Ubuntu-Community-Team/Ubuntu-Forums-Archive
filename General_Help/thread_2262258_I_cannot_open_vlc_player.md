---
title: "I cannot open vlc player"
date: 2015-01-23
forum: General Help
---

### Post by mamun3 on 2015-01-23
I am useing Ubuntu 14.04LTS. I cannot open my installed vlc player. Some problem are fix in "terminal"

mamun@mamun-MS-7592:~$ vlc
VLC media player 2.1.4 Rincewind (revision 2.1.4-0-g2a072be)
[0x83b9158] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[0x8443aa0] skins2 interface error: no suitable dialogs provider found (hint: compile the qt4 plugin, and make sure it is loaded properly)
[0x8443aa0] skins2 interface error: cannot instantiate qt4 dialogs provider
[0x8443aa0] [cli] lua interface: Listening on host "*console".
VLC media player 2.1.4 Rincewind
Command Line Interface initialized. Type `help' for help.
> 



help me plz.

---

### Post by 3246251196 on 2015-01-23
Perhaps you do not have the necessary QT4 libraries? I am suprised that when installing VLC (if done through the proper package manager) it did not pull in QT4. I do not know normally work with the GUI. Moreover, my guess at the problem might not be correct. But it would be interesting to see the results of ```
 dpkg -l | grep -i qt 
``` and whether or not you remember installing VLC through conventional means.

---

### Post by mc4man on 2015-01-23
From terminal - 
```
vlc -Iqt4
```
If vlc opens ok (should) then switch back to the qt interface (or 'use native style') in Tools > Preferences > Interface
(or just delete  ~/.config/vlc/vlcrc

---

### Post by Bucky Ball on 2015-01-23
*Thread moved to **General Help**.*

Welcome. How did you install it? Best to use the version in the official repositories unless you have specific reasons to do otherwise.

---

