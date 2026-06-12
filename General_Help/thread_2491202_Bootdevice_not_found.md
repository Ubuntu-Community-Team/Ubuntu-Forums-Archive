---
title: "Bootdevice not found"
date: 2023-09-29
forum: General Help
---

### Post by furnicket on 2023-09-29
Hello,
I have an HP Elitebook 8470p and I installed ubuntu with a USB key.
The installation went well but it no longer starts and it is displayed  "bootdevice not found please install an operating system on your hard  disk, Hard Disk - (3F0)
I tried a boot repair that shows me: 
The current session is in BIOS-compatibility mode. Please disable  BIOS-compatibility/CSM/Legacy mode in your UEFI firmware, and use this  software from a live-CD (or live-USB) that is compatible with UEFI  booting mode. For example, use a live-USB of Boot-Repair-Disk-64bit ([www.sourceforge.net/p/boot-repair-cd]("http://www.sourceforge.net/p/boot-repair-cd")), after making sure your BIOS is set up to boot USB in EFI mode. This will enable this feature.
The problem is that my Bios doesn't have these options.
Here's also the boot-info: [https://paste.ubuntu.com/p/TbHB67jvhY/](https://paste.ubuntu.com/p/TbHB67jvhY/)
Thank you for your help, have a good day.

---

### Post by MAFoElffen on 2023-10-02
From booting from a Ubuntu 22.04.3 desktop installer LiveUSB, please post the results of this within CODE tags:
```

sudo dmidecode -t 0,1

```
Up until about a year ago, I worked as a Certified Onsite HP, Dell ad Lenovo Warranty Service Technician. I know that the UEFI settings in that machine has options to change that.

Also, in the creation of the installer media, if you create it as GPT, then it will only boot as UEFI... That error message has no need to lie to you. We just need to explore ways to support it in different ways until we get something to enforce that better.

---

### Post by oldfred on 2023-10-02
You are showing both BIOS install with grub in MBR and bios_grub partition.
And UEFI install with grub in ESP - efi system partition, your sda2.
Your Boot-Repair report shows it booted in BIOS mode.
But you have mount of ESP in fstab on line 167 for UEFI boot. So last fix or install was UEFI.

You should only boot in same mode, always UEFI or always old BIOS. How you boot live installer flash drive UEFI or BIOS is then how it installs or repairs.
Microsoft has required vendors to install Windows in UEFI boot mode to gpt partitioned drives since 2012, so most systems now are UEFI based.

Some older HP, seem to have a hard coded UEFI that only booted "Windows Boot Manager" by description. Or may dual boot as long as Windows entry was there.
If only booting Ubuntu we have added an UEFI boot entry that says Windows but boots Ubuntu.
See also
man efibootmgr

The efibootmgr command assumes ESP is sda1 unless you give it specific drive -d & partition -p parameters:
    sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi" -d /dev/sda -p 2

You can revert to Windows boot with:
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\Microsoft\Boot\bootmgfw.efi" -d /dev/sda -p 2

---

### Post by furnicket on 2023-10-03
I'm sorry, I'm a beginner on Linux and I don't have good computer skills, so I'm having trouble understanding everything. If I understand correctly, to be able to run ubuntu I have to write in the terminal: sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi" -d /dev/sda -p 2 
If so, since the computer does not start, how can I access the terminal? From the USB boot key?

---

### Post by furnicket on 2023-10-03
```

# dmidecode 3.3
Getting SMBIOS data from sysfs.
SMBIOS 2.7 present.

Handle 0x000E, DMI type 0, 24 bytes
BIOS Information
    Vendor: Hewlett-Packard
    Version: 68ICF Ver. F.74
    Release Date: 04/11/2019
    Address: 0xF0000
    Runtime Size: 64 kB
    ROM Size: 5 MB
    Characteristics:
        PCI is supported
        PC Card (PCMCIA) is supported
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
    BIOS Revision: 15.116
    Firmware Revision: 66.56

Handle 0x000F, DMI type 1, 27 bytes
System Information
    Manufacturer: Hewlett-Packard
    Product Name: HP EliteBook 8470p
    Version: A1029D1102
    Serial Number: CNU336CXFW
    UUID: 274d9d1f-7382-11e3-bbcd-d9e6c803c06a
    Wake-up Type: Power Switch
    SKU Number: A1G60AV
    Family: 103C_5336AN G=N L=BUS B=HP S=ELI

```

---

### Post by oldfred on 2023-10-03
if you boot live installer flash drive in UEFI boot mode, you can use efibootmgr.
Do not think efibootmgr works if in BIOS boot mode.

---

### Post by furnicket on 2023-10-03
when I write the command in the terminal, it answers me: EFI variables are not supported on this system

---

### Post by oldfred on 2023-10-03
Did you boot live installer in UEFI mode?

---

### Post by furnicket on 2023-10-03
when I write the command in the terminal with desktop installer LiveUSB , it answers me : EFI variables are not supported on this system

Here is the bios: [https://postimg.cc/s1xQr2GQ](https://postimg.cc/s1xQr2GQ) 
and the error message: [https://postimg.cc/23LkGLBw](https://postimg.cc/23LkGLBw)

---

### Post by furnicket on 2023-10-03
how do I know if the live boot installer is in UEFI mode? I downloaded the standard ubuntu

---

### Post by furnicket on 2023-10-03
when I write in terminal: [ -d /sys/firmware/efi ] && echo "EFI Session" || echo "Non-EFI session" he answers: non-EFI session
I don't know how to have a EFI session

---

### Post by tea for one on 2023-10-03
> **furnicket said:**
> I don't know how to have a EFI session
When you boot a USB device to run a live "Try Ubuntu" session (or install an operating system), you can sometimes have two options per device if both Legacy and UEFI are allowed in the firmware settings.
The attachment shows the two options.
You need the option beginning with UEFI: (i.e. UEFI followed by a colon)

---

### Post by furnicket on 2023-10-04
When I escape at startup, I arrive at this: [https://postimg.cc/18pPc1jr](https://postimg.cc/18pPc1jr) 
Then I do F10 and I fall back to F2 
If I press F9 I come across this: [https://postimg.cc/k6J3qVw2](https://postimg.cc/k6J3qVw2) then this: [https://postimg.cc/k2mTk0T4](https://postimg.cc/k2mTk0T4) 
With F7 or ENTER, I get the error message 3F0 While doing my research, 
I have the impression that I simply no longer have BIOS, is this possible?

---

### Post by furnicket on 2023-10-04
I tried to reinstall the Bios by downloading it from the HP site except that now when I press F10 I am asked to enter a BIOS Administrator password which I do not have... (it was a computer 'business). Do you see another solution?

---

### Post by oldfred on 2023-10-04
You always need to know the UEFI/BIOS password, if one is set.

You may be able to reset password by removing coin battery or jumpering pins next to coin battery on motherboard.
You need to review service manual for your machine which you can download from HP.

---

