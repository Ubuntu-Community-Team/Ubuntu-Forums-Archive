---
title: "Unable to reinstall grub"
date: 2023-10-10
forum: General Help
---

### Post by maitreya10 on 2023-10-10
I'm running a Windows 11 dual boot with Kubuntu 22.04(LTS) on a Dell laptop. I opened Windows 11 after almost 3 months and the system did a complete update of it's firmware which stopped showing me the grub menu during boot and the system now directly boots into Windows, I tried to do the recommended boot-repair using live USB but it gave some errors. 
Here's the link of the boot repair report
**Link:** [https://paste.ubuntu.com/p/4xwwfKWTsw/](https://paste.ubuntu.com/p/4xwwfKWTsw/)

Below is the output of the ```
[COLOR=#000000][FONT=&amp]sudo dmidecode -t 0,1[/FONT][/COLOR]
``` command:[COLOR=#000000][FONT=&amp]
[/FONT][/COLOR]```
[FONT=monospace][COLOR=#000000]# dmidecode 3.3[/COLOR]
Getting SMBIOS data from sysfs.
SMBIOS 3.2 present.

Handle 0x0001, DMI type 0, 26 bytes
BIOS Information
        Vendor: Dell Inc.
        Version: 1.24.0
        Release Date: 08/11/2023
        ROM Size: 32 MB
        Characteristics:
                PCI is supported
                PNP is supported
                BIOS is upgradeable
                BIOS shadowing is allowed
                Boot from CD is supported
                Selectable boot is supported
                EDD is supported
                Print screen service is supported (int 5h)
                8042 keyboard services are supported (int 9h)
                Serial services are supported (int 14h)
                Printer services are supported (int 17h)
                ACPI is supported
                USB legacy is supported
                Smart battery is supported
                BIOS boot specification is supported
                Function key-initiated network boot is supported
                Targeted content distribution is supported
                UEFI is supported
        BIOS Revision: 1.24

Handle 0x0100, DMI type 1, 27 bytes
System Information
        Manufacturer: Dell Inc.
        Product Name: Inspiron 15 3511
        Version: Not Specified
        Serial Number: FZXY3L3
        UUID: 4c4c4544-005a-5810-8059-c6c04f334c33
        Wake-up Type: Power Switch
        SKU Number: 0AB0
        Family: Inspiron
[/FONT]
```[COLOR=#000000][FONT=&amp]
[/FONT][/COLOR]
 Boot-repair gives Locked-NVram detected error.

---

### Post by MAFoElffen on 2023-10-10
Thank you. Didn't see another PM. But found your thread...

Now follow the direction from my second message...

To others, his report say it was booted in BIOS mode Legacy/CSM instead of UEFI. I gave him instructoins to create the Boot repair LiveUSB to force it to boot only as UEFI.

---

### Post by maitreya10 on 2023-10-10
Followed the instructions for creating the LiveUSB in UEFI mode, here's the link of the summary given by boot info without doing the boot repair.
**Link: **[https://paste.ubuntu.com/p/Dk4mG8GZ9C/](https://paste.ubuntu.com/p/Dk4mG8GZ9C/)

---

### Post by MAFoElffen on 2023-10-10
Congratulatons. It booted as UEFI. > /sys/firmware/efi/efivars was created and the EFIVARS were read. > NVRAM was not locked.

Boot-Repair should be able to fix that with no problems now.

Please keep us posted.

---

### Post by maitreya10 on 2023-10-10
Did the recommended boot-repair but it failed with the same error saying **[COLOR=#111111][FONT=monospace]NVram is locked (Ubuntu not found in efibootmgr)[/FONT][/COLOR]**[COLOR=#111111][FONT=monospace].
Here's the boot repair summary
**Link:** [https://paste.ubuntu.com/p/CGcSCzHSrJ/](https://paste.ubuntu.com/p/CGcSCzHSrJ/)[/FONT][/COLOR][COLOR=#111111][FONT=monospace][/FONT][/COLOR]

---

### Post by MAFoElffen on 2023-10-10
Download and create a UEFI boot only Installer LiveUSB for Ubuntu 22.04.3 LTS. It has the same kernel as your installed system.

On first boot ensure Windows has fastboot turned off. then reboot and get into the BIOS settings. I can see that SecureBoot is turned off.

Boot from the Installer LiveUSB, Use "Try". Open a terminal session.
```

ls /sys/firmware/efi/efivars/
# if this comes back as not found, stop here and post back the results

# if it come back good, then continue
sudo su
mount /dev/nvme0n1p7 /mnt
mount --make-private --rbind /dev  /mnt/dev
mount --make-private --rbind /proc /mnt/proc
mount --make-private --rbind /sys  /mnt/sys
mount --make-private --rbind /run /mnt/run
cd /mnt
chroot .
mount -a
apt update
grub-install --target=x86_64-efi --efi-directory=/boot/efi --bootloader-id=ubuntu --recheck --no-floppy
exit
sudo shutdown -P now

```
Boot and test.

---

### Post by MAFoElffen on 2023-10-10
As for this error:
```

modprobe: FATAL: Module efivars not found in directory /lib/modules/6.2.0-26-generic

```
That seems to be a BUG in the script. efivars does not exist in the system except as /sys/firmware/efi/efivars. There is no efivars at /lib/modules/*-generic/. At least, not in Ubuntu. I will report that to yannubuntu... (I'm a contributor.)

Just for my own notes for the BUG Report, after 12.04, it didn't have an efivars or efivarfs module added as a module if it was built into the kernel, which can be found by:
```

mafoelffen@Mikes-ThinkPad-T520:~$ grep 'CONFIG_EFI_VARS=y\|CONFIG_EFIVAR_FS=' /usr/src/linux-headers-*-generic/.config
/usr/src/linux-headers-5.15.0-58-generic/.config:CONFIG_EFI_VARS=y
/usr/src/linux-headers-5.15.0-58-generic/.config:CONFIG_EFIVAR_FS=y
/usr/src/linux-headers-5.15.0-84-generic/.config:CONFIG_EFI_VARS=y
/usr/src/linux-headers-5.15.0-84-generic/.config:CONFIG_EFIVAR_FS=y
/usr/src/linux-headers-5.19.0-46-generic/.config:CONFIG_EFI_VARS=y
/usr/src/linux-headers-5.19.0-46-generic/.config:CONFIG_EFIVAR_FS=y
/usr/src/linux-headers-6.2.0-32-generic/.config:CONFIG_EFIVAR_FS=y
/usr/src/linux-headers-6.2.0-33-generic/.config:CONFIG_EFIVAR_FS=y

```
It looks like after kernel 5.19.0-46 is where it made the transition from efivars to just efivarfs... The 6.2 kernels on my computer only have that.

---

### Post by maitreya10 on 2023-10-10
Getting error for the chroot command.
```
[FONT=monospace][COLOR=#000000]root@kubuntu:/mnt# chroot[/COLOR]
chroot: missing operand
Try 'chroot --help' for more information.

[/FONT]
```

Should the "chroot" command instead be "chroot /mnt"?

---

### Post by maitreya10 on 2023-10-10
> **MAFoElffen said:**
> Download and create a UEFI boot only Installer LiveUSB for Ubuntu 22.04.3 LTS. It has the same kernel as your installed system.

On first boot ensure Windows has fastboot turned off. then reboot and get into the BIOS settings. I can see that SecureBoot is turned off.

Boot from the Installer LiveUSB, Use "Try". Open a terminal session.
```

ls /sys/frimware/efi/efivars/
# if this comes back as not found, stop here and post back the results

# if it come back good, then continue
sudo su
mount /dev/nvme0n1p7 /mnt
mount --make-private --rbind /dev  /mnt/dev
mount --make-private --rbind /proc /mnt/proc
mount --make-private --rbind /sys  /mnt/sys
mount --make-private --rbind /run /mnt/run
cd /mnt
chroot
mount -a
apt update
grub-install --target=x86_64-efi --efi-directory=/boot/efi --bootloader-id=ubuntu --recheck --no-floppy
exit
sudo shutdown -P now

```
Boot and test.
Getting error at chroot command, asking for operands, should it be "chroot /mnt"?

---

### Post by MAFoElffen on 2023-10-10
Yes. either of these...
```

chroot /mnt
## OR
chroot .

```
Because you cd'ed into /mnt already by that point...

---

### Post by maitreya10 on 2023-10-10
> **MAFoElffen said:**
> Download and create a UEFI boot only Installer LiveUSB for Ubuntu 22.04.3 LTS. It has the same kernel as your installed system.

On first boot ensure Windows has fastboot turned off. then reboot and get into the BIOS settings. I can see that SecureBoot is turned off.

Boot from the Installer LiveUSB, Use "Try". Open a terminal session.
```

ls /sys/frimware/efi/efivars/
# if this comes back as not found, stop here and post back the results

# if it come back good, then continue
sudo su
mount /dev/nvme0n1p7 /mnt
mount --make-private --rbind /dev  /mnt/dev
mount --make-private --rbind /proc /mnt/proc
mount --make-private --rbind /sys  /mnt/sys
mount --make-private --rbind /run /mnt/run
cd /mnt
chroot . T
mount -a
apt update
grub-install --target=x86_64-efi --efi-directory=/boot/efi --bootloader-id=ubuntu --recheck --no-floppy
exit
sudo shutdown -P now

```
Boot and test.
Thanks alot for your time and wonderful input, I was able to successfully get back into my Ubuntu system following your instructions. The grub has been installed again and works well.

---

### Post by MAFoElffen on 2023-10-10
Glad everything worked out and things are working for you.

Again, welcome to the Ubuntu Forum. It's a great Community, with some wonderful people that like to share their experience and enjoy helping each other. If you ver have a question about something feel free to ask.

---

