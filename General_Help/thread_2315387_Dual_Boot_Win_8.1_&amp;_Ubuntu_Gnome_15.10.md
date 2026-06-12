---
title: "Dual Boot Win 8.1 &amp; Ubuntu Gnome 15.10"
date: 2016-02-28
forum: General Help
---

### Post by Mateusz_ on 2016-02-28
Good Afternoon All, 

I just installed Ubuntu for the first time and it looks amazing. 

I wanted to install it alongside of my Windows 8.1 to give it a go to begin with and see if I like it. 

I followed instructions on YouTube and online and managed to install the OS without any major problems. However I can't seem to be able to boot back to Windows now;/ 

I installed the software on one of my partitions on my second internal HDD. I followed instructions and divided that 350GB partition into a smaller one etc. 

However now I am able to boot straight into my Ubuntu, and when trying to change the HDD to SSD where my Win 8.1 was it is still loading up Ubuntu. 

How do I find out if I'm doing something wrong, or if I just screw up;/ and more importantly if I did, can I recover the files somehow? 

Many Thanks 

Mateusz

---

### Post by grahammechanical on 2016-02-28
When you installed Ubuntu did you install it in EFI mode?

If Windows is installed in EFI mode, and from Windows 8 upwards it usually is, we must install Ubuntu in EFI mode.


[URL="https://help.ubuntu.com/community/UEFI"]https://help.ubuntu.com/community/UEFI

[/URL]You might need the the services of Boot Repair. We install boor repair when running a Ubuntu live session. We select Create BootInfo Summary. and boot repair will provide a URL to where the BootInfo summary is stored online. Post the URL in this thread. Then we can see the situation as Boot Repair sees it.

Boot repair will suggest a repair option. You might want to wait until some of us have given you some advice before you accept the default repair option.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Regards

---

