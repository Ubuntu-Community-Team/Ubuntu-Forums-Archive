---
title: "[SOLVED] Newbie &amp;quot;lost&amp;quot; windows"
date: 2007-12-30
forum: General Help
---

### Post by tonychar on 2007-12-30
Hi, I've just loaded Ubuntu with the live CD, aiming to have a dual boot system, to have a proper play with Ubuntu. However, when I boot up there is no option to boot windows, we go straight into Ubuntu.  

I have a sneaking suspicion I have overwritten the hard drive, as there was no option to size the partitions on installation.

I have everything saved on an external hard drive, using the windows back up tool before I went for the Install, but I don't have an idea on how to add that back in???  Can I restore Windows and start again?

I am no expert, so basic step by step advise would be very much appreciated!!

Thank you!!

---

### Post by zhouxing on 2007-12-30
> **tonychar said:**
> Hi, I've just loaded Ubuntu with the live CD, aiming to have a dual boot system, to have a proper play with Ubuntu. However, when I boot up there is no option to boot windows, we go straight into Ubuntu.  

I have a sneaking suspicion I have overwritten the hard drive, as there was no option to size the partitions on installation.

I have everything saved on an external hard drive, using the windows back up tool before I went for the Install, but I don't have an idea on how to add that back in???  Can I restore Windows and start again?

I am no expert, so basic step by step advise would be very much appreciated!!

Thank you!!

Probably you have used your whole harddisk as Ubuntu partition during the installation process. This means you could have lost all your data on your hard driver. Fortunately, you have backup in you external harddisk.

You could use Virtual Box or VMWare to install a virtual machine in your ubuntu, then you can install your windows.

But if you want to dual boot to windows and ubuntu, it is suggested that you install windows first, then install ubuntu on a seperate partition. In this way, Grub will configure your dual boot automatically.

---

### Post by tonychar on 2007-12-30
But if you want to dual boot to windows and ubuntu, it is suggested that you install windows first, then install ubuntu on a seperate partition. In this way, Grub will configure your dual boot automatically.[/QUOTE]

Thanks for the reply.

This is what I attempted, (a dual boot) but it seems I made a mistake with the partition options.

So how do I install Windows again?  It was pre-installed from new, but I do have the back up files to work with, but I can't just copy them to the hard drive and it give me a working windows os (can I?).

What I don't understand is how to install windows - if  I try to boot from my external drive, there is no install programme, it's just backed up files.

---

### Post by tonychar on 2007-12-30
> **zhouxing said:**
> Probably you have used your whole harddisk as Ubuntu partition during the installation process. This means you could have lost all your data on your hard driver. Fortunately, you have backup in you external harddisk.

You could use Virtual Box or VMWare to install a virtual machine in your ubuntu, then you can install your windows.

But if you want to dual boot to windows and ubuntu, it is suggested that you install windows first, then install ubuntu on a seperate partition. In this way, Grub will configure your dual boot automatically.

Sorry, just looked at the virtual box site.

If I understand this correctly, the software will use my back up data to create a virtual windows system within the Ubuntu operating system?

---

### Post by RC Howe on 2007-12-30
Something like that. If you plug your backup drive into Ubuntu it might recognize it, which will let you recover your data. Virtual Box may require a windows CD, I'm not sure.

I do not know if there is any good software to do a block-for-block clone of a hard disk, which is what you would need to do if you wanted to resize your Ubuntu partition and put Windows back exactly like the backup.

---

### Post by tonychar on 2007-12-30
> **RC Howe said:**
> Something like that. If you plug your backup drive into Ubuntu it might recognize it, which will let you recover your data. Virtual Box may require a windows CD, I'm not sure.

I do not know if there is any good software to do a block-for-block clone of a hard disk, which is what you would need to do if you wanted to resize your Ubuntu partition and put Windows back exactly like the backup.

It does recognise my Lacie hard drive, thanks for the help.  I appreciate it very much!:)

---

