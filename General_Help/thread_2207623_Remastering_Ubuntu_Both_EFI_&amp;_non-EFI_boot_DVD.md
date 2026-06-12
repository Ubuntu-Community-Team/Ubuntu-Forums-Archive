---
title: "Remastering Ubuntu: Both EFI &amp; non-EFI boot DVD?"
date: 2014-02-24
forum: General Help
---

### Post by jstar10 on 2014-02-24
Hey all,

I'm trying to develop a customized Ubuntu DVD that will boot on both EFI & non-EFI machines. The official Ubuntu distribution does this -- I'm wondering how?

I currently have been using Remastersys to create ISOs, but it doesn't boot on EFI machines & development on that project slowed (halted?). I did find this post:

[http://www.remastersys.com/forums/index.php?topic=2632.0](http://www.remastersys.com/forums/index.php?topic=2632.0)

... but the download links that point to a specific IP are no longer available.

Ultimately, I want to customize a distribution: set which packages are installed, background image, startup scripts etc. & be able to distribute the DVD & not have to worry if the end-user has an EFI or non-EFI setup.

Any help would be appreciated!

---

### Post by oldfred on 2014-02-24
Since the Ubuntu installer is on a FAT32 partition with boot flag, UEFI will look for efi files in the efi partition. That uses grub to boot in efi mode.
But a BIOS boot does not see efi partition but sees a bootable partition and looks for standard syslinux boot files.
And they are the same partition but the different boot loaders are ignored if in different mode.

---

### Post by dvdlmnzr on 2014-04-25
> **oldfred said:**
> Since the Ubuntu installer is on a FAT32 partition with boot flag, UEFI will look for efi files in the efi partition. That uses grub to boot in efi mode.
But a BIOS boot does not see efi partition but sees a bootable partition and looks for standard syslinux boot files.
And they are the same partition but the different boot loaders are ignored if in different mode.

Thanks for the feedback! I'm working with OP on this project. 

I'm a little confused when you mention partitions. We're hoping to create a bootable DVD, and as far as I know, we can't partition the DVD with different flags. Is there a way do this before we package the installer as an .iso file, in such a way that it will work in both Legacy and UEFI systems? 

Thanks!

---

### Post by oldfred on 2014-04-25
I was thinking flash drive with partitions.

But how UEFI and BIOS work with DVD, I do not know about. I have not used a DVD for installing for several years.

---

### Post by dvdlmnzr on 2014-04-25
Oh okay. Thanks for your help!

---

