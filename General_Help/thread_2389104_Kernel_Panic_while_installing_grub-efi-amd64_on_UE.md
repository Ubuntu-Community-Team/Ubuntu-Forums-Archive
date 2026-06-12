---
title: "Kernel Panic while installing grub-efi-amd64 on UEFI Secure Boot HP 11m-ad0XX"
date: 2018-04-11
forum: General Help
---

### Post by Casey_Friday on 2018-04-11
[Here is the Kernel Panic [gist.github.com]]("https://gist.github.com/fridaynext/ebf8524df2ffef5c163f233c08954eb2")

I've been trying multiple approaches for about 3 weeks now, and I still can't get Ubuntu to completely install on an HP Pavilion x360 Convertible 11m-ad013dx (also known as [11m-ad0XX]("https://support.hp.com/us-en/drivers/selfservice/hp-pavilion-11m-ad000-x360-convertible-pc/15551382/model/16351156")).  The installer always faces a kernel panic while installing GRUB to the EFI partition, while installing **grub-efi-amd-64**.  I have tried the following:


[LIST=1]
[*]TPM Available, Secure Boot ON, Legacy (CSM) **Disabled**
[*]TPM Hidden, Secure Boot ON, Legacy (CSM) **Disabled**
[*]TPM Available, Secure Boot OFF, Legacy (CSM) **Disabled**
[*]TPM Available, Secure Boot OFF, Legacy (CSM) **Enabled**
[*]Clear all HP Default Keys, TMP Hidden (OFF), Legacy (CSM) **Enabled**
[*]Tried just about everything from [oldfred's massive UEFI thread]("https://ubuntuforums.org/showthread.php?t=2147295") (great post!)
[*]Update [Intel microcode]("https://downloadcenter.intel.com/download/27591/Linux-Processor-Microcode-Data-File?v=t") (manually, and with [update-intel-microcode]("http://manpages.ubuntu.com/manpages/precise/en/man8/update-intel-microcode.8.html")) and try grub-efi-amd64 install again
[*]Install **linux-headers-4.15.0-13-generic** to see if it was a kernel problem (didn't help)
[*]Encrypt home directory / No encryption / LUKS for entire drive
[*]Separate /boot partition from the EFI partition
[*]Run **boot-repair** from Installation USB after installation is finished (crashes with the same kernel panic at grub-efi-amd64)
[*]Create a **boot-repair** boot USB, and disable Secure Boot to boot from that USB to attempt a boot-repair fix (**unsuccessful**)
[/LIST]
[B]
I have also tried:
[/B]    1. Install Windows 10 Home in UEFI mode (and update all drivers), then
[LIST]
[*]Install Ubuntu 16.04.4 with "alongside Windows Bootloader" option
[*]Install Ubuntu 16.04.4 by creating swap partition and EXT4 partition, selecting sda2 (EFI created by windows) as boot/efi
[*]Install Ubuntu 17.10 with above options
[/LIST]
    2.  Boot from Ubuntu USB installer, **format entire SSD**, install solo Ubuntu 16.04 / 17.10 **(****with no Windows installation)**

I've tried just about every combination I can think of, but I always get a Kernel Panic when trying to install the Grub EFI bootloader, which then affects all **dpkg** commands later, as the system sees **grub-efi-amd64 **as a broken package.  The system always freezes at "**Installing for x86_64-efi platform**."

[Here is the Kernel Panic [gist.github.com]]("https://gist.github.com/fridaynext/ebf8524df2ffef5c163f233c08954eb2")

I have found multiple [threads]("https://ubuntuforums.org/showthread.php?t=2330915") / posts that haven't provided successful solutions for me.
[SIZE=4]
* * *
[SIZE=1]&#8203;[/SIZE]
What I think it might be
[/SIZE]I'm assuming that this is either a kernel issue (need to find a non-problematic kernel) or a Secure Boot issue (HP Keys, TPM, etc), but I can't pin it down.  **Secure Boot is a must for this machine,** so although I'm okay installing Ubuntu with it disabled, I need it enabled full-time once the installation is successful.[SIZE=4]

Where to go from here?
[/SIZE]oldfred has mentioned that HP doesn't follow proper UEFI naming conventions, but I've still been able to get to the GRUB command line prompt and load the **vmlinuz/initrd** images, and boot successfully, just can't get full GRUB installed.

[B][SIZE=3]Help?[/SIZE]
[/B]If anyone has suggestions, please please let me know, as I really like the form factor of this laptop, but I'd like to get a successful UEFI + Secure Boot install.  I'm hoping the Kernel Panic includes a line that I missed, that's easy for someone else to spot what I need to change/fix to get this installed successfully.

---

### Post by oldfred on 2018-04-11
If you managed to get though oldfred's thread on install/repair, you now know as much as he does. :)

Even if you want secure boot (not sure why as it really is just Windows control), you may want to start with it off.
And then install signed kernel & grub. But you will not be able to add any proprietary drivers.

Never have changed any TPM settings, I thought it just worked with defaults.
 UEFI secure boot doesn't have anything to do with a TPM.
[https://www.ibm.com/developerworks/community/blogs/smartersecurity/entry/uefi_secure_boot_and_the_tpm20?lang=en](https://www.ibm.com/developerworks/community/blogs/smartersecurity/entry/uefi_secure_boot_and_the_tpm20?lang=en) 


 May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by dragonfly41 on 2018-04-11
I am a Dell user myself so can't help .. but found this thread  .. not very helpful though ..

[https://h30434.www3.hp.com/t5/Notebook-Boot-and-Lockup/I-can-make-my-HP-Pavilion-15-ab125ax-to-dual-boot/td-p/6145921](https://h30434.www3.hp.com/t5/Notebook-Boot-and-Lockup/I-can-make-my-HP-Pavilion-15-ab125ax-to-dual-boot/td-p/6145921)

---

### Post by Casey_Friday on 2018-04-13
BootInfo Summary: [http://paste.ubuntu.com/p/c9KMRX9vRP/](http://paste.ubuntu.com/p/c9KMRX9vRP/)

boot-repair has constant issues every time it asks to reinstall grub, when it gets to "installing for x86_64-efi platform", which generates that "General Protection Fault: 0000 [#1] SMP" in the kernel panic.  Still trying other things (attempting a Lubuntu install now, with the same results).

---

### Post by oldfred on 2018-04-13
It is an HP and a Celeron.
Both historically have had issues.
HP requires various work arounds, but I thought they Celeron issues were mostly resolved. 

It looks like grub is correctly install inside the ESP and has boot to grub.cfg in install. But report did not show a grub.cfg in your install. It that where grub is then failing (at creating grub.cfg)?
If you manually boot into install and run this do you get an error?
sudo update-grub

If all else fails we can create your own grub.cfg manually.

If you want to read ahead. I do this on some of my flash drive installs to simplify boot & updates. And I do it for all my additional installs and turn off os-prober as it takes forever to search all my partitions for other installs. 
That also could be an issue. If you have any NTFS or Linux partition that is corrupted os-prober may be crashing as it cannot open it to see if there is an install.

 How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)

---

### Post by Casey_Friday on 2018-04-16
It's actually a Pentium, but it's the mobile version.  I got through it, albeit in an unconventional way.


[LIST=1]
[*]Reset all BIOS security settings to default, including Secure Boot ON, and Legacy DISABLED
[*]Boot from Windows 10 1709 Recovery USB
[*]Delete all partitions, then click "New" in Windows installer partitioner
[*]Delete 'System', 'MSR', and main partitions, but keep the Recovery partition as is.
[*]Use DiskPart to install a 750MB EFI partition (labeled 'System'), with plenty of room for grub / linux headers
[*]Click 'New' again, and create a 36GB (out of 120GB SSD) partition for Windows - automatically creates the MSR again
[/LIST]

Then, I installed Windows 10, and all the drivers for the HP laptop, including all the CPU updates - Trusted Execution, etc.

I then booted from the USB Ubuntu 16.04 installer in UEFI mode, and in a terminal ran:

```
$: sudo -s
#: ubiquity -b
```

To install the OS without installing the bootloader.  Then, when it was time to partition, I chose "Something Else", and performed the following in the partitioner:


[LIST=1]
[*]Create an 8192 MB swap space partition (8GB of RAM installed in the laptop), then use the remaining space (~75GB) for the root (/) partition of Ubuntu.
[*]Encrypted the home directory
[*]Ran the installer.
[*]Clicked "Continue Testing", then **Shut Down **the computer.
[/LIST]

I then removed the SSD from that laptop, inserted it into a test desktop machine I have, and booted from the USB Ubuntu 16.04 installer, then installed boot-repair from the yannubuntu ppa, and ran boot-repair (with Secure Boot option checked) on the SSD, and it worked flawlessly.  I then put it back into the HP laptop, and I now have a functioning dual-boot Win10 / Ubuntu 16.04 setup with Secure Boot enabled.  **Awesome!**

---

