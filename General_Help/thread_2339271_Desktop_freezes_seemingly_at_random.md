---
title: "Desktop freezes seemingly at random"
date: 2016-10-06
forum: General Help
---

### Post by Zeikcied on 2016-10-06
My mom has had this computer for a little over a year now.  [http://www.newegg.com/Product/Product.aspx?Item=9SIA6R43BK8493](http://www.newegg.com/Product/Product.aspx?Item=9SIA6R43BK8493)  (Newegg link provided for the hardware specs.)

I installed the previous Kubuntu LTS release, and other than some graphics issues, things have worked well enough.  In the last month or so, however, she's been complaining that the system freezes, and it seems to be random.  I upgraded her to the current LTS (16.04) hoping that would solve the problem, but it didn't.  I followed some steps online to get her on the 4.7.4 kernel, and that didn't help, either.

It's happened at least twice when using LibreOffice, but she says it's also happened when browsing the internet in Firefox.  I don't know of any pattern to it.  And when I say it freezes, I mean the mouse and keyboard go dead, and the only way out is to force a shutdown.

Is this a kernel bug?  A graphics bug?  An issue with under-powered hardware?  Should I switch her to Xubuntu or Lubuntu?  Any help would be greatly appreciated.

---

### Post by colmax on 2016-10-06
Seems that system uses on chip graphics with no dedicated card
I'd still be inclined to check if xserver is being used
settings>software&updates>additional drivers
Cheers

---

### Post by Zeikcied on 2016-10-06
I went to System Settings -> Additional Drivers, and the only thing there was an unchecked box next to something about intel-microcode.  So I checked that, applied other updates, removed the 4.7.4 kernel (just in case), and rebooted.  Hopefully that helps.

Thanks. :)

---

### Post by Bucky Ball on 2016-10-07
> **Zeikcied said:**
> ... removed the 4.7.4 kernel ...

Good. Just stick with the kernel that is default for that release. This was working on an *older* kernel. Upgrading to a newer one that is not for your release is only going to find new issues rather than solved much as this is not a brand new, released yesterday, off the shelf machine with all new hardware components.

I'm thinking hardware if this has just started happening 'out of the blue' and is consistent across Ubuntu releases. Do you have Win installed on it and does that also freeze??? 

16.04 currently = 4.4.0-38-generic

You were using a kernel that is probably intended for 16.10, not released yet and still bug crushing and troubleshooting pre-release.

Might be obvious, but have you updated/upgraded the machine since you installed 16.04?

```
sudo apt update
sudo apt full-upgrade
```

That will get 16.04 fully up to date. I have a mother-in-law that never updates her machine, much to my distress when I sit down at it once every six months to see that she is kernels behind the current one and everything is woefully out of date ...

---

### Post by HermanAB on 2016-10-07
Well, did you rule out a hardware problem?

You can boot off an install CD and see if it ever fails.  If it does, then it is likely a PSU issue.

---

### Post by QLee on 2016-10-07
It likely is the " Bay Trail" hardware problem.  Has been around quite a while.

Please see:

Kernel Bugs
[https://bugzilla.kernel.org/show_bug.cgi?id=109051](https://bugzilla.kernel.org/show_bug.cgi?id=109051)

Launchpad Bugs
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1531865](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1531865)

Ubuntu Thread (or any of the numerous other threads)
[https://ubuntuforums.org/showthread.php?t=2314964](https://ubuntuforums.org/showthread.php?t=2314964)

When you have read about it and the suggested fix, you can test it by pushing the E key when the GRUB menu comes up and navigating to the line with "quiet splash", amending it with the suggested command line option and then following the directions at the bottom of the GRUB screen to boot with that new command line option. That will let you test it for that bootup. If no more crashes, you can add it to the GRUB menu.

---

