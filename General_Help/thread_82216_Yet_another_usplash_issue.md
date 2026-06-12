---
title: "Yet another usplash issue"
date: 2005-10-26
forum: General Help
---

### Post by MilestoneIII on 2005-10-26
I'm really sorry if this problem has been answered elsewhere, but I've been searching for about 3 hours. I've recently done a fresh install of Breezy. The last setup I had ran usplash with no issues. This one, has a big error somewheres, lol. Right after the grub menu, the first thing I see is an error saying:

insmod: can't read '/lib/modules/2.6.12-9/initrd/vesafb.ko'  (I know it's there, I checked, and even copied another to see if it was that)

Then there's a pause, and normal setup resumes. First, my boot image is set to vga=795. that should be 1280x1024 millions. I've got a Dell 5150 laptop, with the crappy nvidia 5200 (64meg) and a 1400x1050 display. Past that, I've tried reconfiguring the initrd image, and yes, reinstalled the usplash. No success. It's unusual, since I had it working before. The only thing I've not tried is setting the vga to 792. I'll try that untill I hear anything. I've even messed witht the "TIMEOUT 120" and had no success. Thanks guys.

---

