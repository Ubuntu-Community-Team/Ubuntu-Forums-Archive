---
title: "Lost root partition after hibernate"
date: 2008-07-08
forum: General Help
---

### Post by thezood on 2008-07-08
Hi guys,

I just accidentally pressed the Suspend button on my keyboard while watching a movie. The system hibernated fast as hell and when I booted the computer again, nothing happened. Having read that hibernate/suspend doesn't work well, I just reset my computer. 

After reboot, GRUB couldn't load (Error 17 and Error 21). Having had this problem before, I just booted the Live CD to reinstall GRUB. That didn't work because I was unable to mount the root filesystem. The partition editor didn't even recognize it as a valid partition. So I ran fsck on it and it found many, many errors. After correcting these, I was able to mount the root filesystem but there was nothing left on my drive whatsoever! All my documents, all OS files, everything was gone! The only thing left is a lost+folder containing a hundred or so files named #2098680. Apparently, fsck deleted the ext3 journal, making the filesystem ext2 instead.

Does anyone know if there's any way of recovering my files? And is this something that has happened to anyone else? I read that many people had problems with hibernation but this... This is just absurd. 

I actually think of abandoning Ubuntu after this, because if it's possible to mess up the root partition this bad by just pressing one button, then it is simply not useable. I wonder what other "little surprises" there are in Ubuntu?

---

### Post by thezood on 2008-07-08
Allright, I think I've recovered much of my data (allthough no filenames so sorting will be hell). Still, I'm very much interested in how this could have happened. The thing is, I remember I accidentally pressed the hibernation key when I first installed Ubuntu last year and the same thing happened then. I had to reinstall then too. I didn't think of it until now because it wasn't a big deal then, since I had nothing on the partitions.

So this happened twice with different Ubuntu versions. Very, very weird indeed.

---

