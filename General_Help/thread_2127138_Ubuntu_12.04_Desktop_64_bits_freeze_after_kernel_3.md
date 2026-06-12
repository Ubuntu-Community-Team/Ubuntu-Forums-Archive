---
title: "Ubuntu 12.04 Desktop 64 bits freeze after kernel 3.2.0-39 update"
date: 2013-03-19
forum: General Help
---

### Post by jramirezpita on 2013-03-19
Hi, (this is the first time I participate in this forum)

I've just updated my desktop, now it has the new kernel 3.2.0-39. After rebooting I run Google Chrome and the whole system get freezed. I can't do anything but push the reset buttom in the computer box (no key combination works! neither text consoles with ALT + F1, ...). I've tried it again getting the same result.

So I've rebooted the system with the old kernel 3.2.0-38 and everything is fine. I assume there is an issue with this kernel version. 

Any help?

Thanks.

---

### Post by Ximaceo on 2013-03-19
Hello jramirezpita,

I had problems too, I found this:

[http://news.softpedia.com/news/New-Kernel-Vulnerabilities-Affect-Ubuntu-12-10-and-12-04-LTS-338323.shtml](http://news.softpedia.com/news/New-Kernel-Vulnerabilities-Affect-Ubuntu-12-10-and-12-04-LTS-338323.shtml)

> The security flaws can be fixed if you upgrade  your system(s) to the linux-image-3.2.0-39 (3.2.0-39.62) package(s) for  Ubuntu 12.04 LTS
For detailed instructions on how to upgrade your system, see the following link: [https://wiki.ubuntu.com/Security/Upgrades](https://wiki.ubuntu.com/Security/Upgrades). Don't forget to reboot your computer after the upgrade!

edit: type "uname -a" on Terminal to know the kernel version.

---

### Post by davidskytte on 2013-03-19
I have the exact same problem. However, i can't reboot in to an older kernel version (for some strange reason i don't have grub). I'd there any way to go back to a previous version using the terminal?

---

### Post by Ximaceo on 2013-03-19
Has you tried upgrate the system?

> $ sudo apt-get update
$ sudo apt-get dist-upgrade

---

### Post by jramirezpita on 2013-03-19
Yes, I did it but it doesn't resolve the problem.

---

### Post by Dave_L on 2013-03-19
As of a couple of days ago, for Ubuntu desktop amd64 12.04, wasn't the latest kernel 3.5.0-25?

---

### Post by howefield on 2013-03-19
> **Dave_L said:**
> As of a couple of days ago, for Ubuntu desktop amd64 12.04, wasn't the latest kernel 3.5.0-25?

Only for fresh installs of 12.04.2 or if OP manually upgrades the kernel packages.

2 "strands" of supported kernel in 12.04, the original 3.2.0-x series and 3.5.0-x included with the hardware enablement packages.

---

### Post by Dave_L on 2013-03-19
> **howefield said:**
> Only for fresh installs of 12.04.2 or if OP manually upgrades the kernel packages.

2 "strands" of supported kernel in 12.04, the original 3.2.0-x series and 3.5.0-x included with the hardware enablement packages.

Thanks for the clarification.  (I did a fresh install of 12.04.2 recently, which had kernel 3.5.0-23, which was then upgraded to 3.5.0-25.)

---

### Post by Impavidus on 2013-03-19
> **davidskytte said:**
> I have the exact same problem. However, i can't reboot in to an older kernel version (for some strange reason i don't have grub). I'd there any way to go back to a previous version using the terminal?Can't you get the grub menu by pushing shift as soon as the BIOS screen clears?

> **Dave_L said:**
> As of a couple of days ago, for Ubuntu desktop amd64 12.04, wasn't the latest kernel 3.5.0-25?3.5 is available in the repos, but who installed 12.04 more than a few months ago still has 3.2, unless (s)he upgraded manually.

---

### Post by jcanipe on 2013-03-19
I encountered the same problem last night when I applied the latest maintenance from Update Manager. I also put a thread under Desktop: [Applied maintenance to Ubuntu 12.04; after restart my desktop is not responding]("http://ubuntuforums.org/showthread.php?t=2127155") I can telnet into the box, but that is about it. I, like you, am only running one OS; so no grub menu. I am going to try pressing Shift after BIOS.

---

