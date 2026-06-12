---
title: "New install"
date: 2024-02-28
forum: General Help
---

### Post by larryb1607 on 2024-02-28
I plan to install Ububtu Cinnamon on my external HDD.  I have a Ibuntu based distribution already installed on this device.  This install already has a boot, root and a home partition.  I am going to slowly phase out this distro in favor of the Cinnamon one.  I will be setting up an ext4 partition and then installing similar to the other distro install.  Do I still have to create a new boot partition or will the new boot data be written to the old boot partition?  Any other suggestions welcome.

Thaks

---

### Post by cdbrunow on 2024-02-28
As far as I'm aware, if you're installing onto an external HDD the installer will make a new root and boot partition on that drive that will be recognizable by the BIOS/UEFI. It's customizable in the installer IIRC

EDIT: You might be able to tell the installer to use the boot partition on the other drive, I'm not sure. If so I think you would need to update your bootloader settings to allow you to select which OS you want to boot into.

---

### Post by tea for one on 2024-02-28
> **larryb1607 said:**
> I plan to install Ububtu Cinnamon on my external HDD.
What is installed on your internal disk?
Is it UEFI mode with GPT?

---

### Post by oldfred on 2024-02-28
Are you installing Ubuntu and then the Cinnamon desktop.
Or another distribution that uses Cinnamon?

Do not confuse a /boot partition that is ext4 and not really required for most desktops with an ESP - efi system partition required for UEFI boot that does have the grub boot files. ESP is normally shared, /boot should not be shared. But Ubuntu distributions both official flavors & others based on Ubuntu use "ubuntu" for default boot entry. And external drives boot directly like live installer from a UEFI : xxxx entry where xxxx is name or label of drive. And internal entry with "ubuntu" will require external drive to be plugged in to boot any install.
 
UEFI is normally gpt partitioned, not very old MBR(msdos) partitioned.

Most systems since 2012 are UEFI (even if vendor still says BIOS) as Microsoft required vendors to install Windows in UEFI boot mode to gpt partitioned drives with release of Windows 8.
My Dell still says BIOS, but once in "BIOS" it says it is UEFI only. Systems starting 2020 are becoming UEFI only.

---

### Post by deadflowr on 2024-02-28
> Are you installing Ubuntu and then the Cinnamon desktop.
Or another distribution that uses Cinnamon?


Going out on a limb and guessing they're installing Ubuntu Cinnamon
[https://cdimage.ubuntu.com/ubuntucinnamon/releases/23.10/release/]("https://cdimage.ubuntu.com/ubuntucinnamon/releases/23.10/release/")
It is an official flavor now, but currently only 23.10 is supported.

They do offer a version for 22.04 that was pre-official flavor, but that looks like it'll reach EOL soon.

---

### Post by larryb1607 on 2024-02-29
I got the distro from here: [https://ubuntu.com/desktop/flavours](https://ubuntu.com/desktop/flavours).  My system is a Dell laptop running Windows 7 on the main HDD.  This was purchased in 2012, but may be older.  I am pretty sure that it does NoT have a UEFI BIOS.  I boot Linux from an external HDD.  I created an ext4 partition on the ext HDD and installed the older Ibuntu based distro onto that partition.  Gparted shows 3 partitions within the larger partitiom.  I plan to do the same thing to install the Cinnamo flavor, but then I wondered about having 2 boot partitions and came here.

---

### Post by tea for one on 2024-02-29
> **larryb1607 said:**
> My system is a Dell laptop running Windows 7 on the main HDD.  This was purchased in 2012, but may be older.  I am pretty sure that it does NoT have a UEFI BIOS
You can double check via System Information > System Summary > BIOS Mode

It's important to know the installed mode of your Windows OS because you should always avoid mixed mode dual boot systems.

---

### Post by yancek on 2024-03-01
>   Gparted shows 3 partitions within the larger partitiom.  I plan to do  the same thing to install the Cinnamo flavor, but then I wondered about  having 2 boot partitions and came here. 		

That would indicate an MBR/Legacy install with an Extended partition containing logical partitions.  You could determine this by simply running the command:  sudo parted -l
If you don't understand the output, post it here and someone will explain.

Where do two boot partitions come in?  Are you going to keep the old Linux and then add the new one?  You don't need or want two boot partitions on the same drive and in fact, in most insances do not need a boot partition.

---

### Post by larryb1607 on 2024-03-03
Strange, I submitted a reply yesterday and do not see it.  Anyway, my laptop is Legacy BIOS.  I plan to slowly migrate to the newer install which I have not done yet.  I would keep the old install until I have migrated data and anything else I need and then remove it.

---

### Post by oldfred on 2024-03-03
Apps store data in /home. But using that data in newer install may change data and make it not work in old install.
I had that happen with my Firefox profile. I had used it in multiple installs for years, but then using profile in a new install broke use in other installs. I had backup so old install still worked. Best to have good backups before any major change.

Should not need /boot as a partition unless a server type install using LVM & encryption. And I believe not may not be required anymore as boot process has been updated to support encrypted LVM better.

Also swap is now a file inside /. If you have a swap partition it will automatically be used. That is normally not an issue unless you use hibernation and hibernation not normally recommended.

---

