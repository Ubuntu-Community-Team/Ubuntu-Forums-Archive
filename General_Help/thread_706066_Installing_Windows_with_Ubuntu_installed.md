---
title: "Installing Windows with Ubuntu installed"
date: 2008-02-24
forum: General Help
---

### Post by ali999 on 2008-02-24
Hi, I'm trying to install a dual boot with Windows XP. I already have Ubuntu 7.10 installed on my system. I want to install XP on a seperate hard disk so I figured it would simply be a matter of putting in the WIndows disc and rebooting my system and then fixing GRUB to dual boot. Unfortunately when I restart my system the GRUB boot loader won't load the windows cd. I followed the instructions found here: [http://cutecomputer.wordpress.com/2006/10/10/boot-cdrom-through-grub/](http://cutecomputer.wordpress.com/2006/10/10/boot-cdrom-through-grub/)

Now when I restart I can choose to boot from a CD-ROM but when I choose it, my computer just ends up restarting.

Can anyone please help me here. I really need to install XP to get some of my programs to work.

---

### Post by dcstar on 2008-02-24
> **ali999 said:**
> Hi, I'm trying to install a dual boot with Windows XP. I already have Ubuntu 7.10 installed on my system. I want to install XP on a seperate hard disk so I figured it would simply be a matter of putting in the WIndows disc and rebooting my system and then fixing GRUB to dual boot. Unfortunately when I restart my system the GRUB boot loader won't load the windows cd. I followed the instructions found here: [http://cutecomputer.wordpress.com/2006/10/10/boot-cdrom-through-grub/](http://cutecomputer.wordpress.com/2006/10/10/boot-cdrom-through-grub/)

Now when I restart I can choose to boot from a CD-ROM but when I choose it, my computer just ends up restarting.

Can anyone please help me here. I really need to install XP to get some of my programs to work.

Dual booting is so boring these days, install VMware Server and then install Windows in a VM......   :)

---

### Post by Mustard on 2008-02-24
> **ali999 said:**
> Hi, I'm trying to install a dual boot with Windows XP. I already have Ubuntu 7.10 installed on my system. I want to install XP on a seperate hard disk so I figured it would simply be a matter of putting in the WIndows disc and rebooting my system and then fixing GRUB to dual boot. Unfortunately when I restart my system the GRUB boot loader won't load the windows cd. I followed the instructions found here: [http://cutecomputer.wordpress.com/2006/10/10/boot-cdrom-through-grub/](http://cutecomputer.wordpress.com/2006/10/10/boot-cdrom-through-grub/)

Now when I restart I can choose to boot from a CD-ROM but when I choose it, my computer just ends up restarting.

Can anyone please help me here. I really need to install XP to get some of my programs to work.

Rather than trying to boot a CD through Grub, you could change your bios settings at startup to first look for a CD to boot from rather than looking for a hard drive first.  Have you ever used BIOS before?  Or is your computer one of these 'legacy computers' spoken of in the article you linked?

---

### Post by toa on 2008-02-24
> **ali999 said:**
> Hi, I'm trying to install a dual boot with Windows XP. I already have Ubuntu 7.10 installed on my system. I want to install XP on a seperate hard disk so I figured it would simply be a matter of putting in the WIndows disc and rebooting my system and then fixing GRUB to dual boot. Unfortunately when I restart my system the GRUB boot loader won't load the windows cd. I followed the instructions found here: [http://cutecomputer.wordpress.com/2006/10/10/boot-cdrom-through-grub/](http://cutecomputer.wordpress.com/2006/10/10/boot-cdrom-through-grub/)

Now when I restart I can choose to boot from a CD-ROM but when I choose it, my computer just ends up restarting.

Can anyone please help me here. I really need to install XP to get some of my programs to work.

What about your Harddrive, you said you installed ubuntu! was the drive totally allocated to ubuntu with ext2 or ext3 filesystem, make sure you have a seperate empty partition with NTFS prepared for windows.

How is the drive structured?

---

### Post by Mustard on 2008-02-24
I'd add that this is also going to be a problematic experience.  Ideally you should install windows XP first and then Ubuntu second.  Ubuntu behaves well with windows and doesnt try to override it.  Windows however will attempt to control the system at the expense of another operating system.  Examples of this are, window won't boot from a slave drive (without some tricky little tweaks in grub), it has to be on the master drive.  I dont think Windows will go on anything else but the primary partition, but I may be wrong about that.  Also windows will overwrite grub after installation, so you would have to manually reinstall grub to boot into Ubuntu.

If it is at all possible for you to start the whole process again, then I would suggest you start from scratch, install windows XP, then do a clean install of Ubuntu.  Of course this is going to mean you lose all your data from Ubuntu, so that might not be a reasonable option for you.

It is possible to install windows second (and have windows on a second slave drive), but its not straightforward.

---

### Post by Mustard on 2008-02-24
> **toa said:**
> What about your Harddrive, you said you installed ubuntu! was the drive totally allocated to ubuntu with ext2 or ext3 filesystem, make sure you have a seperate empty partition with NTFS prepared for windows.

How is the drive structured?

Thats a good thought too.  He mentioned he has a second drive that he wants to install windows on.  I suspect that the second drive is not the master drive however.  He would be attempting to install WinXP on a slave drive and I dont think that is going to work.

---

### Post by toa on 2008-02-24
> **ali999 said:**
> Hi, I'm trying to install a dual boot with Windows XP. I already have Ubuntu 7.10 installed on my system. I want to install XP on a seperate hard disk so I figured it would simply be a matter of putting in the WIndows disc and rebooting my system and then fixing GRUB to dual boot. Unfortunately when I restart my system the GRUB boot loader won't load the windows cd. I followed the instructions found here: [http://cutecomputer.wordpress.com/2006/10/10/boot-cdrom-through-grub/](http://cutecomputer.wordpress.com/2006/10/10/boot-cdrom-through-grub/)

Now when I restart I can choose to boot from a CD-ROM but when I choose it, my computer just ends up restarting.

Can anyone please help me here. I really need to install XP to get some of my programs to work.

Take MUSTARD solution of overdoing the whole thing, i forgot about the second harddrive... 

Do the thing from scratch, specially if its a new ubuntu installation,

It's a future solution..

---

### Post by toa on 2008-02-24
> **ali999 said:**
> Hi, I'm trying to install a dual boot with Windows XP. I already have Ubuntu 7.10 installed on my system. I want to install XP on a seperate hard disk so I figured it would simply be a matter of putting in the WIndows disc and rebooting my system and then fixing GRUB to dual boot. Unfortunately when I restart my system the GRUB boot loader won't load the windows cd. I followed the instructions found here: [http://cutecomputer.wordpress.com/2006/10/10/boot-cdrom-through-grub/](http://cutecomputer.wordpress.com/2006/10/10/boot-cdrom-through-grub/)

Now when I restart I can choose to boot from a CD-ROM but when I choose it, my computer just ends up restarting.

Can anyone please help me here. I really need to install XP to get some of my programs to work.

Take MUSTARD solution of overdoing the whole thing, i forgot about the second harddrive... 

Do the thing from scratch, specially if its a new ubuntu installation,

It's a future solution if your planning to keep WIndows..

---

### Post by ali999 on 2008-02-24
> **Mustard said:**
> Thats a good thought too.  He mentioned he has a second drive that he wants to install windows on.  I suspect that the second drive is not the master drive however.  He would be attempting to install WinXP on a slave drive and I dont think that is going to work.

I could set my second drive as master...and set my current master one to slave. I don't know if my Ubuntu will load properly though after that. Any suggestions?

---

### Post by toa on 2008-02-24
> **ali999 said:**
> I could set my second drive as master...and set my current master one to slave. I don't know if my Ubuntu will load properly though after that. Any suggestions?

Generally it was always Ubuntu taking over Windows with its GRUB, i dont know even if you manage to install windows, you might end up installing ubuntu again to recognize Windows... ?

---

### Post by Mustard on 2008-02-24
> **ali999 said:**
> I could set my second drive as master...and set my current master one to slave. I don't know if my Ubuntu will load properly though after that. Any suggestions?
As long as you don't overwrite your drive that has Ubuntu installed on it, it will be possible to recover.  

In saying its possible I would also have to say that it depends on how confident you are that you understand certain processes like manually reinstalling grub and googling up solutions online for any hurdles you might strike along the way.

Offhand I would say that you could install WinXP to the master drive, Afterwards you may need to manually install grub again to gain access to your old Ubuntu installation.

Having the tools at hand BEFORE you start the process would be a good idea too.  I would print out any guides that you might need so you can access them without needing a running system, and I would have a good Live CD of some kind that you could use a temporary operating system or rescue tool should things go amiss.

Good luck. It should be an interesting learning experience at the very least. :)

---

### Post by Tanno on 2008-02-24
Try following this and see if this helps. There are guides here to show every which way to install Linux and Vista or XP.

[The definitive dual-booting guide: Linux, Vista and XP step-by-step]("http://apcmag.com/5162/the_definitive_dual_booting_guide_linux_vista_and_xp")

Maybe it'll give some insight to your issue.

---

### Post by ali999 on 2008-02-24
> **toa said:**
> Generally it was always Ubuntu taking over Windows with its GRUB, i dont know even if you manage to install windows, you might end up installing ubuntu again to recognize Windows... ?

I actually don't mind doing tht at all, but I need to get my windows installed first. I'll try some of this stuff out and see what happens

---

### Post by ali999 on 2008-02-24
> **Mustard said:**
> Rather than trying to boot a CD through Grub, you could change your bios settings at startup to first look for a CD to boot from rather than looking for a hard drive first.  Have you ever used BIOS before?  Or is your computer one of these 'legacy computers' spoken of in the article you linked?

Changing the BIOS settings worked. BIOS was set to try and boot from hard disk first then the CD. I just changed the order. Gonna end up having to reinstall Ubuntu though afterwards I think.

---

### Post by Mustard on 2008-02-25
> **ali999 said:**
> Changing the BIOS settings worked. BIOS was set to try and boot from hard disk first then the CD. I just changed the order. Gonna end up having to reinstall Ubuntu though afterwards I think.

Thats good.  Well done. :)

---

### Post by ali999 on 2008-02-25
Alright....problem is still not fully solved. I got the boot disk to run, I run the Windows boot up and chose to install it on my second disk. This didn't work however though, setup would format and copy the files over but when it restarts to do the installation I get a boot error. I figured this might be because I was installing it on a slave disk so I reset it to master. But then I get an error saying Buffer I/O error reading from fd0 or something like that when I try to install Windows again. I figured this was because none of my disks were formatted to NTFS. I ended up reinstalling Ubuntu on my slave disk. Now I'm wondering if I use gparted to format the drive as NTFS, and then install windows on it, would that work?

---

