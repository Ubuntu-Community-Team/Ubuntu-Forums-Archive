---
title: "Need help recovering grub menu"
date: 2020-03-24
forum: General Help
---

### Post by drummond2 on 2020-03-24
Hello, 

A little background: I’m on a thinkpad x220 and was dual booted with Ubuntu/windows 7. I decided to upgrade windows 7 to windows 10. Went well but had a few issues with drivers so I installed a fresh copy of windows 10 onto the windows partition. Windows 10 now works but I lost my grub menu and can no longer boot into Ubuntu.

I’ve tried a lot and can’t seem to figure this out. I booted Ubuntu with live media. In gparted I can see my Ubuntu partition is still there. I tried running a command in cmd on windows 10 and that didn’t work either.

I’m trying to run boot repair now via the live media but I’m getting this error:

[https://imgur.com/a/EEuzh22](https://imgur.com/a/EEuzh22)

Can anyone help me out? I’m really stuck.
Thanks!

Edit: I generated this file with boot repair if it helps


[https://drive.google.com/file/d/1Sjzn2KQiR7RSDIPrRtVM8_NF-77L9zbu/view?usp=drivesdk](https://drive.google.com/file/d/1Sjzn2KQiR7RSDIPrRtVM8_NF-77L9zbu/view?usp=drivesdk)

---

### Post by yancek on 2020-03-24
> I installed a fresh copy of windows 10 onto the windows partition.  Windows 10 now works but I lost my grub menu and can no longer boot into  Ubuntu. 

Well, that should not be a surprise as that is and always has been expected behavior with a windows install.  It has overwritten the boot code in the MBR of the drive and now has windows code and that is why it only boots windows.  A Legacy install of windows will overwrite boot code in the MBR durin the install and the user will not be asked if that is wanted nor will the user be informed that it is happening.  It is possible to use bcdedit to create a boot entry for Ubuntu but it is a very convoluted process.  Reinstalling Grub is possible in a variety of ways and is what you need to do.  The link below explains several ways to do this including one using boot repair since you already have it.  See section 2.2 at the link below.

 [https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

Once you re-install Grub and get it working, you might clean up your kernels as you have an astounding number which are not needed or used.

---

### Post by oldfred on 2020-03-24
You also need to houseclean old kernels.
New versions of Ubuntu only keep 2 kernels.

[https://help.ubuntu.com/community/RemoveOldKernels](https://help.ubuntu.com/community/RemoveOldKernels)

---

