---
title: "Removing Ubuntu And Grub"
date: 2008-05-26
forum: General Help
---

### Post by Kralnor on 2008-05-26
Howdy!

I have been running WinXP and Ubuntu in a dual boot configuration but I wish to uninstall Ubuntu. So I booted from the WinXP installation CD in an attempt to run 'fixmbr' from the Recovery Console.
However, I couldn't quite figure out how to access the RC so when I reached the screen which prompts you for a partition to install Windows on I figured it was best to abort the setup. 
To my surprise, Grub was no longer loaded upon rebooting.

Am I safe to delete the EXT partitions at this point or should I make sure to run fixmbr? If the latter, how exactly do I access the RC?

---

### Post by nick_h on 2008-05-26
If you are now booting to Windows without grub then the Windows disk obviously has installed a suitable boot loader.

You can just reformat the ext3 partitions if there is nothing on them you want to keep.

---

### Post by Kralnor on 2008-05-26
Thanks for the reply.

I made the stupid decision to try and proceed with the installation process, hoping that I would get the option to enter the RC at some point.

So now I have two installations of WinXP on the same partition and can boot to both from the Windows boot loader.

Next step is trying to figure out how to remove the most recent one ;)

EDIT: That was very easy. Simply using the bootcfg utility bundled with WinXP did the trick.

---

