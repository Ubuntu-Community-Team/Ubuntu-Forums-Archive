---
title: "Ubuntu won't start"
date: 2008-02-21
forum: General Help
---

### Post by Ledin on 2008-02-21
I don't known if is the right place to post this but when I restarted my computer today it wouldn't start and gave me the following error message
[15,298705] Kernel Panic-not syncing: VFS: unable to mount root FS on unknown  -Block (0,0)

if anyone can help me solve this problem that would be appreciated.

---

### Post by deepclutch on 2008-02-21
^initrd.img is not found.check and make sure in menu.lst(/boot/grub/) that in title Ubuntu, a kernel line,followed by initrd path is given.

if above things are correct,chances are that ur initrd.img is corrupt.generate a new initrd image by mounting and chrooting in hdd ubuntu installation and u can do it as dpkg-reconfigure linux-image-x-x

---

### Post by erginemr on 2008-02-21
> **deepclutch said:**
> ^initrd.img is not found.check and make sure in menu.lst(/boot/grub/) that in title Ubuntu, a kernel line,followed by initrd path is given.

if above things are correct,chances are that ur initrd.img is corrupt.generate a new initrd image by mounting and chrooting in hdd ubuntu installation and u can do it as dpkg-reconfigure linux-image-x-x

I also agree with you that this is probably an initrd-img problem, but if the OP is a Linux newbie, it will not be easy for him to find the correct hard drive to mount and chroot to it. 

If he is lucky, he may have a backup of the same file created before the corruption. So, let us try this trick first:

1. Boot from the Ubuntu Live CD. Select "Computer" from "Places" menu.

2. Find your real Ubuntu hard drive and double click to mount it.

3. Find the "/boot" directory inside. The problem is, you can see what is inside, but cannot make any changes. So, we need to open it as root.

4. Right-click on the folder icon and select "open with other application...". Inside the dialog, select use a custom command and write "gksu nautilus". 

5. Now you should be able to change the names. The corrupted file is initrd-img-<version_name>. You are lucky if you have a back-up of the file as initrd-img-<version_name>**.bak**. If so, rename the corrupted file to initrd-img-<version_name>**.orig**, and initrd-img-<version_name>**.bak** file to initrd-img-<version_name>.

6. Close the new nautilus window. Press the "Computer" icon from the toolbar of the original window to show the hard drives again, right click on your drive and select "unmount".

7. Restart your computer without the Live CD.

Come back for more, if you don't happen to have a back-up initrd-img file. Then, we shall try to help you chroot in your hard drive from the Live CD, bu this will not be for the faint of heart.

---

