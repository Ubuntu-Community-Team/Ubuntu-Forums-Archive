---
title: "cryptsetup password prompt not always shown"
date: 2017-01-07
forum: General Help
---

### Post by ayup on 2017-01-07
Hi, 

I am running Ubuntu 16.04.1 LTS with encryption, but for a while now the cryptsetup password prompt during booting doesn't always show, instead this step is skipped and I jump directly to the screen where I am asked to type in my "normal" password. It took me a while to notice this because otherwise everything works and the booting process doesn't show any other errors, it is really only that the step where I enter the cryptsetup password is skipped. And it doesn't always happen. I can't determine any rule when it happens and when it doesn't, it seems random to me, but there could be something that I'm just not seeing.

I did some research and couldn't find an already described bug that fit my problem.

Can someone make sense of this and help me troubleshoot?

Thanks a lot and best!

---

### Post by hphde on 2017-01-10
Are you sure you have a proper LUKS setup? Without entering the passphrase you cannot really boot a crypted system.

---

