---
title: "Cannot remove BURG"
date: 2015-03-14
forum: General Help
---

### Post by michael1964 on 2015-03-14
I was playing around with customizing GRUB but wasn't happy with the results, so I tried BURG before I realized it only work with a BIOS (my laptop is UEFI). I removed BURG using the purge option with apt-get, but now when I try to open Grub Customizer I get this message:

Burg Found!
Do you want to configure BURG instead of Grub2?

I manually deleted any BURG files and directories that I could find but can't get rid of this message. Any ideas what might be causing Grub Customizer to still think that BURG is around?

---

### Post by oldfred on 2015-03-15
I think both Burg & Grub Customizer create their own versions of grub2's scripts. 
Post this:

ls -lha /etc/grub.d

And the easier way to fix it may be just a total uninstall/reinstall of grub including copy/rename current grub script file /etc/grub.d, so you get all new scripts. 
If you have customized things you may have to redo them though.

---

### Post by michael1964 on 2015-03-15
I got this:

drwxr-xr-x   3 root root 4.0K Mar 14 22:08 .
drwxr-xr-x 149 root root  12K Mar 14 22:08 ..
-rwxr-xr-x   1 root root 9.3K Apr 11  2014 00_header
-rwxr-xr-x   1 root root 6.0K Apr 10  2014 05_debian_theme
-rwxr-xr-x   1 root root  12K Apr 11  2014 10_linux
-rwxr-xr-x   1 root root  11K Apr 11  2014 20_linux_xen
-rwxr-xr-x   1 root root 2.0K Mar 12  2014 20_memtest86+
-rwxr-xr-x   1 root root  12K Apr 11  2014 30_os-prober
-rwxr-xr-x   1 root root 1.4K Apr 11  2014 30_uefi-firmware
-rwxr-xr-x   1 root root  214 Oct 10  2013 40_custom
-rwxr-xr-x   1 root root  216 Oct 10  2013 41_custom
drwxr-xr-x   4 root root 4.0K Mar 14 14:43 backup
-rw-r--r--   1 root root  483 Oct 10  2013 README
-rw-r--r--   1 root root    0 Mar 14 22:08 .script_sources.txt

I have searched a few of the config files for a reference to burg but can't find anything, but I didn't run burg to configure anything so I'd be surprised if I find anything.

I'm just puzzling over what Grub Customizer is finding to think that burg is installed.

---

### Post by oldfred on 2015-03-16
Looks mostly like standard scripts.

What is in backup folder and what is in .script_sources.txt. 
Have not seen those.

You can run Boot-Repair and just look at or post the link it gives for its summary report. That shows just about everything related to booting.
       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by michael1964 on 2015-03-16
Here's the link: [http://paste.ubuntu.com/10613094/](http://paste.ubuntu.com/10613094/)

I didn't paste the contents here as it's pretty long.

backup directory has copies of grub files and .script_sources.txt is an empty file.

---

### Post by oldfred on 2015-03-17
Script did not find any brug references.

But that you have backup grub scripts is either from brug or Grub customizer. And I thought grub customizer changed the names slightly of the scripts. So those scripts may be from burg?

I would just use Boot-Repair to run the total uninstall/reinstall of grub. Rename the folder with the grub scripts and it will install all new ones with the new full reinstall of grub.

Did you run Boot-Repair previously to get system to boot?
You have this file which old versions of Boot-Repair created:
 /EFI/Microsoft/Boot/bkpbootmgfw.efi

That was because grub2's os-prober could not correctly create entries for Windows and some computers would only boot the Windows entry so it renamed grub also to be Windows.

---

### Post by michael1964 on 2015-03-20
I renamed the backup directory then ran the grub configuration tool and it still asked if I wanted to configure burg or grub. I'm thinking that it's not something that it finds in the grub.d directory.

Right now I might explore other options than boot repair as booting is fine and it's just an annoying message. I'll do some more digging, but really not sure what is being found as I did a purge of burg and anything else that was installed (or at least anything that I was aware of).

If anyone knows of a list of items I should have purged for burg I could try those again.

Thanks for all the help so far guys.

---

### Post by michael1964 on 2015-03-25
OK, so I completely uninstalled grub, removed all config folders and reinstalled. Guess what? Grub customizer STILL thinks that burg is installed.

I can only guess that grub customizer is finding something that is not in the /boot directory...

---

### Post by michael1964 on 2015-03-29
Just wondering - does anyone know of any other locations than /boot where burg might write config files or leave some remnants of an installation?

---

### Post by oldfred on 2015-03-29
You also had EasyBCD with this which may be the old grub4dos. What entries does it have.

/NST/menu.lst

---

### Post by michael1964 on 2015-03-29
> **oldfred said:**
> You also had EasyBCD with this which may be the old grub4dos. What entries does it have.

/NST/menu.lst

It contains this:

> # NeoSmart NeoGrub Bootloader Configuration File 
# 
# This is the NeoGrub configuration file, and should be located at C:\NST\menu.lst 
# Please see the EasyBCD Documentation for information on how to create/modify entries: 
# [http://neosmart.net/wiki/display/EBCD/](http://neosmart.net/wiki/display/EBCD/) 
 
title Ubuntu 
root (hd0,6) 
kernel /boot/vmlinuz-3.8.0-26-generic root=/dev/sda7 ro quiet splash 
initrd /boot/initrd.img-3.8.0-26-generic 
boot

But I'm not sure that's the problem as I used that quite some time back and uninstalled it; but this problem only came about when I tried to install burg a considerable amount of time later.

---

### Post by oldfred on 2015-03-29
That was my last gasp at where something maybe hidden.

Not sure what else to suggest. Do not know anything about grub customizer so cannot tell what it may be looking at. I prefer to manually change grub configurations, but it does take some learning effort and those looking for something quick often use Grub Customizer.

---

### Post by michael1964 on 2015-03-31
I really don't know where to look either, and I can't find anything in any of the config files that helps me out.

Oh well, I can live with the message I guess. Not sure what else I can do.

---

### Post by dcstar on 2015-04-05
> **michael1964 said:**
> I really don't know where to look either, and I can't find anything in any of the config files that helps me out.

Oh well, I can live with the message I guess. Not sure what else I can do.

Manually remove the /etc/burg.d folder and any /etc/default/burg files.

---

