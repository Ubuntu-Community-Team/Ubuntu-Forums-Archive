---
title: "Custom Kernel"
date: 2007-03-11
forum: General Help
---

### Post by quark_77 on 2007-03-11
Hi All,

I have downloaded the latest Kernel (2.6.20.2) from kernel.org and following the Master Kernel Thread [http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158) have build various versions of the kernel (2.6.20, 2.6.20.1 and 2.6.20.2). I can follow the tutorial just fine, the build succeeds, however, booting any of the above kernels is impossible. The best scenario with 2.6.20.2 is this:

[LIST]
[*]Kernel spits out: Modprobe: FATAL: unable to load /lib/modules/2.6.20.2-custom1/mods.dep
[*]Kernel freezes later on at: Waiting for root filesystem
[/LIST]

I am running Linux on an IBM Thinkpad R60. I have SCSI disks (sdaX) and Core2Duo... does anybody know the ideal configuration for the kernel to get all this working / stop these errors causing the kernel to choke? Will the root=/dev/sda11 (my root drive) switch solve the problem??

Thanks in advance for your help, I'm very new to kernel building and can't get it to work... yet!

Quark_77

---

### Post by Bachstelze on 2007-03-11
Did you create an initrd with the correct modules ?

---

### Post by quark_77 on 2007-03-11
Hi,

I used the following:

> make-kpkg -initrd --revision=0.1 kernel_image kernel_headers modules_image

Which automatically generates an initrd. To clarify where I have got with the 2.6.20.2 source, root fs is not loaded, I am dropped to the shell (initramfs) and the usb device takes ages to evaluate.

Any ideas what switches need to be turned off so that my kernel can pick up /dev/sda11 (root)?

Thanks in advance!

---

### Post by widdma on 2007-03-11
I had this problem on the 2.17.20 upgrade and found that my previous sda device was now mounted as hda.

try editing you boot options to root=/dev/hda1 (or some other partition number)

tip: if you boot up without the quiet option and watch carefully you will see the kernel mount your drives by name, that was how I noticed

---

### Post by quark_77 on 2007-03-12
Hi widdma,

Thanks for the advice. hda didn't show up at all, my drives have remained as SCSI however the letters have swapped my cdrom is now /dev/sda and my hd /dev/sdb hence changing the root let me build the kernel...

Two more questions now I have seen a working home-made kernel:
[LIST]
[*]Swapping the above around? Is it possible to have my hard disk back on sda? I've put the SCSI drivers as modules, not statically linked, I'm hoping this will work...?
[*]My wireless adapter is no longer eth1 - how do I set it up so it detects my wireless adapter as eth1 or is this not possible?
[/LIST]
Also got to look up how to build in fglrx as you guessed it I have an ATI graphics card and the graphics are painful without the driver...!

Thanks for your help!

Quark_77

---

### Post by quark_77 on 2007-03-12
OK, more research done and...

tg3 from broadcom for my ethernet adapter is compiled in. Additionally I need ipw3945 and fglrx. If I understand what I have read correctly I can build the fglrx kernel module when I start up the kernel.

I've downloaded ipw3945 for my intel pro/wireless - how do I build support for this into the kernel tree so I can see it in xconfig?? Or should I build this as a module too??

Thanks again for your help... I'm asking these questions before I rebuild the kernel as it takes ages!

Thanks again for your help!!

---

### Post by quark_77 on 2007-03-15
As the original problem now resides with patches and other peripheral issues I shall post my further questions in a new thread.

Thanks for your help.

---

