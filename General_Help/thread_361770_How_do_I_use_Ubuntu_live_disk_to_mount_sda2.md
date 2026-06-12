---
title: "How do I use Ubuntu live disk to mount sda2?"
date: 2007-02-14
forum: General Help
---

### Post by Athanasius on 2007-02-14
I would like to use the Ubuntu live disk to mount my hard disk (sda2) so that I can copy some info to cd-rom before I re-format.  Can someone please give me a step-by-step?

---

### Post by llamakc on 2007-02-14
Open the terminal. 

sudo mount /dev/sda2 /mnt

cd /mnt

---

### Post by Athanasius on 2007-02-14
I will try it and see what happens

---

### Post by Athanasius on 2007-02-14
Do I have to add anything to /etc/fstab?

---

### Post by llamakc on 2007-02-14
That will mount your drive to /mnt. If you need to specify a filesystem type, the command would be:

sudo mount -t vfat /dev/sda2 /mnt [for a FAT partition]

and so on depending on the partition's format. From there, I guess you could use whatever burning program exists on the LiveCD.

---

### Post by llamakc on 2007-02-14
> **Athanasius said:**
> Do I have to add anything to /etc/fstab?

No, the command will manually mount it for the time period you have the LiveCD in.

---

### Post by Athanasius on 2007-02-14
Once I get to the /mnt part then what?  Is there a way to make it come up on the desktop?

---

### Post by Athanasius on 2007-02-14
Oh, I see it all under mnt/home/ath.. nevermind.  Thank you so much.  

You can burn cd's in Nautilus right?

---

### Post by llamakc on 2007-02-14
To be honest, I do not know. Perhaps when you boot the LiveCD, it will already be mounted? If so, there will be icons on the desktop pointing to the partitions.

If there is not an icon, and you manually mount it, you would then open the burner program like:

sudo nameofprogram

and then use its navigable windows to find the data you want to burn. 

There may be other ways though: what type of partition is sda2? A leftover linux partition? A windows partition? How much data are you speaking about?

---

### Post by llamakc on 2007-02-14
I guess you have two cd drives, with one being a burner. I'm not sure what program is on the LiveCD, or if burning works in Nautilus from the LiveCD. Plop a blank in your burner and see what happens.

---

### Post by Athanasius on 2007-02-14
It is a Linux partition and maybe a cd's worth of data.. it is fine though,, it's all good.  Thank you very much for your help

---

