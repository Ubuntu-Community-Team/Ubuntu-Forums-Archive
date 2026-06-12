---
title: "boot broken after re-installing Ubuntu 16.04"
date: 2018-06-20
forum: General Help
---

### Post by Elliot_Findley on 2018-06-20
I have an Acer Aspire E 15 laptop. Until yesterday I had Windows 10 installed alongside Ubuntu. Since I never use Windows any more I decided to remove it by reinstalling Ubuntu 16.04 from a live USB. After doing so I received the following when trying to boot: 

Default Boot Device Missing or Boot Failed. 

I've tried boot-repair twice, but both times a failure. The pastebin can be found here: 
http://paste.ubuntu.com/p/8HjnSt66Nd/

On the plus-side, my Windows partition seems to have been removed successfully! 

Please help!!

---

### Post by yancek on 2018-06-20
An Acer requires you to set "trust" for any operating system that did not come pre-installed.  Check the boot screen for an option to enter the BIOS Setup.  I don't use Acer so you will have to check the manual you got with the computer or do an online search for it.  You should actually be able to find that info using the search option here at the forums as there have been numerous posts on the subject.

---

### Post by oldfred on 2018-06-21
If you have not updated UEFI from Acer, you should also do that.

       Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)
[https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[https://ubuntuforums.org/showthread.php?t=2342323](https://ubuntuforums.org/showthread.php?t=2342323)
Acer Cloudbook shows screen for selecting trust
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392](http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392)
 InsydeH20 setup utility
Acer Very latest UEFI/BIOS works, downgrade not required:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141)

---

