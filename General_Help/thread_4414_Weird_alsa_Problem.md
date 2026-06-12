---
title: "Weird alsa Problem"
date: 2004-11-15
forum: General Help
---

### Post by wondering_jew on 2004-11-15
It seems when i reboot I no longer have any sound, I reinstall alsa and restart my computer and i have sound again, until i restart and my sound goes away again, I'd like a way to fix this beside not ever turing off my computer, any help would be great its pretty frustrating

---

### Post by Rodney on 2004-11-15
Run "sudo alsamixer" minus the quotes in a terminal , set your levels , unmute any you need using the M key.
When you have it all set to your liking run "sudo alsactl store"
This saves your settings for you.

---

### Post by wondering_jew on 2004-11-15
Thanks i havent restarted yet to check it out but did the commands.

---

### Post by wondering_jew on 2004-11-17
I rebooted again and found the same problem.... when i reinstall alsa-base and restart it works until the next reboot, after i reboot alsa does not detect my sound card and i am unable to open up any mixer its not that the sound is muted

---

