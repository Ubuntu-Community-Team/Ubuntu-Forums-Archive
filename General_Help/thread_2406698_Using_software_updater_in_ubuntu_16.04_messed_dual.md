---
title: "Using software updater in ubuntu 16.04 messed dual boot"
date: 2018-11-24
forum: General Help
---

### Post by xviktor on 2018-11-24
Hello,
So, i had a need to update firefox. I found instructions online that said easiest wa, to do so was to use software updater. When i ran it, it found quite a bit of updates so I just choose to update them all. Upon completion it asked me to restart PC and i restarted it. Usualy when restarting PC it boots up grub where I can pick beetwen ubuntu and windows 10. This time it booted up straight to windows 10 without booting up grub. First thing I tried was opening boot manager. There I saw that boot order was wrong first was windows boot manager(KINGSTONE some numbers etc) and second ubuntu(same as in the first one) so i picked ubuntu and it loaded grub and from there I went to ubuntu. There I uploaded some files theat i had to upload for projek I was doing(that was the reason I had to update firefox) and from there I tought that I know the solution. I restarted the PC went to BIOS boot options and there I saw that for boot optiona I had thees two. First was windows boot manager(same thing as in boot menu) and second was just eindows boot manager without anything else. So I was sceptical but I still tried chaning boot priority order so i jsut changed their places saved it and exited. And it still booted up windows. Then I tried going into boot menu again to see boot order this time it was as it should be, I stil picked ubuntu and it loaded windows. I went to bios again to see what is going on with priority order and there i saw that first priority, windows boot manager, changed name to couple of empty spaces. And second priority was still WBM(kingston etc) i changed them again and restarted went to bios and name again changed to WBM. So long story short forst time I managed to boot grub by manualy picking ubuntu in boot menu, after that I changed boot priority in BIOS so ubuntu goes first but BIOS and boot menu show diferent names for that option (BIOS - Windows Boot Manager, boot menu - ubuntu(kingstone...)), changing priority changes name of that option but not other, in boot menu names dont change, after changing boot priority in BIOS both options load windows. So how should i go about fixing this. Thanks in advance.
P.S. I have ubuntu 16.04, windows 10 and use uefi boot option

---

### Post by Impavidus on 2018-11-24
I never need a reason to upgrade firefox. I just install all available upgrades every day. That gave me one regression in 12 years.

I noticed an upgrade to grub a few days ago, although that was on 18.04 and I'm not sure there was a grub update on 16.04 too. It may be the culprit. Maybe your UEFI doesn't like the new grub.

Can you run [boot repair](https://help.ubuntu.com/community/Boot-Repair) from a live disk, create a boot info summary and show us the link? It may have some useful information. Also tell us some details about your hardware, like make and model. Some brands need some tweaking before they're willing to boot Ubuntu.

---

### Post by xviktor on 2018-11-24
Ok so, I am using Acer Aspire 5 A515-51G-39MV laptop. I have run boot repair. When I ran it it asked me to disable secure boot to continue I pressed yes and it continued and finished. After that I went to menu and pressed shutdown button, but it didnt'n want to shut down. It was stuck on, I guess, shutdown screen. It was stuck there for 40 minutes(wasn't frozen some dots were moving like it was loading something). After that I shuted it down manualy(using power button). After that i tried booting it up but I just get secure boot fail screen. After I press enter it just boots up windows, windows explorer opens and I get popup teling me that windows can't acces that disk. That it could be damaged or it must use form.that windows can recognize etc along those lines. It works good as much as I can tell. I can acces both windows partitions and no data seems to be lost. Here is pastbin link that was made after boot repair finished its job ([https://paste.ubuntu.com/p/MShm3gDgk4/](https://paste.ubuntu.com/p/MShm3gDgk4/)). Thanks in advance.

---