### Post by jramirezpita on 2013-03-19
I've just installed kernel 3.8.3-030803-generic and it works by now. I followed this instructions [http://www.upubuntu.com/2013/03/installupgrade-to-linux-kernel-383-in.html](http://www.upubuntu.com/2013/03/installupgrade-to-linux-kernel-383-in.html)

I don't know if it's going to be a good idea passing from 3.2.X to 3.8.x.

---

### Post by Rob__oo00T on 2013-03-19
> **jramirezpita said:**
> Hi, (this is the first time I participate in this forum)

I've just updated my desktop, now it has the new kernel 3.2.0-39. After rebooting I run Google Chrome and the whole system get freezed. I can't do anything but push the reset buttom in the computer box (no key combination works! neither text consoles with ALT + F1, ...). I've tried it again getting the same result.

So I've rebooted the system with the old kernel 3.2.0-38 and everything is fine. I assume there is an issue with this kernel version. 

Any help?

Thanks.
Same issue but using thunderbird.. after update and restart, system freezed.

---

### Post by gpalarea on 2013-03-20
I'm having the freeze too.  After yesterday's update to 3.2.0-39 my system freezes constantly.  12.04 64b

---

### Post by fvu on 2013-03-21
Same problem for 32-bits kernel 3.2.0-39 upgrade.  System hangs, and only mouse pointer can be moved.  Can't even change to terminal (ALT-F1).  Also noticing minor screen refresh glitches where small rectangles on the screen don't refresh properly.  Related to Intel graphics driver (see also [http://ubuntuforums.org/showthread.php?t=2127155](http://ubuntuforums.org/showthread.php?t=2127155) )?

Reverted back to kernel-3.2.0-38 by setting GRUB_DEFAULT=2 (sudo vi /etc/default/grub) and doing a sudo update-grub.

---

### Post by BolinMDT on 2013-04-03
Is there a permanent fix to this yet?

I'm still pressing SHIFT after the BIOS screen and using the previous kernel. I've got the latest updates but kernel 3.2.0-39 still freezes up.

This is a major problem (especially as I'm not a computer person!), surely it would have been attended to by now? I just can't find a permanent solution.

---

### Post by BolinMDT on 2013-04-09
Ok, I have now downloaded the latest kernel, 3.2.0-40, but the problem remains - the system freezes shortly after logging in. So I am still having to access the grub menu and select kernel 3.2.0-38.

Could anybody please help me fix whatever is going wrong?

Regards, Bolin.

---

### Post by disc9 on 2013-04-10
This problem seems to be pretty prevalent, at least on Intel based machines. As 12.04 is the long term release I think they will push a new kernel release soon. In the meantime use the previous version.

---

### Post by disc9 on 2013-04-13
> **disc9 said:**
> This problem seems to be pretty prevalent, at least on Intel based machines. As 12.04 is the long term release I think they will push a new kernel release soon. In the meantime use the previous version.


Just crashed my machine again launching Virtualbox. Same hard freeze. And my other machine that uses the -40 Kernel crashed yesterday for the first time ever! At least it dumped an error to the screen--referenced Virtualbox even though it was not in use at the time. Been using Intel DQ77KB motherboards and they are rock solid. I used to be able to say that about Linux...

---

### Post by gnomie2000 on 2013-04-16
Same problem here. Also integrated intel video on 12.04 64 Bit. Since upgrade to 3.2.0.39 (also 3.2.0.40) reproducibly crashing under minor X activity. Yes, there should very, very many machines with this spec out there. Still... doesn't get fixed. I am running 3.2.0.38 just fine. But it took me a frustrating while to find out. Would this have been better, if I bought commercial support? I am using this machine for work after all.

---

### Post by vbalsys on 2013-05-02
Problem solved upgrading to 3.5.0-28-generic kernel (thanks to jcanipe from [http://ubuntuforums.org/showthread.php?t=2127155](http://ubuntuforums.org/showthread.php?t=2127155)).
 What I've actually done was:

 [FONT=courier new]$ sudo apt-get install linux-generic-lts-quantal[/FONT]

If you had your grub changed to stick with 3.2.0-38, you will have to revert change back to normal:
[FONT=courier new]
$ sudo vim /etc/default/grub[/FONT]

and after saving it:

[FONT=courier new]$ sudo update-grub[/FONT]

Restart and enjoy.

---

