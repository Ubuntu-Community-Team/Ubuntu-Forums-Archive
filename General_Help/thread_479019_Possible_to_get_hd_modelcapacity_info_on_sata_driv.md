---
title: "Possible to get hd model/capacity info on sata drives?"
date: 2007-06-19
forum: General Help
---

### Post by glave on 2007-06-19
I know with ide drives I can simple cat what I need from /proc/ide/ideX to get the model, capacity, and whatever else. Is this not possible with sata drives? I've looked in /proc/scsi, and I can see the promise controller, and several numbers listed under it, but I cannot cat those.


Is there somewhere else I can look to get this info?

---

### Post by logos34 on 2007-06-19
sudo smartctl -i /dev/sda  (req. smartmontools package)
sudo lshw -C disk
sudo lshw

not sure if that helps much, though

---

