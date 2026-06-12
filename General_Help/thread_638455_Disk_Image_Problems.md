---
title: "Disk Image Problems"
date: 2007-12-12
forum: General Help
---

### Post by Trurl on 2007-12-12
I have an ailing 60 GB laptop harddrive. On it are two main partitions--Windows XP Pro and Feisty. 

I recently purchased a 120GB harddrive and my plan was as follows: Image the XP partition, transfer it to the new harddrive, and then install the latest ubuntu (I don't mind losing the old partition). 

I created the windows image using DriveImage XML and appear to have successfully transfered it to the new drive. However, I cannot boot from the imaged disk. I get the "no bootable media found" error. 

I also cannot image ubuntu and go from there because DriveImage can't seem to handle my linux partition. 

I thought perhaps the boot problem is because I normally use GRUB to load the boot table, but since I don't have GRUB on the imaged disk, perhaps this is causing the problem?

So: any ideas on how I can succeed at my devious plan to: boot from the imaged disk; install updated ubuntu in a new, larger partition; rejoice ?


Thanks for any help!

---

### Post by kpkeerthi on 2007-12-12
You may want to re-install GRUB on your new HDD. Try [Super GRUB Disk]("http://supergrub.forjamari.linex.org/").

---

### Post by Trurl on 2007-12-12
Thanks, I'll give it a shot! However, I'm not sure how/where to install it to the new hard drive since I can't boot from that hard drive to begin with. 

Also, does GRUB work without Linux? That's probably a silly question but I'm not very familiar with the boot process.

---

### Post by kpkeerthi on 2007-12-12
You need to boot off Super GRUB disk. You don't have to install it to hard drive. Spend some time reading the docs.

You do not need to have linux for GRUB to work. GRUB can boot windows just fine.

---

