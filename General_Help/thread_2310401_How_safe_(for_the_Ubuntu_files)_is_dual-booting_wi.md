---
title: "How safe (for the Ubuntu files) is dual-booting with Windows?"
date: 2016-01-18
forum: General Help
---

### Post by Jon_Huse on 2016-01-18
Just wanted some opinions on this. 

I switched to Ubuntu years ago, primarily because of security concerns with Windows. However, there are still a handful of things I need to use Windows for. Currently, I'm using Virtualbox so the Windows install doesn't have access to the filesystem. Windows 7 will no longer update correctly inside the virtual environment though, which is an issue.  

How safe would it be to dual-boot a Windows install from a second hard drive? Would the Windows install have full access (while running) to the Linux files? 

What I don't want to risk is a scenario where ransomware or some other malware on the Windows OS can harm the Ubuntu files. 

Thoughts? 

Thanks.

---

### Post by yancek on 2016-01-18
> How safe would it be to dual-boot a Windows install from a second hard drive? 

Easier than on the same drive if you do not have a lot of experience installing systems.  The second hard drive would have to be an internal hard drive as windows installer will not install on a usb drive.

> Would the Windows install have full access (while running) to the Linux files? 

No.  It wouldn't have any access at all.  The only thing you are likely to see of Linux is the Healthy partition in Disk Management.  Windows is not capable of reading or writing to any Linux filesystem, a business decision on the part of microsoft.  No money in it for them.  There is third party software available but I don't know how good it is.
 
> 
What I don't want to risk is a scenario where ransomware or some other malware on the Windows OS can harm the Ubuntu files. 

Don't see how that could happen if windows can't read or write to the Linux filesystem.  The link below has some very useful information and a detailed tutorial on dual booting with windows.  Nothing on UEFI but if you have windows 7, you are probably not using it.

---

### Post by maxinstuff2 on 2016-01-18
Windows ransomware will typically target data in Windows userspace and/or Program Files directories if the malware has somehow gained administrator rights.

As in anything that lives under c:\Users, and perhaps c:\Program Files too.

I don't think it would go after your linux partition, there's no real way the malware would know that there was anything of value there.
With that said, there's new malware every day - best to just keep your Windows partition secure in the first place.

---

### Post by Jon_Huse on 2016-01-18
> **yancek said:**
> Easier than on the same drive if you do not have a lot of experience installing systems.  The second hard drive would have to be an internal hard drive as windows installer will not install on a usb drive.



No.  It wouldn't have any access at all.  The only thing you are likely to see of Linux is the Healthy partition in Disk Management.  Windows is not capable of reading or writing to any Linux filesystem, a business decision on the part of microsoft.  No money in it for them.  There is third party software available but I don't know how good it is.
 


Don't see how that could happen if windows can't read or write to the Linux filesystem.  The link below has some very useful information and a detailed tutorial on dual booting with windows.  Nothing on UEFI but if you have windows 7, you are probably not using it.

Thank you for the info. This clears up things quite a bit. 

> **maxinstuff2 said:**
> Windows ransomware will typically target  data in Windows userspace and/or Program Files directories if the  malware has somehow gained administrator rights.

As in anything that lives under c:\Users, and perhaps c:\Program Files too.

I don't think it would go after your linux partition, there's no real  way the malware would know that there was anything of value there.
With that said, there's new malware every day - best to just keep your Windows partition secure in the first place.

Thanks for the help. 

Agreed about keeping Windows secure. Part of the motivation for moving outside the VM is that I really want to keep it updated, which isn't happening now.  

Back when I was on that platform, I always ran A/V and used Sanboxie to browse. Still, it's hard for me to trust that OS.

---

### Post by Bucky Ball on 2016-01-19
Windows wouldn't have a clue what an EXT partition is, let alone read/write to it. Access irrelevant. Win can't use them. You couldn't write to an EXT partition from Win if you wanted intentionally (without some manual intervention and installing some workarounds).

---

### Post by Cavsfan on 2016-01-19
I also wanted to mention that you definitely do not want to write to your windows partition from a linux partition.

Windows keeps track of everything and when another OS writes to that partition bad things could happen.

I learned that the hard way several years ago on Vista when the auto backup of my files broke. I ended up having to re-install windows and I had never in my life had to do that before.
I've moved to Windows 7 and now 10 and cannot even mount the C: drive from Xubuntu Xenial Xerus 16.04, which is totally fine with me.

I also have Arch Linux on this box and I am able to mount C: read only from there, which I like.

Cheers

---

### Post by Bucky Ball on 2016-01-19
What Cavsfan said ...

Messing with your Win OS partition from a booted Ubuntu install is not a good idea.

---

### Post by pfeiffep on 2016-01-19
> **Bucky Ball said:**
> What Cavsfan said ...

Messing with your Win OS partition from a booted Ubuntu install is not a good idea. I certainly agree with this, but want to add that having a separate drive for data formatted NTFS is one method for sharing data between Windows and Linux.

---

### Post by Cavsfan on 2016-01-19
> **pfeiffep said:**
> I certainly agree with this, but want to add that having a separate drive for data formatted NTFS is one method for sharing data between Windows and Linux.

Indeed you are right! I have a 1TB USB drive formatted to NTFS. I'll use that to save something I want to get with Windows later. So that is a solution for both Windows and Linux systems.

---

