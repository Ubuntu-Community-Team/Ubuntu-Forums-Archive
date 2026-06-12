---
title: "How to uninstalling one distro and install a new one"
date: 2013-05-07
forum: General Help
---

### Post by Kojak Peg on 2013-05-07
He everyone 
I'm dual booting with xp, and want to uninstall my current linux distro. So I can install a different one. I've had a look around the web, and everyone seems to be using a program called easyBCD. Then deleting the linux partition in windows disk management. Is this the best, or only way; or are there other, better ways to uninstall a linux distro?

Many thanks

---

### Post by Impavidus on 2013-05-07
If this is not wubi, you can have multiple linux versions installed at the same time or delete (overwrite) the old one as part of the installation process. Not needed to uninstall first.

---

### Post by grahammechanical on 2013-05-07
Are you using EasyBCD as the boot manager? If so at some time you will need to edit its menu to remove the entries for your present Linux distro and then to put in the entries for its replacement distro. I cannot help you with that. But as for replacing one Linux distro with another one, then I would say it would depend on what distro you want to replace.

You might want to try Linux Secure Remix. It used to be called Ubuntu Secure Remix and is often recommended on this forum for fixing boot issues. It has a utility called OS-Uninstall for just the purpose that you require. There is also the Boot Repair utility that you might need. It runs from a live session.

[http://sourceforge.net/p/linux-secure/wiki/Home/](http://sourceforge.net/p/linux-secure/wiki/Home/)

Regards.

---

### Post by Shrek01 on 2013-05-07
You don't need to uninstall the old distro.  When you install the new one, and you get to the part of Partitions, select to manually create your partitions and simply choose the partition used by the old distro.  That's it. As for the the dual boot part, it should detect your XP and add it to the list of choices you'll have on boot.
Just in case you choose the wrong partition, don't forget to backup all important things from your XP ;)

---

### Post by oldfred on 2013-05-07
Only Vista & 7 have BCD, XP uses boot.ini, so you cannot use EasyBCD with XP. We tend to prefer grub2 as it is designed for multi-booting where the Windows boot loader needs the third party or work arounds to make it work.

---

### Post by Kojak Peg on 2013-05-07
Thank you
everyone for your replies. I haven't deleted the partition yet. so don't have a boot problem, yet, but I'll keep the [COLOR=#000000]Boot Repair utility[/COLOR] in mind for the future, just in case. However, if I can, simply, overwrite the old distro with the new one, I'll do that. I just wasn't sure of how best to do it, because although I have used partitions before, I've never dual booted before. And I wanted to make sure, before doing anything drastic.
 
As for backing up, it's always a good idea, isn't it. And I'll probably be getting ride of xp, all together soon. So will have to transfer the files over. I did try out linux a while ago with an old laptop, but I've only just made the switch over properly and I have found I prefer linux. However it will be a long time before I give up on a GUI and try out Arch linux, lol

Thanks again everyone

---

### Post by Shrek01 on 2013-05-07
You'll be fine.  If you read everything step by step during the installation, and know that while asked for Partitions to set it manually, and if you set your old partition which will mean that the old partition will be formated and the new distro installed on it, and if you use the boot manager that Ubuntu uses (by default Grub will be installed)... you should be fine.  If you want XP to handle that, it is possibe with boot.ini  but not a good idea if you are trying to get rid of it in the future. 
By default Ubuntu takes over the boot management and handles it perfectly in my experience (unless you have a new computer with Windows 8 pre-installed, UEFI and boot secure). I installed hundreds of these (Ubuntu/Debian), and up to Windows 7 it was a breeze.  

If you are wondering, with Windows 8 and UEFI, secure boot and all this nonsense, it is just a little bit trickier and needs boot repair... but it is still possible.  
But in your case, dual boot with XP (or up to Windows 7) it shouldn't be a problem.  The Ubuntu installer does an excellent job!

Have fun! And unless you choose the wrong partition and format the windows one, there is always a way to get both OS back.

Cheers

---

