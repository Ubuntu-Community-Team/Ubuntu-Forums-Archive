---
title: "Gutsy, reiser4, nvidia"
date: 2007-09-26
forum: General Help
---

### Post by e-gandalf on 2007-09-26
I've been trying to test reiser4 on Gutsy.

First of all, it seems that custom kernel is a real PITA in Ubuntu world because the model of updates doesn't take into account that kernel might be modified.
It means that if I'd decide to switch one of my partitions to reiser4 I'll have to play with it with each and every kernel update I think... well...

I installed linux sources for 2.6.22, added reiser4 patch, added it as a module in menuconfig, did make-kpkg --initrd --append-to-version=-reiser4 kernel_image kernel_headers

and installed both kernel_image and kernel_headers with dpkg.

After rebooting Ubuntu (why, oh why can't I just install this one single driver as a module... it's a driver, it doesn't touch kernel itself...) with custom kernel I landed in the text mode with nvidia-glx saying bye, bye.

Reinstalling nvidia-glx didn't help. I think I have to recompile the driver using nvidia installer...

Whoa, this leaded me to putting a white flag on top of the roof and going back to old and well used default kernel.

Question: Is there any better method to get reiser4 support? Any easier one? I know, I know, it's not in def kernel, it may kill kitties, and because Hans is offline noone should use it... but... let's assume I trust reiser4 being stable enough for me. Did anyone find an easier way? Without a need to recompile kernel, nvidia driver etc. to get this one reiser4 driver alive?

Thanks for any help :)

P.S. This is open source, if we will not eat our dog food, who will? I've read that reiser4 won't be supported in Ubuntu until it hits mainline. Pity cause I doubt Linus will get it into mainline until the activity around reiser4 goes up. blind circle.

---

