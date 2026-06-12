---
title: "Cannot boot into Ubuntu"
date: 2023-05-10
forum: General Help
---

### Post by androy518 on 2023-05-10
Device: HP 15t-cs200
OS: Ubuntu 23.04 (installed on nvme ssd)

I cannot boot into Ubuntu. It started after I installed Flatpak with apt and restarted. I got an error that that I do not remember and it would not boot. I tried restarting and got the same error. I logged into Windows which was installed on a separate sata ssd and downloaded the Ubuntu ISO from the website and added it to a flash drive that I have Ventoy installed on. When I booted into it, it detected the Ubuntu that I already had installed but there was no option to repair it. I tried installing it and it worked then I removed the second Ubuntu and its partition using gparted on the usb flash drive. When I restarted, instead of the boot loader, I saw the GNU GRUB command line.
I tried typing:
 set pager=1
 ls
 ls (hd1,gpt2)/
 ls -l (hd1,gpt2)/boot
 set root=(hd1,2)
 linux /boot/vmlinuz-6.2.0-20-generic root=/dev/nvme0n1p2
 initrd /boot/initrd.img-6.2.0-20-generic
 boot

When it started, it looked like it did something for a little while before freezing. I tried turning the computer off and on again but it ended up back in the Gnu grub instead of the bootloader.

This album contains a picture of the partitions on the ssd that Ubuntu is installed on and a picture of the freeze after trying to boot from Gnu grub. [https://imgur.com/a/dOQYFs5](https://imgur.com/a/dOQYFs5)

Can anyone solve this issue?

---

### Post by oldfred on 2023-05-10
You often get grub when you have two grub's, one old non-working one & one new one.
And that is then from installing differently UEFI or BIOS. Since UEFI system, you should always use UEFI.
I also see virtual install which I do not know about?

Please copy & paste the pastebin link to the BootInfo summary report ( do not post report), do not run the auto fix till reviewed. Use often updated ppa version over somewhat older ISO with your USB installer  or any working install.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by androy518 on 2023-05-10
This is the link: 
[http://paste.ubuntu.com/p/jy3qbscmKs/](http://paste.ubuntu.com/p/jy3qbscmKs/)

---

### Post by mIk3_08 on 2023-05-10
> **androy518 said:**
> This is the link:
[http://paste.ubuntu.com/p/jy3qbscmKs/](http://paste.ubuntu.com/p/jy3qbscmKs/)

It says   "No boot loader is installed in the MBR of /dev/nvme0n1."
> 
============================== Boot Info Summary ===============================

 => No boot loader is installed in the MBR of /dev/nvme0n1.
 => Windows 7/8/10/11/2012 is installed in the MBR of /dev/sda.
 => Grub2 (v2.00) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,2)/grub. It also embeds following components:
    
    modules
--------------------------------------------------------------------------------------------------------------------------------------
> **oldfred said:**
> You often get grub when you have two grub's, one old non-working one & one new one.
Please take the advice of oldfred. This will give you a big chance that you can revive your O.S's. seems you have dual boot O.S in your machine. 
You can use rEFInd, Grub2, Clover EFI Bootloader and etc. for this.
Regards and cheers.

---

### Post by androy518 on 2023-05-10
I do have dual boot. Windows is installed on a separate ssd so it works properly. How would I go about removing the broken grub/installing grub? Do I do that from the Ubuntu iso on the flash drive? Also, which partition would I install it to? Would it be the nvme0n1p1?

---

### Post by oldfred on 2023-05-10
You do not want grub in MBR as that is for old BIOS install.
You have UEFI system, UEFI install of Windows & Ubuntu looks like it is UEFI as you have mount of ESP - efi system partition in fstab on line 226.

But you now show UEFI Secure Boot on, line 92? Did you originally install with it on? Try with UEFI Secure Boot off.
There are in effect two versions of Ubuntu installs. One for UEFI Secure boot where the entire boot process is signed. And one without Secure boot.

You always install boot loaders to a drive like /dev/sda or /dev/nvme0n1, not to a partition lik nvme0n1p1. With UEFI installs it knows to find & use the ESP for updated boot files.

Boot-Repair is offering to reinstall the signed version of grub. But you may need signed kernel & if proprietary video like nVidia Or Wi-Fi you have to manually sign the proprietary driver with a MOK - machine owner key. Or you are verifying the code is safe. Since proprietary drivers are a blob of code Ubuntu cannot sign that code.

---

### Post by androy518 on 2023-05-11
I tried booting with secure boot off it went to the Gnu grub. After I typed the commands, I got the same freeze that I got before. I think I may have had Secure Boot enabled when I installed it before. How can I tell for sure if Secure Boot was enabled when I installed it? I remember using mok manager before.

---

### Post by oldfred on 2023-05-11
If you used MOK then you installed with Secure Boot on.
I do not use Secure Boot.
You can turn it back on and use Boot-Repair's advanced mode to reinstall grub & also choose to install a kernel. You then will need to use MOK to allow the addition of a proprietary driver. Not sure how that works when reinstalling.

---

### Post by androy518 on 2023-05-11
I ran the boot repair and I was able to install the bootloader, start the system, and get to the error that I forgot about. It looked something like
/dev/nvme0n1p2 clean (a large fraction) blocks ...
I pressed alt+f2, signed in, then ran
sudo apt-get install --reinstall ubuntu-desktop
reboot

After the reboot, I was able to access Ubuntu again. Thank you for the help.

---

### Post by oldfred on 2023-05-11
This is not an error, but just a message saying system has found no issues.
/dev/nvme0n1p2 clean

Glad you got it working.  You can change to Solved.

---

