---
title: "Lubuntu File Manager Not Displaying Network Shares"
date: 2017-11-24
forum: General Help
---

### Post by spode2 on 2017-11-24
I have used Lubuntu for some years, and the Network folder in the default file manager, PCManFM, has always behaved erratically (same with Thunar too). Sometimes it will correctly display all machines connected to the network, but then a software update will cause it to just display an empty Windows group folder. I then wait patiently until it starts working again, having learned from experience not to waste time on any of the fixes recommended in forums - most of which are many years old.

As the problem has remained present over the last few updates for both 17.04 and 17.10, I would be pleased if someone could explain what the underlying problem is. I can put smb://device-name into the PCManFM navigation toolbar and the shares are mounted and displayed, so there does not seem to be any problem with name resolution or Samba setup, just that the file manager is not automatically scanning the network for shares. Is PCManFM still being actively developed? Is there a lightweight alternative which works properly?

---

### Post by spode2 on 2017-11-24
And right on cue, one of today's updates has restored the network folder function!

---

### Post by Holger_Gehrke on 2017-11-24
Don't assign blame or give praise were they aren't due. All the file managers you mentioned use the same abstraction layer for making things that aren't really file system look like they are: gvfs (GIO virtual file system). So unless today's update was connected in some way to that, the update probably did not cause the network folder to work, except perhaps in some roundabout way by forcing gvfs to refresh some stuff ... 

And yes,there are still people working on pcmanfm, although mainly in maintenance since it has been feature complete for years.

---

### Post by spode2 on 2017-11-24
Thanks for the reply.

This affected 2 Lubuntu machines so, after finding one worked, I powered up the other and found the problem was still there. I updated it, rebooted, and the problem was gone, so I do not think it was a coincidence.

Good to hear PCManFM is still being looked-after, as I do like it.

---

