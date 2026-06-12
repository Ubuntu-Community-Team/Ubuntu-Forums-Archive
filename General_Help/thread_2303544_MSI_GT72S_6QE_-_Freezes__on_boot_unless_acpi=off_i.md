---
title: "MSI GT72S 6QE - Freezes  on boot unless acpi=off is used"
date: 2015-11-19
forum: General Help
---

### Post by fabbari on 2015-11-19
Update: 01/16/2016

If you have this beast of laptop you will notice that the boot process will freeze almost immediately.

There is a temporary fix for this and it involves changing the kernel boot parameters - I also recommend updating your BIOS if it's a version before the E1782IMS.112 - by downloading it from the MSI web site: [http://www.msi.com/product/notebook/support/GT72S-6QE-Dominator-Pro-G.html#down-bios](http://www.msi.com/product/notebook/support/GT72S-6QE-Dominator-Pro-G.html#down-bios).

The freeze is a known bug in the Linux Kernel - see [https://bugzilla.kernel.org/show_bug.cgi?id=109081](https://bugzilla.kernel.org/show_bug.cgi?id=109081).

After you have installed the new BIOS -- not mandatory but recommended -- you have to change your boot params - see [https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) to include:

[FONT=courier new]intel_idle.max_cstate=7
[/FONT]
So your [COLOR=#333333][FONT=monospace]GRUB_CMDLINE_LINUX_DEFAULT[/FONT][/COLOR] should now look something like this:

[FONT=courier new]GRUB_CMDLINE_LINUX_DEFAULT="intel_idle.max_cstate=7"
[/FONT]
Run a

[FONT=courier new]sudo update-grub[/FONT]

and you should be good to go.

If you are installing Ubuntu for the first time, you can add the parameter to the boot line of the installer.

  Fabio

---

### Post by michal.gregor on 2015-12-03
I would add that the same can be achieved using the following boot parameter:

 intel_idle.max_cstate=0

The advantages are obvious &#8211; no need for a BIOS update and C States will still work on Windows.

---

### Post by fabbari on 2015-12-15
Thank you Michal! I have no Windows on the machine -- so I didn't think about that! :)

  Fabio

---

