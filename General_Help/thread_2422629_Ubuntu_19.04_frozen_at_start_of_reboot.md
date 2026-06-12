---
title: "Ubuntu 19.04 frozen at start of reboot"
date: 2019-07-10
forum: General Help
---

### Post by MibunoOokami on 2019-07-10
Hi all,
I seem to have a back to front problem. I went to restart my PC today and its stuck at the purple screen with the red dots going by, it's been like that for 10 minutes. All "helpful" info relates to this problem occurring at startup and mostly after a fresh install, neither of which apply to me.

Before opting to press and hold the power button, I happened to press f1 (which might be just as well) and see an error [FAILED] Failed unmounting /home

Now I don't know what to do, if /home didn't unmount and I force a shutdown it's possible I could lose some stuff right? But is there any alternative available?

Thanks

P.S I can't select Linux distro when posting this thread from mobile

---

### Post by oldfred on 2019-07-10
Generally pressing and holding Ctrl+Alt and
then PrintScr, R, E, I, S, U, B (Raising Elephants Is So Utterly Boring)
should do a clean reboot.
R gives back control of the keyboard, S issues a sync, E sends all processes but init the term signal, I sends all processes but init the kill signal, U mounts all filesystem ro to prevent a fsck at reboot, B reboots the system 

What brand/model system?
What video card/chip?
New install or older install & what recent changes?

      
 May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by MibunoOokami on 2019-07-11
I keep getting signed out every time I try to post...

Do I try that at the purple screen or the black screen from f1?

PC is Lenovo all in one,
I don't know the graphics details off hand.
Install a couple of weeks old, no recent changes.

Come to think of it, I added vboxuser (I think it was called) to groups earlier today. Apart from that no other changes.

---

### Post by MibunoOokami on 2019-07-11
> **MibunoOokami said:**
> Do I try that at the purple screen or the black screen from f1?

Since the purple screen is the one normally present I used that command there and it worked (great mnemonic BTW) and I followed the instructions for installing boot-repair. I didn't run it though, just created the summary which is at [https://paste.ubuntu.com/p/RmsfVfFPqR/](https://paste.ubuntu.com/p/RmsfVfFPqR/)

Miles of info in there, I hope it's helpful.

---

### Post by oldfred on 2019-07-11
You have UEFI hardware.

You have Windows installed in UEFI boot mode.

It looks like you have Ubuntu installed in UEFI boot mode and booted Ubuntu live installer in UEFI boot mode, but at some point installed Ubuntu in BIOS boot mode as you have a copy of grub in gpt's protective MBR and a bios_grub partition which is required for BIOS boot with grub on gpt drives. Since fstab shows mount of /boot/efi, it looks like currently in UEFI boot mode.

Not sure if BIOS boot would work, but evenually UEFI & BIOS versions of grub get out of sync and then you have issues. You should only be booting in UEFI boot mode for all installs and always for live installer.

Windows will turn fast start up back on with updates. 
Boot-Repair says this:
 Windows not detected by os-prober on sda3. 
      
 Fast Start up off (always on hibernation), note that Windows turns this back on with updates
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

You should be able to directly boot Windows from UEFI boot menu, and then turn fast start up off, so then you can boot Windows from grub menu.

Looks like your model can be anything from Celeron to i7 Intel chip based.
Post this:
       
  grep -E 'model|stepping' /proc/cpuinfo | sort -u

---

### Post by MibunoOokami on 2019-07-11
> **oldfred said:**
> You have UEFI hardware.  You have Windows installed in UEFI boot mode.  It looks like you have Ubuntu installed in UEFI boot mode and booted Ubuntu live installer in UEFI boot mode, but at some point installed Ubuntu in BIOS boot mode as you have a copy of grub in gpt's protective MBR and a bios_grub partition which is required for BIOS boot with grub on gpt drives. Since fstab shows mount of /boot/efi, it looks like currently in UEFI boot mode.  Not sure if BIOS boot would work, but evenually UEFI & BIOS versions of grub get out of sync and then you have issues. You should only be booting in UEFI boot mode for all installs and always for live installer.   This goes back to when I first installed 18.04, I eventually was able to get that to boot in BIOS mode because UEFI would only boot Windows. When it came to installing 19.04 I had completely forgot the the process of getting it to boot via BIOS mode, however, with the exception of yesterday&#8217;s reboot failure, it has been working fine.   I&#8217;ll most certainly look at fixing this, probably with another clean install, from what I understand 19.04 support will stop in January which means either going back to 18.04 LTS, or 19.10.  > **oldfred said:**
>  Windows will turn fast start up back on with updates.  Boot-Repair says this:  Windows not detected by os-prober on sda3.         You should be able to directly boot Windows from UEFI boot menu, and then turn fast start up off, so then you can boot Windows from grub menu.  Looks like your model can be anything from Celeron to i7 Intel chip based. Post this:           grep -E 'model|stepping' /proc/cpuinfo | sort -u   On the odd occasion that I use Windows, I don&#8217;t allow networking or updates, so this might not be an issue. In fact, I had completely forgotten I still had Windows until installing 19.04 and decided to leave it there &#8220;just in case&#8221;.  Grep output ```
$ grep -E 'model|stepping' /proc/cpuinfo | sort -u model        : 112 
model name    : AMD A6-9220 RADEON R4, 5 COMPUTE CORES 2C+3G 
stepping    : 0
```

---

### Post by oldfred on 2019-07-11
When I looked on Internet, your model only mentioned Intel.
But you have AMD, which then may have some different issues. 

Other than general issues, I have not kept track of AMD vs Intel issues for most systems.
Not sure then what may be best to review.

---

