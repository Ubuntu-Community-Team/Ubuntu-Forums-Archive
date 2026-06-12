---
title: "VMWare Grub Error 21"
date: 2007-03-24
forum: General Help
---

### Post by nickuntu on 2007-03-24
Hey all,

I recently installed Ubuntu Edgy, my first time with linux and I am LOVING IT. I haven't been on my WIndows partition in over 2 months now. I've also installed beryl and all that, its really nice i'm loving it.

Recently I've found the need to do some design with applications that are not available to Linux or work well with Wine, and so I'm attempting to boot up my second partition (on a seperate drive (windows)) using VMWare.

I have followed all the tutorials I can find, but I am consistently running into a GRUB ERROR 21 when I start my windows partition within VMWare and I don't understand for the life of me why it's happening.

Configuration:

hd0 - NTFS Partition (160GB)
hd1 - Linux drive (160GB) (including swap and all those partitions)

My GRUB has 2 options... my current Kernel and Microsoft XP.

But when I load the drive in VMWare GRUB doesn't load and just displays Error 21.

Anyone have any experience with this?

---

### Post by JohnPhys on 2007-03-25
The problem is that the vm needs to be able to read off of the linux partition in order to fully load grub and know where windows is to boot.

I tried adding the first partition to the vm, but that didn't work (it might for you).

Another thing you can do is boot the winxp cd (in the vm!!!!) and boot to the recovery console, and run "FIXMBR".  This should overwrite the virtual MBR (it should NOT overwrite the real MBR) so that everything will boot normally.  I have done this sucessfully.

Still, I'd use  the dd command to back up your MBR and partition tables to an external drive (they're very small file sizes) and have a live cd ready just in case things go wrong.

---

### Post by buddha001 on 2008-01-04
I'm having the same issue, except I get error 17 in grub. Of course I'm also running with a SATA disk which linux treats as SCSI and VMware doesn't like to work well booting into physical partitions using SCSI. So I may be hosed by that. Is there anyway of creating an image of my existing Windows installation and then using it as a virtual machine?

Thanks!

---

### Post by dcstar on 2008-01-05
> **buddha001 said:**
> 
............ 
Is there anyway of creating an image of my existing Windows installation and then using it as a virtual machine?

Thanks!

Yes, you download the free (Windows) convert utility from the VMWARE site and use it for exactly that purpose.

---

