---
title: "Samsung 900x install problems"
date: 2013-01-10
forum: General Help
---

### Post by conradin on 2013-01-10
Hi All, I am having the worst time with a Samsung 900x install of 12.04 Ubuntu. The bios seems finicky about the devices it recognizes, but I finally got a good boot from a brand new USB drive boot disk. The installation went through, claimed successfully completion, then reboot. on Reboot, I never once saw grub, or a Linux boot-loader. 

I was looking for other people having a tough time, but all I see is folks saying how well it works. 

It has windows 8 on the hard drive.... and Im just confused right now. Am I getting blocked or something? What is going wrong?

Im going to reburn my boot disk, and checksum the iso. What else might be going wrong? Ive never had this many problems installing linux before. :(

---

### Post by Muratturat on 2013-01-10
> **conradin said:**
> Hi All, I am having the worst time with a Samsung 900x install of 12.04 Ubuntu. The bios seems finicky about the devices it recognizes, but I finally got a good boot from a brand new USB drive boot disk. The installation went through, claimed successfully completion, then reboot. on Reboot, I never once saw grub, or a Linux boot-loader. 

I was looking for other people having a tough time, but all I see is folks saying how well it works. 

It has windows 8 on the hard drive.... and Im just confused right now. Am I getting blocked or something? What is going wrong?

Im going to reburn my boot disk, and checksum the iso. What else might be going wrong? Ive never had this many problems installing linux before. :(

You have to re-install grub or grub 2 and then you have to load it.

---

### Post by threeta on 2013-01-30
no problems with crunchbang waldorf.  The boot from usb can be a bit hit and miss.  

not working
right click, keyboard back light

boots in 12 seconds!!

---

### Post by conradin on 2013-02-05
The Bios was confusing me.
it says something like if you delete the cryptographic signatures, which happens when you disable secure-boot, the OS will may fail to boot.
However, disabling the secure UEFI boot was the only way I could get Linux to boot after installing it. The first time I opted to install /boot from the USB 1 time, retaining secure-boot.

After disabling UEFI secure-boot I installed Linux, but windows wouldn't boot. Then I found a post by slickymaster in this thread and all was well.
[http://ubuntuforums.org/showthread.php?t=2091032](http://ubuntuforums.org/showthread.php?t=2091032)

---

