---
title: "boot menu gone/boot-repair option 2 did not fix it"
date: 2021-08-30
forum: General Help
---

### Post by JamButty on 2021-08-30
I don't need Windows often, but when I do, I really do. Boot menu does not appear - boots directly into Ubuntu. I have been using dual boot for years with little problem. Other than an upgrade issue, I can't imagine what borked the boot menu as I have not been messing with the system in any way recently.
At first tried just ```
sudo update-grub
```
and got output that looked hopeful

```
fred@fred-Inspiron-3847:~$ sudo update-grub
[sudo] password for fred: 
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.11.0-27-generic
Found initrd image: /boot/initrd.img-5.11.0-27-generic
Found linux image: /boot/vmlinuz-5.11.0-25-generic
Found initrd image: /boot/initrd.img-5.11.0-25-generic
Found Windows Boot Manager on /dev/sda1@/EFI/Microsoft/Boot/bootmgfw.efi
Adding boot menu entry for UEFI Firmware Settings
done
```
but no change. Ran Boot-Repair via livedisk, but also no change.
Suggestions welcome.

Boot-Repair data is in [https://paste.ubuntu.com/p/YJxr669FVJ/](https://paste.ubuntu.com/p/YJxr669FVJ/)

---

### Post by oldfred on 2021-08-30
Boot-Repair fixes Linux boot issues, most often just reinstall of grub. It does not fix Windows issues.

Grub only boots working Windows.
And Windows updates often turn fast start up back on which sets hibernation flag preventing the Linux NTFS driver from properly seeing the NTFS partition(s).

Can you directly boot Windows from UEFI boot menu (not grub menu). 
And maybe f8 to get into repair mode? And turn off fast start up again or make other fixes?

Always best to also have Windows repair/recovery flash drive to make Windows repairs, if you cannot boot Windows.
Repair/backup/restore
[https://support.microsoft.com/en-us/windows/create-a-recovery-drive-abb4691b-5324-6d4a-8766-73fab304c246](https://support.microsoft.com/en-us/windows/create-a-recovery-drive-abb4691b-5324-6d4a-8766-73fab304c246)
 
[http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options](http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options)

---

### Post by tea for one on 2021-08-31
> **JamButty said:**
>  Boot menu does not appear - boots directly into Ubuntu.

When you power on the PC, try tapping ESC while the PC boots.
Does Grub appear?

---

### Post by JamButty on 2021-08-31
Tried repeatedly with ESC and F12 while booting but before initial Ubuntu splash appears. It does not get me into grub. It either hangs or the boot sequence commands are displayed until it completes boot into Ubuntu. Just now found reference of F2 for Dells to get into BIOS - maybe that will work. Trying now.

---

### Post by ajgreeny on 2021-08-31
I presume you mean that the grub menu is not appearing so let's see the output of [cat /etc/default/grub] to check there is nothing there causing this problem.

In a dual boot system the grub menu normally shows at every boot so something may have gone wrong there, or more likely, there is a problem in your Windows system which Ubuntu will not be able to fix; you may need to boot to a Windows Recovery DVD instead.

---

### Post by oldfred on 2021-08-31
If you have UEFI fast boot on, either originally or from an UEFI update reset, you often do not have time to press any keys.
Fast boot assumes no system changes, so UEFI does not rescan system for what hardware you have and does not then write that updated info onto drive for operating system. If making system changes best to have fast boot off in UEFI, different than Windows fast start up setting which also needs to be off.

You usually can get one normal boot when fast boot is on, with a full "cold" boot. Full power down including removing battery if laptop, and holding power switch for 10 sec or so with system unplugged, to drain all power. 
If that does not work, you have to either remove coin battery or jumper the reset pins on motherboard. But then that resets settings for UEFI and you immediately have to go into UEFI and redo all the settings you change. I keep a list as UEFI updates reset 6 or 7 settings on my motherboard, some required, some optional that I prefer.

---

### Post by JamButty on 2021-08-31
F2 got me into BIOS. Exiting BIOS into boot, tried ESC again and this time it got me the grub command line. Reboot command from there got me the standard boot menu back. Used Windows a few minutes to see it it looked kosher. It did. Shut down, repeated procedure to make sure it worked as a stopgap if needed, then rebooted normally and the menu remained.
Thanks all.

---

