---
title: "Another VMWarePlayer (Ubuntu Host: XP Guest) Sound Issue"
date: 2007-02-25
forum: General Help
---

### Post by Icarus3000 on 2007-02-25
When I run XP through VMWarePlayer it seems that XP doesn't see any audio hardware at all.  I have VMTools installed, and sound is set to true in my .vmx file.

In the device manager I see "legacy audio drivers" "audio codecs" and "media control devices", but when I select CONTROL PANEL>SOUNDS it says "No Audio Device".

Strangely enough, if I use rdesktop to connect to my vmware machine, I do get sound.

I have tried the fix suggested here:  [http://www.ubuntuforums.org/showthread.php?t=331175&highlight=vmware+sound](http://www.ubuntuforums.org/showthread.php?t=331175&highlight=vmware+sound)

(using vmplayer in place of "vmware", since I did not find a file "/usr/bin/vmware"), but that made no difference.

Anyone have any suggestions?

Thanks!
Icarus3000

---

