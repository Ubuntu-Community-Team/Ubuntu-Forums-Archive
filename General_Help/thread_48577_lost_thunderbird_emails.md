---
title: "lost thunderbird emails"
date: 2005-07-13
forum: General Help
---

### Post by Loki7 on 2005-07-13
following instructions given by, [www.plaintivemewling.com/?p=20](www.plaintivemewling.com/?p=20), for creating a centralized email folder that could be used by my various linux distros, (Fedora3, Ubuntu, soon Xandros), everything was working fine. copied the older winxp emails through mozilla and finally had all the wifes'emails together.
Problem: got rid of winxp's ntfs harddrive, formatted vfat, and during a cut-and-paste from the prior shared harddrive to the new harddrive, lost the *.slt file.
simply did a cut, went to the other harddrive, and pasted. the pasted file disappeared, and stupidly enough, i didn't copy, i cut.
no more file
searched with 'find files', no luck. rebooted into Fedora, still no luck.
I cannot find the email file anymore
is there some sort of clipboard where the cut file could be waiting?
any suggestions would be appreciated

---

### Post by arnieboy on 2005-07-13
sorry to hear u lost your file.. next time a paste function does not happen, try and paste it somewhere else like back in ur home directory or somewhere so that the file is not lost forever (as long as it is still on the clipboard) before u reboot or log off.. 
herez how u can see if the file is still there somewhere or not.. 
from a terminal:

```
sudo updatedb
slocate *.slt*|more
```

good luck

---

### Post by Loki7 on 2005-07-13
i would have pasted it elsewhere, but it dissapeared. i found references from the correct .slt file, but they are in nautilus xml files.
thanx

is it possible to retrieve from nautilus?

---

### Post by arnieboy on 2005-07-13
[QUOTE=Loki7]i would have pasted it elsewhere, but it dissapeared. i found references from the correct .slt file, but they are in nautilus xml files.
thanx

is it possible to retrieve from nautilus?[/QUOTE]
no it is not. thats just a reference.. u need the actual file.

---

### Post by Loki7 on 2005-07-13
oh well,
Thank you very much for your time,
later dude

---

### Post by maruchan on 2005-07-13
[img]http://www.friendlyskies.net/tbirds.jpg[/img]

---

### Post by Loki7 on 2005-07-13
funny, very funny
exept for the fact i lost 5 days of work, i could laugh also.
live and learn

---

