---
title: "Wubi made my Raid system unbootable"
date: 2007-06-24
forum: General Help
---

### Post by lixjgrib on 2007-06-24
I want to get Ubuntu onto my Alienware m9700 notebook, but the Ubuntu and now the Wubi installs all make my system unbootable. I know the problem is the mirrored raid (fakeraid), but how to I fix it or get around it? I've already destroyed my windows install several times, so I don't care if I just install a single boot Ubuntu at this point. I want it. Duelboot with XP would be nice, but not necessary for me.

I've seen the FakeRaidHowto, and some other guides that refer to that, but I'm too much of a newbie to get through it successfully. I noticed someone said that Wubi doesn't work with striped Raid, but mine is mirrored. It doesn't boot at all, and in fact just keeps rebooting itself through the bios startup.

---

### Post by ago on 2007-06-24
We do support some raid (0, 1) did you try the latest version from the website? Also wubi does not touch the MBR /partition table, so I do not see how it could make the system unbootable.

---

### Post by CrazyGuy123 on 2007-06-24
I expect wubi has ignored the raid and used just one of the mirrored disks, causing the raid set to go out of sync.  The usual solution would be to disable raid, get the system working how you want it, and recreate the raid set.  I wouldn't be able to give step by step instructions though because different raid hardware/software is different - you may get more help in an ubuntu/windows forum for your hardware.

---

### Post by ago on 2007-06-24
That seems quite plausible

---

### Post by lixjgrib on 2007-06-27
It seems that it was an aborted install that caused the problem. I still couldn't get it to work with raid after a couple of more attempts, so I just disabled my raid and it was fine. Various other problems persist, but its working.

---

