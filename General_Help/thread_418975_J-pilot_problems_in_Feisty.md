---
title: "J-pilot problems in Feisty"
date: 2007-04-22
forum: General Help
---

### Post by trents on 2007-04-22
J-pilot synced without problems with my Palm Z22 in Dapper and Edgy but I can't get it to work in Feisty. Wonder what the difference is? Anybody else had the same problem? Kpilot won't work either, but then I never could get it to work with the earlier Ubuntu versions either.

Steve

---

### Post by trents on 2007-04-25
Here's an update:
Here's what works for me:  If I open terminal and issue the command "sudo modprobe visor" before attempting the hotsync then J-pilot is able to locate the palm device. I then tap the hotsync button on my Palm Z22 screen and then I mouse click on J-pilot's hotsync button. Oh yes, the port settings line can be left blank or you can enter /dev/pilot. Any other entry will prevent J-pilot from finding the device. At least that's how it is on my system. Issuing the command "sudo modprobe visor" is really  the key here. Keep in mind this terminal command must be issued anew with every restart of the computer. This suggestion came from Jed Montgomery, the J-pilot project lead. I had emailed him with the issue.

By the way, I was even able to get Kpilot to sync after issuing the "psudo modprobe visor command". I had never gotten Kpilot to work before, even under Dapper and Edgy. With Kpilot, however, you must click on the blue "Reset Device Connection" after initially attempting a hotsync.

Steve

---

