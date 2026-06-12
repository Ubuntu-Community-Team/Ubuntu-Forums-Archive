---
title: "help with installing the latest kernel for a live instance"
date: 2015-10-22
forum: General Help
---

### Post by leo_remick on 2015-10-22
Greetings,

        I have been working on a custom **live** remix of **xubuntu 14.04** and have successfully created several working images up to this point. The process I have been using is mounting the image and extracting and altering the contents. Lately I have been trying to **install kernel 4.0.0-040000**. after extracting the image I chroot in and install  the kernel .deb packages then move the boot/vmlinuz and boot/initrd.img to the base image "casper" directory and rename to vmlinuz.efi and decompress the initrd then package it using cpio and lzma to initrd.lz. After all that and creating the new squashfs I generate the iso. **Then we come to the problem...** I try to boot the live distribution and after a few seconds I get the error "**/cow format specified as aufs and no support found**" and I end up at the initramfs console and the boot process ceases. I have searched the error (not many returns from the query) and they mostly seem from mint from ranging issues. Not sure if its a kernel issue, casper issue, or maybe I missed a config somewhere? Any help would be greatly appreciated. 

Thanks,
Leo

---

### Post by leo_remick on 2015-11-06
The title should read **"installing new kernel for custom iso"** sorry...
[B][I][Note] The error I was experiencing was because the kernel modules in /lib/modules/${YOR_CUSTOM_KERNEL} need to be located in the initial ramdisk for live sessions (which I explain below).
[/I][/B]
I thought the Ubuntu community is what made the distribution great. I haven't received a lick of help from the community in the form of pointers, tips, or even a reply. Regardless, I solved the issue and have returned to update my original post.

follow a guide such as [this]("https://help.ubuntu.com/community/LiveCDCustomization") and you should have 2 directories from the ISO ${EXTRACTED_IMAGE_CONTENTS_DIRECTORY} and ${UNSQUASHED_FILESYSTEM}

Now for the custom kernel and installation
First of all when compiling the custom kernel I made sure I enabled support for...
 1. general settings > initramfs support
2. filesystems > misc filesystems > squashfs4.0
3. filesystems > misc filesystems > UFS (union)
4. device drivers > block devices > compressed ram block device support
5. device drivers > block devices > loopback device support

then compile and install the kernel to the ${UNSQUASHED_FILESYSTEM} and move boot/initrd.img-XXXX and boot/vmlinuz-XXXX to your ${EXTRACTED_IMAGE_CONTENTS_DIRECTORY}/casper and rename them to just "initrd.gz" and "vmlinuz"

1. then decompress the initial ramdisk with the archive tool
2. which will produce a cpio compressed file and decompress it with the archive tool
3. copy ${UNSQUASHED_FILESYSTEM}/lib/modules/${YOR_CUSTOM_KERNEL}/*         --to-->    
    ${EXTRACTED_IMAGE_CONTENTS_DIRECTORY}/casper/${DECOMPRESSED_INITRD}/lib/modules/${YOR_CUSTOM_KERNEL}

compress the initrd
4. cd ${EXTRACTED_IMAGE_CONTENTS_DIRECTORY}/casper/${DECOMPRESSED_INITRD}
5. find . | cpio --quiet --dereference -o -H newc | lzma -7 > ../initrd.lz

And thats it for installing a custom kernel to the ubuntu iso

---

### Post by leo_remick on 2015-11-12
P.S.
How do I get this thread marked "solved"? Thanks.

---

### Post by bapoumba on 2015-11-12
> **leo_remick said:**
> P.S.
How do I get this thread marked "solved"? Thanks.
Under Thread Tools :)

---

### Post by leo_remick on 2015-11-13
Sweet... thanks.

---

