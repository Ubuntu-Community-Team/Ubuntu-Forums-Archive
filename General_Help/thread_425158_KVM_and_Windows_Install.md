---
title: "KVM and Windows Install"
date: 2007-04-27
forum: General Help
---

### Post by ronald_stall on 2007-04-27
I am following the directions at [https://help.ubuntu.com/community/KVM](https://help.ubuntu.com/community/KVM) but get down to the the command:

```
kvm -no-acpi -m 384 -cdrom /dev/cdrom -boot d windows.img
```

The QEMU/KVM window pops up, Windows starts but then hangs at "Starting Windows"

Any ideas?

Thanks

---

### Post by Tomy on 2007-05-01
> **ronald_stall said:**
> I am following the directions at [https://help.ubuntu.com/community/KVM](https://help.ubuntu.com/community/KVM) but get down to the the command:

```
kvm -no-acpi -m 384 -cdrom /dev/cdrom -boot d windows.img
```The QEMU/KVM window pops up, Windows starts but then hangs at "Starting Windows"

Any ideas?

Thanks
Try adding the -no-kvm option to see if you can boot with qemu only.

If you can try this:
______________________________________________________________________
[http://kvm.qumranet.com/kvmwiki/Windows_ACPI_Workaround](http://kvm.qumranet.com/kvmwiki/Windows_ACPI_Workaround)
**Working around a slow Windows virtual machine due to ACPI**

 If your Windows installation is set to use ACPI (this is the default), kvm can be quite slow. This is due to Windows heavily using a register that has a very large virtualization penalty. 
Fortunately, there is a simple workaround available: disable ACPI support in Windows.  The procedure for doing this is:[LIST=1]
[*]Select "My Computer" with the right mouse button.
[*]Select "Properties".
[*]Choose the "Hardware" tab.
[*]Click the "Device Manager" button.
[*]Select the entry under "Computer" with the right mouse button.  If it says "Standard PC", then there's no need to do anything.
[*]Select "Properties"
[*]Click the "Update Driver" button.
[*]Choose "Not at this time" and clock "Next".
[*]Choose "Install from a list" and click "Next".
[*]Choose "Don't search" and click "Next".
[*]Click "Next".
[*]Choose "Standard PC" and click "Next".
[*]Continue clicking "Next" and reboot the virtual machine[/LIST]________________________________________________________________________

By changing winXP to "Standard PC" I was able to get kvm to boot.

---

### Post by jfaberna on 2007-05-07
I had a similar problem with the Install of WinXP under KVM. I found that when the WinXP install asked for you to hit F6 for additional drivers, you hit F5 instead. The install will give you the option to select Standard PC or other. Pick Standard PC and the install will continue.

Jim a

---

