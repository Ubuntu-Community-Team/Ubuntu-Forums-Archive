---
title: "Windows kicked Ubuntu out?"
date: 2017-02-05
forum: General Help
---

### Post by eduardoflsantos on 2017-02-05
Hi,

My father's desktop has a dual boot for Windows and Ubuntu. He only uses Ubuntu (I think it's **14.04)**

I used his computer today, and noticed there was a tone of regular updates to do (he pays no attention to it). So I clicked on the Update screen and Ubuntu download and installed a lot of stuff. Then it asked to reboot, which I did.

After the reboot, there was a screen with the Toshiba logo, and it was saying the disk had problems and needed to be checked. Then it said it was diagnosing and fixing problems (all of this without all my permission), and then rebooted.

Now it's launching Windows 8 directly. GRUB is gone, and I can't enter on Ubuntu.

Help, please? (when you think Windows can no longer bother you, this happens...)

Thank you.

---

### Post by oldfred on 2017-02-05
May be best to see details, you can run from Ubuntu live installer or any working install:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

With BIOS, an operating system did not change settings.
But with UEFI, the operating system can change boot priority.
Can you still boot Ubuntu entry using UEFI one time boot menu from f12?

You may just need to set Ubuntu as first in boot order again.

This will be part of above Summary report.
sudo efibootmgr -v

---

### Post by eduardoflsantos on 2017-02-05
> 
Can you still boot Ubuntu entry using UEFI one time boot menu from f12?

You may just need to set Ubuntu as first in boot order again.

I can change boot priority. But they share the same HDD, just use different partitions. The selected HDD is correct (and the only one).

---

### Post by oldfred on 2017-02-05
This it sounds like a BIOS/MBR install, and Windows updates installed its boot loader into MBR.
Use Boot-Repair or manual commands to reinstall grub2's boot loader to MBR.

But better to see report to confirm configuration.

---

### Post by eduardoflsantos on 2017-02-05
Hi,

Here is is
[http://paste2.org/HLLggk3M](http://paste2.org/HLLggk3M)

Thank you

---

### Post by eduardoflsantos on 2017-02-05
> **oldfred said:**
> May be best to see details, you can run from Ubuntu live installer or any working install:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)


Boot repair software worked.

Thank you oldfred!

---

### Post by oldfred on 2017-02-05
Is install Ubuntu or Mint?
You are using  a Mint disk to repair system, may work better if same version as install.

It is UEFI system.

And you do not have the direct UEFI entry to boot Windows which is unusual. 
Some boot the failsafe or hard drive entry which is /EFI/Boot/bootx64.efi.
And Boot-Repair usually copies /EFI/ubuntu/shimx64.efi to /EFI/Boot/bootx64.efi as many systems only boot "Windows Boot Manager" by description. So Ubuntu has to use fallback entry.

Can you boot ubuntu entry in UEFI from UEFI boot menu? It is 0005 and second boot option.
You first boot option is "UEFI Toshiba" or 0003.

run this to see details:
sudo efibootmgr -v

       New Windows entry - assumes default sda1  add -p 2 if sda2:
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\Microsoft\Boot\bootmgfw.efi" -d /dev/sda -p 2

      
 Change boot order with efibootmgr, some require all 4 hex char others 1 is ok. 
           
 sudo efibootmgr -o 0005,0003

Check again that order is correct:
sudo efibootmgr -v

See also
man efibootmgr

---

