---
title: "Grip File Name Output"
date: 2007-07-26
forum: General Help
---

### Post by broth420 on 2007-07-26
I am using GRIP to rip and encode flac files from CD's
I would like the files to look like this "01 The End Of The World.flac"

I have figured out how to get the files to look like this "01The End Of The World.flac"
I am wondering if anyone can tell me what the command is to leave a space between "01" and "The End Of The  World.flac"

The following are my encoder settings:

Encoder Command Line:  -V -o %m -T Artist="%A" -T Title="%n" -T Album="%d" -T Date="%y" -T Tracknumber="%t" -T Genre="%G" %w -5

Encode File Format:  ~/Music/%A/%d/%t% %n%.%x

Thanks in advance.

---

### Post by broth420 on 2007-08-21
I figured this out.  In case anyone wants to know

~/Music/%A/%d/%t %n.%x

---

