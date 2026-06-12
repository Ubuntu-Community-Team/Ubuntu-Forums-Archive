---
title: "Did a silly thing -- I think"
date: 2016-11-17
forum: General Help
---

### Post by FerryGnu on 2016-11-17
I have 16LTS installed and was having some problems and decided to install 14LTS along side it. I had been using 14LTS in a VM with windows and it was doing what 16LTS was not. All good. But when I started setting up the new 14LTS, something hiccuped and it stalled so I decide to boot to 16LTS, use GParted to clear the 14LTS Partition and then install 14LTS afresh.

I was just about to shut down 16LTS and boot from the 14LTS Live CD and wondered what Grub might do when I do that.

After installing 14LTS along side 16, there are four options in the Grub list. 
Start 14
Start 14+Special...
Start 16
Start 16+Special...

Soooo, before shutting down I am wondering should I edit the grub list or just boot the 14-Live-CD?

IF edit the Grub list, how do I do that as I do not want  to lose a weeks work with setting up 16LTS with wine, veracrypt etc if Grub crashes at the next start.

---

### Post by howefield on 2016-11-17
Just boot and install 14.04 and grub will take care of itself, overwriting the current grub configuration with a fresh one.

PS. Ensure that you are using 14.04.1 or 14.04.5 install media to ensure support till 2019.

---

### Post by FerryGnu on 2016-11-18
Phew, thanks. It did it all for me as you described. Saved.

Thank you.

---

