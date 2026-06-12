---
title: "Can't boot Ubuntu - Please help."
date: 2008-01-28
forum: General Help
---

### Post by Sparky222B on 2008-01-28
Hi,

I installed Gutsy not too long ago on a Vista PC of mine, and I'm now dual-booting. GRUB is working fine.

However, when I boot Gutsy in normal or recovery mode, it reaches "Mounting root file system" and then does nothing. Freezes. I've tried disabling and disconnecting every piece of hardware and pariphial that's not needed to physically start the machine.

How can I solve this?
Thanks

---

### Post by erginemr on 2008-01-29
It is hard to tell; can be a lot of things. Were you able to boot into the system normally beforehand? 

One of the possibilites is a broken "initrd.img" file. Please follow this ongoing thread to see if it helps:
[http://ubuntuforums.org/showthread.php?t=681481](http://ubuntuforums.org/showthread.php?t=681481)

---

### Post by Sparky222B on 2008-01-30
> **erginemr said:**
> It is hard to tell; can be a lot of things. Were you able to boot into the system normally beforehand? 

One of the possibilites is a broken "initrd.img" file. Please follow this ongoing thread to see if it helps:
[http://ubuntuforums.org/showthread.php?t=681481](http://ubuntuforums.org/showthread.php?t=681481)

I have replaced the file, however it still will not boot. Thanks, but any other suggestions?

---

### Post by kesman on 2008-01-30
Or try reinstalling ubuntu, works too.

---

### Post by Sparky222B on 2008-01-30
> **kesman said:**
> Or try reinstalling ubuntu, works too.

How witty. Obviously I realize that - don't you think that if I had nothing to lose I would just wipe and reinstall? I don't want to loose all my customizations and apps.

---

### Post by torgrot on 2008-01-30
If you created a /home partition then re-installing won't affect them.  You will have to download all of the updates for your system and any custom apps you have installed.  Just as a suggestion boot from the liveCD and try re-installing grub.  It would appear to rebuild the linux image that is booted.  You can find specific instructions here [http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD)

torgrot

---

### Post by kesman on 2008-01-31
Yeah, when you installed ubuntu for the first time, you probably made /home a separate partition. If so, just install ubuntu again and mount /home to the existing partition, and DON'T format it.

---

