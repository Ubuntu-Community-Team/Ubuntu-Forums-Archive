---
title: "32-bit vs 64-bit Ubuntu 13.10 trying to install 64-bit on a Lenovo Thinkcenter M92 pc"
date: 2013-10-25
forum: General Help
---

### Post by Vannyi on 2013-10-25
I've been trying to install 64-bit Ubuntu 13.10 on a Lenovo ThinkCentre M92 pc and it just will not work.  I'm getting the error message error 1962 no operating system found.  I've Googled this issue and believe it has something to do with UEFI and I have tried all the fixes that I can find online, but still, no luck.

I'm at a point where I may return to Windows, heaven forbid.

As a last ditch effort, would anyone know, can you load 32-bit Ubuntu 13.10 on a M92?  I'm just wondering what determines whether you install 32-bit or 64-bit?  I went with 64-bit only because this is a very new machine and I suspect the chipset would support it, but is it backward compatible?

Thank you

---

### Post by grahammechanical on 2013-10-25
A 64bit OS will run on a 64bit CPU but not on a 32bit CPU. A 32bit OS will run on both 32bit and 64bit CPU. But the issues for you is will 32bit Ubuntu install on hardware that was shipped with Windows 8 installed? Machines with windows 8 pre-installed come with secure boot enabled and with a UEFI boot system. You will need 64bit Ubuntu for that.

> 
[LIST]
[*=left][FONT=inherit]Use a 64bit disk of Ubuntu ([Ubuntu32bit cannot be easily installed in UEFI mode]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1025555"))[/FONT]
[/LIST]

> [COLOR=#333333][FONT=Ubuntu]"[/FONT][/COLOR][Secure Boot]("http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface#Secure_boot")[COLOR=#333333][FONT=Ubuntu]" is a new UEFI feature that appeared in 2012, with Windows8 preinstalled computers. [/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]All current Ubuntu 64bit ([/FONT][/COLOR][not 32bit]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1025555")[COLOR=#333333][FONT=Ubuntu]) versions now support this feature, [/FONT][/COLOR]

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Regards.

---

### Post by BBQdave on 2013-10-25
> **Vannyi said:**
> I've been trying to install 64-bit Ubuntu 13.10 on a Lenovo ThinkCentre M92 pc and it just will not work.

That hardware is 64-bit, so you would want a 64-bit OS.

If your system came with Windows 7, it should not have Secure Boot obstacle. If you are install along side Windows, it may not be showing Ubuntu at start up - defaulting to Windows. If your installing Ubuntu as the only system, it should boot up. If your system came with Windows 8, you would need to disable Secure Boot - to install and boot Ubuntu.

---

### Post by Vannyi on 2013-10-25
I'm really lost on what to do here.  I did stumble across this link that you provided and I did switch the Boot Mode from auto to UEFI and I also disabled quick boot.  I did not see an option in my bios for Intel Smart Response Technology (SRT), but even after making these changes and resinstalling 64-bit Ubuntu, I still get the Error 1962 no operating system found.

I know it's not the hard drive because when I go to reinstall it, it does see the old install and I also tried installing on another Lenovo device, same issue.

Also, just to note, I am not trying to dual boot, just would like to use Ubuntu, no Windows.

One more thing to point out, I've used a scrub CD to wipe the drive clean prior to installing Ubuntu

---

### Post by I.Bun.Tu on 2013-10-25
Have you disabled "Secure boot"? It's a security feature in the UEFI shipped with Windows 8 laptops. I had a Windows 8 laptop and had to disable this in the UEFI (former BIOS) to get Ubuntu to install.

 I may have also had to select the dvd drive to boot manually from the UEFI (this is usually on the last page with the options to exit with/without changing settings; but you need to exit and save after turning off Secure Boot first). This may not be necessary but you definitely need to disable Secure boot. Not quick boot. The secure boot option is also likely on the last page.

---

### Post by Vannyi on 2013-10-25
I got it to work and really, just trying random settings that seemed to make sense

Here's what I did

Quick Boot/Fast Boot =>disable
Boot Mode => Legacy
Serial ATA => IDE

---

### Post by Vannyi on 2013-10-29
> **grahammechanical said:**
> A 64bit OS will run on a 64bit CPU but not on a 32bit CPU. A 32bit OS will run on both 32bit and 64bit CPU.
Regards.

More for my own understanding, but if you have a 32-bit OS on a 64-bit machine, does it slow down the PC in any way or would you get at least the same performance as a 32-bit OS on a 32-bit machine?

---

### Post by oldfred on 2013-10-29
You do not get the same performance.

Did you end up installing Ubuntu in CSM/BIOS/Legacy mode or UEFI mode?

       32-bit vs. 64-bit Ubuntu 13.04 Linux Performance with only 1GB of RAM & most tests better with 64bit Mac Mini
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_x86_1304&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_x86_1304&num=1)
Ubuntu 12.10: 32-bit vs. 64-bit Linux Performance
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_1210_3264&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_1210_3264&num=1)
Assuming your hardware is x86_64 capable (basically any modern Intel/AMD CPU) and have at least 2GB of RAM, you really should be running the 64-bit version.
Essentially says if you can use the 64bit kernel you should.April 2011
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_natty_pae64&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_natty_pae64&num=1)
[https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit)
Ubuntu 32-bit, 32-bit PAE, 64-bit Kernel Benchmarks Dec 2009
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1)
Linus does not like PAE or 32 bit.
[http://cl4ssic4l.wordpress.com/2011/05/24/linus-torvalds-about-pae/](http://cl4ssic4l.wordpress.com/2011/05/24/linus-torvalds-about-pae/)

---

