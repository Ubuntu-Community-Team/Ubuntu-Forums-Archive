---
title: "Boot hang"
date: 2013-07-14
forum: General Help
---

### Post by onilink422 on 2013-07-14
I have a _Lenovo Z580 Laptop with 6gb Ram -- Intel Core i5-3210M CPU @ 2.50GHz × 4. _
*

The laptop hangs on boot unless I boot it without the battery in. Once it is all logged in and everything I can reinsert the battery no problem. It is Frustrating to have to take out the battery whenever I turn it on, sometimes I forget to shove it back inside and I decide to walk away. 

If you need any logs or outputs please feel free to request them. Thanks in advance.

---

### Post by oldfred on 2013-07-14
Some other threads with Lenovo's
Lenovo Z580 laptop
[http://ubuntuforums.org/showthread.php?t=2112271](http://ubuntuforums.org/showthread.php?t=2112271)
See post #29 on removing Battery to get it to reset &  boot Ubuntu.
[http://ubuntuforums.org/showthread.php?t=2117760](http://ubuntuforums.org/showthread.php?t=2117760)

 Lenovo IdeaCentre K410 Pentium 64-bit
[http://ubuntuforums.org/showthread.php?t=2129961](http://ubuntuforums.org/showthread.php?t=2129961)
> Discovered that on my Lenovo, if I press F12 repeatedly on startup, it takes me into a Boot Order menu. If I select Windows there, it boots into Windows. I also found that to get into BIOS at startup on my Lenovo tower, you press F1 rather than the F2 I'm used to on other computers.

      
 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Install with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by onilink422 on 2013-07-15
Yes, I am aware these posts exist and this is the reason I knew about the battery trick. However, none of these *older* posts directed me to a fix. I am on a 3.5 Kernel and I am wondering if there is a way around this at the moment. I am not about to hijack a thread. As far as I know, boot repair only reinstalls GRUB which is not the issue. The problem follows me across any distribution installed. Otherwise, things work perfectly.

---

### Post by oldfred on 2013-07-15
Did you see the next post in that thread that seems to have a work around, something with the ACPI. 
I might also try ACPI boot settings.

       acpi_osi=linux pci=noacpi
or just

 acpi_osi=Linux

This was an Asus, but may be similar with Intel & Intel graphics.

 Asus i3 with Intel graphics, 
"acpi_osi=Linux"
"video=1280x1024-24@75" or whatever native resolution is

 Add similarly to nomodeset on linux line in grub menu as you boot to test.
 How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
Info on other boot parameters
[http://www.kernel.org/doc/Documentation/kernel-parameters.txt](http://www.kernel.org/doc/Documentation/kernel-parameters.txt)

---

