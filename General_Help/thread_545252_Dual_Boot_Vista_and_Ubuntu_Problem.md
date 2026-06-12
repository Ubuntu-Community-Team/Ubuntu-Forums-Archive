---
title: "Dual Boot Vista and Ubuntu Problem"
date: 2007-09-07
forum: General Help
---

### Post by tootlet on 2007-09-07
Greetings,
I have Windows Vista 32 bit Ultimate on sda and Ubuntu 7.04 i386 on sdb. Been tweaking Ubuntu and finally got everything set up as I want with SAMBA sharing and nfs working, printing etc. Booted into Vista to update the data on the 2 programs that are the only reason I run Windows. No problems. But the annoying gadget taskbar kept popping up. So I attempted to go into Control Panel to disable this annoyance. It would flash on the screen but disappear. I tried starting as administrator. Nada. Googled. One guy said to run sfc /scannow from an administrator's command prompt. Results said it was okay. (Don't know what the h*ll that does but it seemed to test the installation integrity...or something). Next suggestion was to boot from the Vista DVD and try a repair. This will wipe out my Grub mbr and I won't be able to get into Ubuntu. Any ideas on how to repair Vista and still avoid a reinstallation of Ubuntu? 

I may just go back to XP as I know I can get it to play nice with Ubuntu but I hate to waste the 10 hours I've invested in getting this machine ticking (mostly) the way I want it to! Thanks,
Tom

---

### Post by confused57 on 2007-09-07
You can reinstall grub with the Ubuntu live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by tootlet on 2007-09-07
Thanks, got my weekends work cut out for me. I'll keep my fingers crossed though that really messes up my typing1
Tom

---

### Post by confused57 on 2007-09-07
If your bios can boot first to your Ubuntu drive, another possiblity would be to install grub's IPL to it's mbr, using the live cd...then you might be able to boot your Vista drive from grub, similar to what's explained in this thread:
[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

If you decide to do this(install grub to your 2nd drive's mbr), you'll need to change root from (hd1,y) to (hd0,y)...

---

### Post by tootlet on 2007-09-08
Thanks for the help. I followed the first link and determined where grub was booting from. Then I booted the Vista DVD and selected repair. It even allowed me to skip fixing the mbr.  I rolled back to a restore point before several Vista updates were applied. Fixed my problem with Control Panel. And it didn't bother my grub boot loader. So I was back in business in 20 minutes. XP would never have let me avoid wiping the mbr. Thanks for the link. I'm only using Windows for 3 legacy programs. Enjoying Ubuntu the more I use it. 
Tom

---

