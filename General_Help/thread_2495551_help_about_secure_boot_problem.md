---
title: "help about secure boot problem"
date: 2024-02-22
forum: General Help
---

### Post by cwajdix on 2024-02-22
Hello
I need help from people who want to stand on the light side of the force... For a long time I have had an unusual problem with hacking devices and accounts in my home network. Maybe I will try to describe the problem with the Linux laptop. Asus vivobook with uefi bios.
When I finally managed to burn Ubuntu 23.10 legacy in which the checksum was correct. I receive the message:
error: shim_lock protocol not found.
error:
you need to load the kernel first.
Press any key to continue.....
  the entire message is visible in the photo. The above loading error occurs when UEFI secure boot is enabled. Generally, loading Linux on my laptop is only possible when:
- I turn off secure boot
- loads live linuxes that have not passed the checksum

The code loading the grub botloader "try or install ubuntu" looks like this:
setparems 'Try or Install Ubuntu'
set gfxpayload keep Linux
/casper/vmlinuz files/cdrom/preseed/ubuntu.seed maybe-
ubiquity quiet splash --
initrd
/casper/initrd

Currently, I don't have any disk installed in my laptop, I only run on the live version loaded into RAM. And regardless of the Linux distribution, the same snap packages in loop0-loop7 are always loaded at every boot. Which can be listed using losetup -l. To be honest, I don't fully understand these mechanisms, but...
I have removed the network card from the motherboard and still the "who" command, which previously only listed tty: of my live session. After some time (usually this can be seen when the processor fan suddenly speeds up to about 3500-4000 rpm) without any special intervention from me or an increase in the number of processes in the system. Sometimes, when I'm in the bios, the laptop starts and goes into helicopter mode...
I will provide the logs and all necessary attachments needed to diagnose and solve his problem that prevents me from doing my job.

---

### Post by oldfred on 2024-02-23
You cannot boot legacy/BIOS/CSM with Secure Boot on.
CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode, only available with secure boot off.

If UEFI system generally better to boot in UEFI mode, either with Secure boot off or with it on, your choice.
But if you need proprietary drivers, you have to provide a MOK - machine owner key to authorize the driver. Ubuntu cannot provide Secure Boot key for proprietary binary blobs like the nVidia driver. And if trusted source, the owner then can provide a MOK.

I use Kubuntu which is a bit more lightweight and do not allow snaps. 
I also have a full install & copy of all files in desktop on an external SSD. I highly recommend using external SSD over flash drives, now. I have many flash drives and do not plan on any more as external SSD is almost as fast as internal SSD or very quick.

System may be running background tasks, does top show what is running?
As system is used it warms up and then fans may speed up.

---

