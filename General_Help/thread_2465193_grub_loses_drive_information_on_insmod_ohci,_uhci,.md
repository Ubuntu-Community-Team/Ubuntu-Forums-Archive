---
title: "grub loses drive information on insmod ohci, uhci, and ehci"
date: 2021-07-24
forum: General Help
---

### Post by tails862 on 2021-07-24
**Problem Brief:**
When /boot/grub/grub.cfg calls insmod of ohci, uhci, and ehci, grub seems to lose all memory of all drive information, leaving only (proc) or (memdisk). I simply deleted those mod files from /boot/grub/x86_64-efi/ to work around this. Grub will then complain that those can't be loaded, but it will still proceed to start Ubuntu without issue. I can live with my workaround, but it bugs me to do something like this.

[B]How I Got Here:
[/B]I created a portable LUKS encrypted Linux boot on an external drive. This drive started out with a 100 MB FAT32 drive for EFI and an encrypted LUKS partition which held root and swap. This worked fine for me without issue, but I had to enter the encryption twice: once to load /boot/grub/grub.cfg and again to load Linux. I decided that it wouldn't hurt security much if I created a third unencrypted ext4 partition for /boot to handle the rest of grub. (I was thinking, this should be easy peasy, right? ](*,)) I copied over boot, updated fstab, and deleted everything under /boot of my root partition, leaving /boot/efi alone. I manually edited grub.cfg of the efi partition to no longer call cryptomount and instead load from this new /boot parition. After rebooting the machine, grub was loaded fine from my new boot partition at /boot/grub/grub.cfg, but it had difficulty finding any drives. It displayed the grub menu. I could drop into command prompt with 'c'. The command "ls" there showed no drives present. 

I only discovered the issue with ohci, uhci, and ehci because I threw in a bunch of echos and ls commands into /boot/grub/grub.cfg like so:
```
echo '1'
ls
insmod usb_keyboard
echo '2'
ls
insmod ohci
echo '3'
ls
insmod uhci
echo '4'
ls
insmod ehci
echo '5'
ls
...
sleep 10


```
At 3 is where ls produced no drive information. Not even the internal drives were shown.

[B]What I've Tried:
[/B]I've tried obliterating /boot/grub and /boot/efi then reinstalling with *grub-install --removable /dev/sda* then *update-grub*. This produces the same issue.

[B]Version Numbers:
[/B]Ubuntu 18.04
Kernel: 5.4.0-80-generic
grub-install: grub-install (GRUB) 2.02-2ubuntu8.23
grub-update: grub-mkconfig (GRUB) 2.02-2ubuntu8.23

[B]Hardware:
[/B]Sager gaming laptop
Samsung T7 SSD (in USB A 3.0 slot)


I appreciate any feedback. Thanks for your time!

---

### Post by oldfred on 2021-07-24
I do not know LVM & encryption. But this is just to see if all UUIDs & GUIDs are correct.

Lets see details, use ppa version with your live installer (2nd option) or any working install,  not Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 

If you use Boot-Repair with encrypted partitions, be sure to mount and decrypt those partitions first.

---

### Post by tails862 on 2021-07-25
Here is the boot info: [http://paste.ubuntu.com/p/YsMnK8mrbZ/](http://paste.ubuntu.com/p/YsMnK8mrbZ/)

I tried running the boot recovery before getting this info, but I still had to *rm /boot/grub/x86_64-efi/?hci.mod* to get grub to boot into Ubuntu again.

---

### Post by oldfred on 2021-07-25
I am not familar with any of the .mod grub files you are saying are issues.

You do have UEFI system, with both Windows & Ubuntu booting in UEFI mode.
But also have old BIOS boot loaders in MBR of all three drives.
That should not matter, as long as you never try to boot in Legacy/BIOS/CSM boot mode.
CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode, only available with secure boot off.

You do show one unknown partition on nvme0n1p1 and it is MBR partitioned.
With UEFI, gpt partitioning is normally used. And both other drives are gpt.

Report did not show some details that typically are inside your / , like fstab & grub.cfg.
Did you not decrypt install before running Boot-Repair, so it could see /? Do not attempt an update, without decrypting as then it cannot fully update & breaks things.

If trying to mount a partition in nvme0n1p1, that can cause errors.
You need to resolve that. Is it also encrypted? Or corrupted?
And better to be gpt, if you have to redo it.

And with multiple drives the drive order & then defaults can cause issues.
System is supposed to use UUID & GUID, but have had issues where grub says hd1, and it only works if I manually change entry to hd0 or hd2. UEFI/BIOS sets drive order, usually based on SATA port order. But NVMe drives may be first or last in order.

---

### Post by tea for one on 2021-07-25
> **oldfred said:**
> You do have UEFI system, with both Windows & Ubuntu booting in UEFI mode.

The lines in the boot-repair report which I cannot quite understand:-

[COLOR="#0000FF"]Lines 82 - 84[/COLOR] 1 OS detected  OS#1:   The OS now in use - Ubuntu 18.04.5 LTS CurrentSession on mapper/ubuntu--vg-root

Windows is undetected?

I hope that the OP can confirm that Windows is installed and bootable?

---

### Post by tails862 on 2021-07-25
Thanks for the info!

The internal nvme drives are used solely when booting Windows and are encrypted with Bitlocker. I was running the Ubuntu system natively from sda when I executed this tool, and mapper/ubuntu--vg-root was properly mounted to /. 

As I was typing my reply, I realized what happened, and now I feel embarrassed :oops: . 

I was having issues with the laptop keyboard and mouse not working when I first setup this system. I applied many different tweaks to /etc/default/grub which forced loading USB. One of them was:
```
GRUB_PRELOAD_MODULES="usb usb_keyboard ohci uhci ehci"
```

 All I really needed to get that working was:
```
GRUB_CMDLINE_LINUX="i8042.nomux=1 i8042.reset"
```

Part of that boot repair cleaned out /etc/default/grub for me, but it didn't automatically execute update-grub which is why I didn't notice until now. Instead of executing that myself, I had copied a grub.cfg backup I had.

I'm guessing that the ohci, uhci, and ehci depends on the rest of the system to be decrypted before they can be loaded? sda2 isn't decrypted at the point when those modules are loaded. Does that sound plausible?

Thank you so much for your time!

---

### Post by tea for one on 2021-07-25
Complicated stuff - Dual booting, external drive with Ubuntu, Windows encryption, laptop keyboard and mouse misbehaving ;)

Yet, somehow boot-repair often yields a couple of clues which lead to a successful outcome.

It is a remarkable piece of software.

---

