---
title: "Dual boot - Cannot Boot Windows"
date: 2013-05-20
forum: General Help
---

### Post by SylntWlf on 2013-05-20
Hi, I'm new to Ubuntu so I bought a magazine dedicated to beginners on how to dual boot Ubuntu and a version of Windows. I completed this fine but now I am unable to boot in Windows (Vista). From the research I've done I think that GRUB might be looking at the recovery partition instead of the main OS partition. Maybe I'm wrong? When I try to boot into Windows I get the recovery console window and set of options. However, while I am in ubuntu I can see the Windows drive and all of my files are intact. Please help!

---

### Post by Albury_Boy on 2013-05-20
The first time I dual booted my laptop Windows was a bit 'funny'. I had to stuff around a little to get it working properly again. When you select the Windows bootloader, what options do you get?

---

### Post by SylntWlf on 2013-05-20
> **Albury_Boy said:**
> The first time I dual booted my laptop Windows was a bit 'funny'. I had to stuff around a little to get it working properly again. When you select the Windows bootloader, what options do you get?



The Microsoft Load bar on the bottom but then it goes to the screen with the recovery options such as command prompt, system restore, disk check for errors, etc.

---

### Post by Mark Phelps on 2013-05-20
Did you make the mistake of using the installer SLIDER to shrink Vista to make room for Ubuntu?  If so, you likely corrupted the Vista boot loader and that now prevents it from booting.

When you get into the Recovery screen, see if there is a Repair Install option.  If so, run that three times, that's right, three times.  That will restore Vista booting but you'll then have to repair GRUB to get access back to Ubuntu.

---

### Post by Albury_Boy on 2013-05-20
Yeah. I dual boot Win7/Ubuntu, and I used the slider too. This was a couple of years ago, so I can't remember the exact procedure. I remember using the repair install option (not sure about the three times thing). It fixed Windows and it would work fine, but then GRUB disappeared. Then I fixed GRUB. It all settled down in the end. 

My best advice is, when you get it working properly again, image your drive so you can re-install everything if you screw it up. Oh.. and avoid upgrading the Ubuntu distro until it's absolutely necessary.

---

### Post by helixo on 2013-05-21
try getting a recovery disk or an installation CD and use them to get a command prompt , or any how just try getting a command prompt and type these :
bootrec.exe/FixBoot
(press enter)
bootrec.exe/FixMbr
(press enter)

reboot 


in simple words this will make windows bootloader to boot before grub/grub2
so once you get into windows,
you can either think of removing ubuntu or installing a software that can deal with multiboot like BSD

---

### Post by SylntWlf on 2013-05-21
Thanks for the tips, and yes I did use the slider to adjust the partition size. I will use the repair option three times as suggested.

---

### Post by SylntWlf on 2013-05-21
> **Mark Phelps said:**
> Did you make the mistake of using the installer SLIDER to shrink Vista to make room for Ubuntu? If so, you likely corrupted the Vista boot loader and that now prevents it from booting.

When you get into the Recovery screen, see if there is a Repair Install option. If so, run that three times, that's right, three times. That will restore Vista booting but you'll then have to repair GRUB to get access back to Ubuntu.


There is a startup repair utility. I'm guessing this is the repair install you are talking about? I didn't bother doing a backup of the Windows partition simply because nothing on there was needed. Since I'm new to Linux I did use the slider but after doing research I'm seeing many newbies have troubles dual booting with Windows, especially Windows 8.

---

### Post by Mark Phelps on 2013-05-21
> **SylntWlf said:**
> There is a startup repair utility. I'm guessing this is the repair install you are talking about? I didn't bother doing a backup of the Windows partition simply because nothing on there was needed. Since I'm new to Linux I did use the slider but after doing research I'm seeing many newbies have troubles dual booting with Windows, especially Windows 8.

Windows 8 is an entirely different set of problems, some SERIOUS, because the machines that come preloaded use UEFI (instead of MBR) boot and often have secure boot enabled.  It is a LOT of work to get those dual-booting, and if that is what you have, you will need to wait until someone comes along that understands the details of UEFI booting and secure-boot.  Sorry

