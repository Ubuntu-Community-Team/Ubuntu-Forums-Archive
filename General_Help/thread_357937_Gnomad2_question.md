---
title: "Gnomad2 question"
date: 2007-02-10
forum: General Help
---

### Post by canadianwriterman on 2007-02-10
I've installed gnomad2 for my Creative Zen Microphoto using the repositories and following various threads. Everything seems to work except the detection of a jukebox. I've edited the file /etc/udev/rules.d/45-libnjb.rules and added the line for my device:

# Creative Nomad Jukebox Zen Microphoto USB 2.0
SYSFS{idVendor}=="041e", SYSFS{idProduct}=="413c", GROUP="plugdev", MODE="0660"

Still not detecting. I also tried creating a file in the same directory called nomad.rules, but I'm still not picking up the device. I used to have it working in Dapper, but now I'm using Edgy and the same process doesn't seem to work.

Any suggestions, anyone?

---

### Post by nereid on 2007-02-10
The version of Gnomad2 from the repositories is a little old. I've got a Creative Zen Micro at christmas and I've had the same problem. You'll have to compile the program by hand. [This thread](http://ubuntuforums.org/showthread.php?t=199250) should help you.

---

### Post by canadianwriterman on 2007-02-10
Thanks, nereid, that worked.

---

