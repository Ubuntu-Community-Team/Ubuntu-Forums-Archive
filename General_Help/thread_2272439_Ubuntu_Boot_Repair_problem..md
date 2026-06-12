---
title: "Ubuntu Boot Repair problem."
date: 2015-04-06
forum: General Help
---

### Post by valentin11 on 2015-04-06
Well as the title says Boot Repair tool failed to help me whit my out of range screen problem.
The URL is [http://paste.ubuntu.com/1754026/](http://paste.ubuntu.com/1754026/).
I was Windows user soo I am not familiar with Ubuntu.
I think all required information is here. Please help me.
Sorry for my English.

---

### Post by oldfred on 2015-04-06
Your pastebin is not working.

But Boot-Repair usually cannot fix video issues.
What brand/model system?
What video card/chip do you have?
Are you able to boot with nomodeset or the second grub menu item - recovery mode?

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

---

### Post by valentin11 on 2015-04-07
Well about the hardware it is a bit old. The video card is NvIdia gforce 9500 gt, the CPU is AMD Athlon 64 X2 Dual Core, motherboard Asrock n61p-s.
The new URL is [http://paste.ubuntu.com/10758408/](http://paste.ubuntu.com/10758408/) . I will try to get in grub to change something but for now ot is out of my screen range after BIOS.

UPDATE : I am able to enter grub but if I try to boot ubuntu I get signal out of range. I will try Boot-Repair one more time.
UPDATE : Well the same thing after grub. The new url is  [http://paste.ubuntu.com/10759914/](http://paste.ubuntu.com/10759914/)

---

### Post by valentin11 on 2015-04-07
I have decided to reinstall the system.
Please close this thread.

---

