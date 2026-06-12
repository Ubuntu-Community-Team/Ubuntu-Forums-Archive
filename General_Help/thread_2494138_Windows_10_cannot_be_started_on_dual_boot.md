---
title: "Windows 10 cannot be started on dual boot"
date: 2024-01-06
forum: General Help
---

### Post by vincentmichaud on 2024-01-06
Good evening,
I can't boot tonight on windows 10, 2nd OS of my dualboot configuration.
When I select this entry in Grub, I get this message
```
 
error: file /EFI/Microsoft/Boot/bootmgfw.efi not available.
```

I've tried refreshing Grub, which detects the Windows 10 entry, and then launched Grub-repair, without success.
Note: booting is done in EFI mode.
Here's the boot repair result
then I ran boot-info again
configuration: desktop Ubuntu 22.04.3 LTS/ Linux 6.2.0-39-generic
I've already created a thread on the[ Ubuntu forum francophone]("https://forum.ubuntu-fr.org/viewtopic.php?id=2083022")

---

### Post by yancek on 2024-01-06
Have you been successfully booting windows10 from Grub?  Were there any changes and if so, what were they?
Can you mount the /boot/efi/EFI partition and navigate there and verify that the specified windows file exists?  It should be in a directory named Microsoft on the EFI partition.  While you are viewing the EFI partition contents, check to see if there is an ubuntu directory with efi files in it.
Are windows and Ubuntu on the same physical drive?

If you have run boot repair, you neglected to post a link to the result which you should have seen when it finished, after running with the option to Create BootInfo Summary.  That would provide valuable and useful information for someone to help you.

---

### Post by oldfred on 2024-01-06
Did a Windows update turn on fast startup or hibernation? Then grub cannot boot Windows.
Can you boot Windows directly from UEFI boot menu?

You also have two entries in fstab, but one does not look like the UUID is there.
Better to use labels and mount points that have some meaning like data, media, or whatever rather than UUID which is difficult to remember.

---