---

### Post by oldfred on 2013-05-21
With Vista the os-prober often mis-identified the recovery and main install. Entries were often reversed in grub menu. Have you tried booting the recovery mode boot option in grub menu. That may be your install.

If not the case, then we may need to see details. But Boot-Repair will not fix Windows most Windows issues which need a Windows repair CD or flash drive.

 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by SylntWlf on 2013-05-22
I ran the startup utility twice and it fixed the problem. I'm not even going to attempt a dual boot with Windows8. From the forums I've seen it is alot of work and can cause alot of problems.

---

### Post by SylntWlf on 2013-05-23
I was able to get Vista working again. I used the repair utility. Not sure if maybe a file necessary for booting was corrupted or maybe GRUB was looking at the recovery partition. Either way I ran it twice and it works fine now. Might get rid of Windows altogether and run the latest version of Ubuntu.

---

### Post by Albury_Boy on 2013-05-23
Great to hear you've got everything working ok. A word of warning about the latest and greatest versions of Ubuntu though. If you like to tinker with your PC then go ahead and install 13.04. BUT... if you need a stable work environment, and need everything to 'just work', then go with the 12.04 LTS. 

Upgrading the OS can be a tricky matter and requires a level of commitment to getting everything to work again. Some things WILL break during upgrades. Common things include display and wifi drivers. Other weird things can happen too, like your touchpad won't work after an upgrade. So, pick a distro and try to stick with it. If you do decide to change to a newer version, then a backup, format and re-install is often the best method.

I rarely use Windows these days, but every now and then I need it. Things like doing tax returns (e-tax Australia) can be hard to get working with WINE (the Windows emulation layer). If you like to game, you will often find it frustrating in Linux. OpenGL is good, but still not as good as DirectX.... yet.

All the best with your Linux adventure :-)

---

### Post by SylntWlf on 2013-05-23
I've heard many people talking about 12.04. What are the issues with 13.04? I have Win8 installed on my laptop for gaming and I regret it. I might install Win7. I just can't get a feel for Win8. Also, if I do install something else it will just be a distro and not a dual boot.

---

### Post by Albury_Boy on 2013-05-23
Honestly, I have no idea what 'potential issues' 13.04 may have. It is the current testing and development release which incorporates the new features which have been developed by the Canonical team, Debian team and volunteers from all over the world. From personal experience with the 'rolling releases' of Ubuntu, I know that there is almost always something broken, and it's always annoying. 

Ubuntu 11.10 broke X11 for me (that runs the GUI display environment). I had nothing but a black screen for three days. I had this forum up constantly on my phone. Asking questions, and trying possible solutions. 

Ubuntu 12.04 is the LTS or 'Long Term Support' version. It's a stable release with support and updates until 2017. 

Think of 13.04 as a beta, and 12.04 as a final release.

You need to ask yourself: 
"Do I want a stable desktop environment with guaranteed support?" **OR **
"Do I want the latest features to tinker with and support ongoing development by submitting valuable bug reports?" 

I run 12.04 on my server - because I need a stable production environment.
I run 12.04 on my main laptop - because I need to get work done and it's frustrating when things are broken.
I tinker with other distro's on an old laptop to get a feel for them, and I don't care if I have to format the HDD and reinstall everything.

Your choice man.

---

### Post by Mark Phelps on 2013-05-23
> **SylntWlf said:**
> ... I have Win8 installed on my laptop for gaming and I regret it. I might install Win7. I just can't get a feel for Win8...

I'm part of a small but growing enthusiast community that insists on using Win8 in "Win7 mode" -- meaning that we use the Desktop exclusively and have installed third-party software to return the look and feel of Win7 to our Win8 systems.

A leader in this area is Stardock.  They offer Start8 (returns the Start menu with direct booting to the Desktop), WindowBlinds 8 (which returns Aero-like transparency to the desktop look and feel) and ModernMix (which allows you to run Metro apps in actual Windows).

So, if you're willing to experiment with Win8 along these lines, like some of the rest of us, you may grow to like it.

---

