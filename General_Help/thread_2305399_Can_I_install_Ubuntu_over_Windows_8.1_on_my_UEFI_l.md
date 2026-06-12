---
title: "Can I install Ubuntu over Windows 8.1 on my UEFI laptop?"
date: 2015-12-05
forum: General Help
---

### Post by t0p on 2015-12-05
I've got a HP15 laptop, 15-g261sa, with Windows 8.1 installed.  Can I install Ubuntu onto it, replacing the Windows 8.1?  I was originally planning a dual-boot, but after some messing round I can't get the dual-boot to work (no grub menu) and as I don't need the Windows I decided straight Ubuntu will do.  Will the UEFI stuff mess with me?  I have secure boot disabled in the "BIOS" menu.

I want to install Ubuntu 14.04.3.

---

### Post by cariboo on 2015-12-05
Most Live CD's boot into UEFI mode, so really you just need to do a normal install.

---

### Post by t0p on 2015-12-05
> **cariboo said:**
> Most Live CD's boot into UEFI mode, so really you just need to do a normal install.

OK I'm gonna do that, and if I brick my laptop I'm gonna blame YOU!!! (just kidding ;) )

---

### Post by t0p on 2015-12-07
I'm bringing this back up, as I really don't want to brick my laptop.

Has anyone reading this actually done what I want to do: to install Ubuntu onto a Windows 8.1 UEFI computer so Windows is gone and Ubuntu owns the whole machine and boots nicely when powered on?

---

### Post by yancek on 2015-12-07
If your computer came with windows 8.1 pre-installed, it is almost certainly UEFI/GPT so you will need to install Ubuntu the same.  If it boots in UEFI mode as indicated above, you should be good to go.  You might try a dual-boot to see how you like it as you can always format the windows partitions later for use by Ubuntu.  If you are not familiar with UEFI, you might read the Ubuntu documentation at the site below regarding dual-booting Ubuntu/windows UEFI.

 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by t0p on 2015-12-07
I tried a dual-install, a couple of times, and couldn't get Ubuntu to boot... no Grub "menu" screen, it just boots straight into Windows.  Thus my wariness:  I don't want to eradicate Windows just to find I can't boot anything else on the machine (UEFI is a beast, I never had problems like this before, I blame the parents...).

---

### Post by westie457 on 2015-12-07
You will need to dive into the system settings (bios) pages using either the manufactures key combinations - usually the Esc key for a HP machine. Check the documentation.

In the page for security you probably have to set a Supervisor password to enable more options and tell the machine to trust a different Boot-loader.

Not owning a HP box I cannot be more specific about this. It does no harm to look and any changes made in these pages do not take effect until they are saved. It is better to do one change Save and Exit (reboot) than do several.

The first page you see will look similar to this pic.

---

