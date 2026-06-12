---
title: "Is ntfs-3g safe?"
date: 2007-06-16
forum: General Help
---

### Post by zigx on 2007-06-16
The site says:
"The driver is in STABLE status since February 2007"

but im looking for any feed back to help me build confidence before i risk killing something that might make me want to kill myself ;)
:KS

---

### Post by logos34 on 2007-06-16
It's worked virtually flawlessly for me since last year.  I've only had to run ntfsfix once and it cleared up whatever the problem was.  I write to configuration files as well as documents on windows partition all the time without incident.

---

### Post by Happy_Man on 2007-06-16
It's fine. Don't be scared by the naysayers; they're just trying to save their own skins in case something does happen. Which it won't. There are far more users like me that have had no problems with ntfs-3g, it's just that on a support forum, you won't see very many posts about it. ;)

---

### Post by zigx on 2007-06-17
im gonna be resizing something like 2.8k images (each about 2mb) that are stored on my windows partition...   do you think this kind of small but massive I/O is grounds for screwing something up?

thanks.

---

### Post by Happy_Man on 2007-06-18
I save entire DVD isos to my Windows partition. Nothing bad has ever happened. ntfs-3g is rock-solid.

---

### Post by black_magician on 2007-06-18
I've been using ntfs-3g for about a year now.  no problems yet!  plus, it was much easier to get working in feisty compared to edgy.

---

### Post by stchman on 2007-06-18
> **zigx said:**
> The site says:
"The driver is in STABLE status since February 2007"

but im looking for any feed back to help me build confidence before i risk killing something that might make me want to kill myself ;)
:KS

I have had no problems using ntfs-3g.  I don't do a whole lot of writing to my ntfs partitions but I do enough.  Don;t be afraid to try it.  I have a page dedicated to partition access.

[http://www.stchman.com/part.html](http://www.stchman.com/part.html)

---

### Post by dannyboy79 on 2007-06-18
the only problem I have ever had was when my linux box froze up and I had to do a hard shutdown, then you need to mount it within windows, then unmount it safely. luckily this was a external disk. the ntfsfix wouldn't work either. It's a simple fix though if you have access to a winbloz box, I have since purchased a little device that converts any sata or ata drive to a usb drive, it's awesome. So if that does happen to you, this little adpater is a god send so if it is an internal disk, you would only have to open up your ubuntu box and not the new windows box you want to mount it too as well. ANyway, other than that, NTFS-3g is awesome, on anohter note, I also use ext2fs-driver ([http://www.fs-driver.org/index.html](http://www.fs-driver.org/index.html)) to write to my external ext3 hard drives within winbloz. but the same goes, I have has a BSOD in winbloz and then the ext3 external disk couldn't be accessed in windows until I ran fsck on the drive, then I could again use it in windows using the fs-driver. good luck

---

### Post by warcriminal on 2007-06-18
NTFS-3g is perfectly safe, we've been using it in a production enviroment now for several months and it's performed flawlessly.

There is a guide at;

[http://www.goitexpert.com/entry.cfm?entry=Make-Your-Windows-Share-ReadWriteable-From-Linux](http://www.goitexpert.com/entry.cfm?entry=Make-Your-Windows-Share-ReadWriteable-From-Linux)

that shows you how to configure it.

---

### Post by jayson.rowe on 2007-06-18
I can say that ntfs-3g did ONE thing for me...It finally broke me from Dual-Booting Windows! Thankfully most of my Data was safe (external drive formatted fat32), however it hosed my NTFS partition windows (and SOME Data) was on - would no longer let me boot Windows - it corrupted the NTFS file system tried initially chkdsk-r to bring it back, but all it would do is report a corrupt partition (I was trying to edit some .doc's in OOo while booted into Ubuntu).

I wasn't really upset - it finally caused me to get Windows off my machine, and gave me an excuse to reload Ubutntu as I had really hacked around in the previous install learning my way, had Kubuntu and Xubuntu installe in it as well, and a gazillion packages I downloaded that I never used, so I needed to reload it anyway (I decided on Gnome, and didn't want any of the KDE stuff, and half the other crap i'd installed) - So now I have Ubuntu on my main drive w/ a 500MB /boot, the rest as / and on my second drive I have /home.

---

### Post by Balazs_noob on 2007-06-18
Using it for about a few months now and it works perfectly ......

---

### Post by kelvin spratt on 2007-06-18
i save everything in ntfs its as safe as it gets on my computer

---

