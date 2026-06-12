---
title: "mounting device without shortcut"
date: 2007-10-19
forum: General Help
---

### Post by dteedh on 2007-10-19
how can i mount a device/partition to /mnt/<something> without getting a shortcut of it on the desktop?

i read somewhere this should only happen to devices mounted to /media. is that right?

my fstab entry looks like that:

/dev/mapper/isw_fafeiigdf_Raid01 /mnt/raid0	ntfs	user	0	2

reading an writing works fine.

---

### Post by dayvy on 2007-10-19
Click "Applications" and go to "System Tools" and click "Configuration Editor".
In the configuration editor navigate to the following apps -> nautilus -> Desktop. In the right pane take the checkmarks out of the appropriate boxes.

---

### Post by dteedh on 2007-10-19
thx, but this will make the mounted cdrom/memorystick etc. in /media disappear as well. :(

---

### Post by dayvy on 2007-10-19
Your right there. Son of a ...

I'm curious if there is an easy fix for this or whether it's a bug.

---

### Post by neon777 on 2007-10-26
Any more ideas?

---

