---
title: "Grub Can't See My Windows Partition."
date: 2014-04-30
forum: General Help
---

### Post by john204 on 2014-04-30
I resized my windows 8.1 partition to make room for Ubuntu 14.04 LTS 64 bit.  Then, I tested my Windows 8.1 partition to make sure it was still functional.  Then, I went back into the Ubuntu start-up drive, created a primary Ubuntu and a Swap partition, then installed Ubuntu.  Now, I can only boot into Ubuntu.  I'd still like to use my Windows Partition from time to time.  Some of my work applications give me little choice.

I've got some screen shots, and I'm hoping somebody on here can give me some assistance clearing this up.  

I'd really appreciate any help.  I'm struggling to figure out how to get grub to show my windows 8 and recovery partitions.

Thanks in advance.

---

### Post by john204 on 2014-04-30
Nevermind.  I installed boot-repair.  It told me that I needed to disable secureboot in the bios before it could do anything.  Just on a hunch, after I disabled secureboot, I tested the windows partition.  Boots like a charm now.

Sorry to have wasted anbody's time, but maybe somebody else will need this and can fix it without instaling boot repair.

---

### Post by sammiev on 2014-04-30
> **john204 said:**
> Nevermind.  I installed boot-repair.  It told me that I needed to disable secureboot in the bios before it could do anything.  Just on a hunch, after I disabled secureboot, I tested the windows partition.  Boots like a charm now.

Sorry to have wasted anbody's time, but maybe somebody else will need this and can fix it without instaling boot repair.

It was a good read and will likely help others. Should mark it as "solved" :)

---

