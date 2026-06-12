---
title: "No Video Mode Selected Boot Screen in 12.04.2 LTS RTW."
date: 2013-02-16
forum: General Help
---

### Post by kevpan815 on 2013-02-16
i am getting a "No Video Mode Selected" Boot Screen Error Message in AMD 64 Ubuntu 12.04.2 Long Term Support Release To Web on my 2010 Dell Inspiron Zino 400 HD each and every time 12.04.2 Boots Up. The computer has both an AMD Dual Core Processor (Not Sure which one however) and a ATI Radeon 3200 HD Graphics Card). I had previously reported this in the Ubuntu + 1 Sub Forum during the Pre-Release Testing, but the issue never got fixed. The computer only stays on that Error message for a couple seconds and then finishes booting normally, so it's NOT really a big issue. I was just curious if anyone else has had the issue, and/or if the issue has been fixed since the AMD [64 20130214]("tel:64 20130214") Alternate CD Nightly Build (which is the last Build that I tested BUT it eventually became AMD 64 12.04.2 LTS RTW as far as I know). Thanks in Advance.

Correction: it says No Video Mode Activated, NOT No Video Mode Selected, my mistake.

---

### Post by schragge on 2013-02-16
Does that error message also list supported video modes? Something like
```

 Video/Mode info:
  Video output not enabled
 Current video mode:
  No video mode selected yet
 Supported video mode(s):
  'VGA'
  'SVGA'
  'XGA'
  'SXGA'
 Parameters:
           cdepth = 16
             mode = <NULL>
           enable = <NULL>

```

---

### Post by kevpan815 on 2013-03-02
No, it only says No Video Mode Selected. I am sorry for not getting back to you sooner but I have been very busy for the last 2 weeks Beta Testing Avast 8.0 for Windows. I have not tried any of the Post 12.04.2 Nightly Builds yet to see if my issue is fixed or not and today I am actually experiencing a slower than normal download from the cdimage.ubuntu.com Download Server so that will not be possible at the moment. The download speed is working just fine at releases.ubuntu.com however so I will try re-downloading 12.04.2 LTS RTW and then do a sudo apt-get update and sudo apt-get upgrade as soon as possible.

---

### Post by fantab on 2013-03-02
How did you install your Graphic Driver for ATI Radeon 3200 HD Graphics Card? From 'Additionl Drivers'? if yes, then revome/uninstall it and reboot.

---

### Post by dcstar on 2013-03-03
> **kevpan815 said:**
> No, it only says No Video Mode Selected. I am sorry for not getting back to you sooner but I have been very busy for the last 2 weeks Beta Testing Avast 8.0 for Windows. I have not tried any of the Post 12.04.2 Nightly Builds yet to see if my issue is fixed or not and today I am actually experiencing a slower than normal download from the cdimage.ubuntu.com Download Server so that will not be possible at the moment. The download speed is working just fine at releases.ubuntu.com however so I will try re-downloading 12.04.2 LTS RTW and then do a sudo apt-get update and sudo apt-get upgrade as soon as possible.

Any 12.04 release is just the same as a running 12.04 release that gets updates. 12.04.2 is just the original 12.04 release with all the security updates installed into it.

You are wasting your time continually downloading builds for already released versions.

---

### Post by kevpan815 on 2013-03-03
It's actually the the Integrated Driver in the CD that I am using. Also I do need to correct myself that the message is actually No Video Mode Activated, NOT No Video Mode Selected, and it affects BOTH of my 2010 Dell Systems. The 2013 system that I have in my Signature does NOT arrive till Monday and I am a little concerned about testing 12.04.2 on it anyways as it is a Windows 8 System with UEFI Firmware Installed by Default so I do NOT plan to install Ubuntu on it at this time.

---

### Post by kevpan815 on 2013-03-03
I should also note that my 2010 Dell Inspiron 1012 Mini Net Book has an Intel Graphics Media Accelerator 3500 Graphics Card, and yet the problem occurs on that system as well.

---

### Post by bogan on 2013-03-03
Hi!, **dcstar**,

You Posted:> Any 12.04 release is just the same as a running 12.04 release that gets  updates. 12.04.2 is just the original 12.04 release with all the  security updates installed into it.This is not strictly true of 12.04.2.xx, which is a special case.

A pre 12.04.2 release with all available updates installed, calls itself 12.04.2 in lsb-release, but 'uname -r' shows it is still running the 3.2.xx kernal, though it includes a few 'lts-quanta' files, essential to allow upgrading to the 3.5.xx kernal..

Whereas a clean install of the 12.04.2 release runs the 3.5.xx lts-quantal kernal and includes a lot of backports and 'lts-quantal' files.

Chao!, **bogan**.

---

