---
title: "Unable to update grub"
date: 2012-12-26
forum: General Help
---

### Post by Impavidus on 2012-12-26
Hi,
I've got a grub related problem.
```

egroot@Cassiopeia:~$ ls -l /boot/grub/menu.lst
-rw-r--r-- 1 root root 5144 dec 26 11:55 /boot/grub/menu.lst
egroot@Cassiopeia:~$ sudo update-grub
[sudo] password for egroot: 
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-3.2.0-35-generic
Found kernel: /boot/vmlinuz-3.2.0-34-generic
Found kernel: /boot/vmlinuz-3.2.0-33-generic
Found kernel: /boot/vmlinuz-3.2.0-32-generic
Found kernel: /boot/vmlinuz-2.6.32-44-386
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

egroot@Cassiopeia:~$ ls -l /boot/grub/menu.lst
-rw-r--r-- 1 root root 5144 dec 26 12:11 /boot/grub/menu.lst
egroot@Cassiopeia:~$ cat /boot/grub/menu.lst
# menu.lst - See: grub(8), info grub, update-grub(8)

# (skipping some irrelevant stuff)

## ## End Default Options ##

title        Ubuntu 12.04.1 LTS, kernel 3.2.0-32-generic
root        (hd0,2)
kernel        /boot/vmlinuz-3.2.0-32-generic root=UUID=75805a10-c085-4f8f-9197-e72f5926910e ro splash 
initrd        /boot/initrd.img-3.2.0-32-generic

title        Ubuntu 12.04.1 LTS, kernel 3.2.0-32-generic (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-3.2.0-32-generic root=UUID=75805a10-c085-4f8f-9197-e72f5926910e ro  single
initrd        /boot/initrd.img-3.2.0-32-generic

title        Ubuntu 12.04.1 LTS, kernel 2.6.32-44-386
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.32-44-386 root=UUID=75805a10-c085-4f8f-9197-e72f5926910e ro splash 
initrd        /boot/initrd.img-2.6.32-44-386

title        Ubuntu 12.04.1 LTS, kernel 2.6.32-44-386 (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.32-44-386 root=UUID=75805a10-c085-4f8f-9197-e72f5926910e ro  single
initrd        /boot/initrd.img-2.6.32-44-386

title        Ubuntu 12.04.1 LTS, memtest86+
root        (hd0,2)
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
root        (hd0,0)
savedefault
makeactive
chainloader    +1

```In other words, update-grub detects all installed kernels, rewrites /boot/grub/menu.lst but does not include the three latest kernels in the grub menu (and indeed, right now I'm using 3.2.0-32). According to synaptic, the following relevant packages are all installed:```

linux-image-2.6.32-44-386
linux-image-3.2.0-32-generic
linux-image-3.2.0-33-generic
linux-image-3.2.0-34-generic
linux-image-3.2.0-35-generic

```confirming the diagnostics from update-grub.

I may have to add this computer is running grub 0.97 and has had no fresh reinstall since dapper drake, but otherwise it's still working perfectly. It's now running 12.04 with the xfce desktop.

Have a nice midwinter full moon!

---

### Post by oldfred on 2012-12-26
I do not think Boot-Repair can fix issues with grub legacy. It does have options to do the uninstall of grub legacy and reinstall to grub2. But if yo ucan boot you can easily do that from command line.

But Boot-Repair runs the BootInfo report which lets us see your entire boot configuration. Post link. You can run from current install, Ubuntu liveCD/Flash or download a full repair ISO to install to flash drive.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by Impavidus on 2012-12-26
Here is the bootinfo report: [http://paste.ubuntu.com/1468006/](http://paste.ubuntu.com/1468006/)

---

### Post by Pjotr123 on 2012-12-26
You might upgrade to Grub 2. Grub 2 works fine and is tweakable as well.

How-to:

1. Grant yourself some rights:
```
sudo -i
```

2. Completely remove Grub 1:
```
apt-get update && apt-get purge grub-common
```

3. Use the Ubuntu-LiveCD of 12.04.1, to install Grub 2:
[https://sites.google.com/site/easylinuxtipsproject/grub#TOC-Repair-Grub-e.g.-because-the-Windows-DVD-has-overwritten-Grub-](https://sites.google.com/site/easylinuxtipsproject/grub#TOC-Repair-Grub-e.g.-because-the-Windows-DVD-has-overwritten-Grub-)

4. Reboot. You should see a basic Grub 2 menu now.

5. Make your Grub 2 menu better looking:
[https://sites.google.com/site/easylinuxtipsproject/beautifygrub](https://sites.google.com/site/easylinuxtipsproject/beautifygrub)

6. Zalig kerstfeest! :)

---

### Post by Impavidus on 2012-12-26
I may look into that tomorrow.

---

### Post by YannBuntu on 2012-12-26
hello
> **Impavidus said:**
> Here is the bootinfo report: [http://paste.ubuntu.com/1468006/](http://paste.ubuntu.com/1468006/)

```
64bits detected. Please use this software in a 64bits session. (Please use Ubuntu-Secure-Remix-64bit (www.sourceforge.net/p/ubuntu-secured) which contains a 64bits-compatible version of this software.) This will enable this feature.

```

Download Ubuntu-Secure-Remix-64bit, boot on it, choose "Try Ubuntu", and run Boot-Repair from it.

---

### Post by Impavidus on 2012-12-27
Will my machine be happy when I try running unity from a live dvd? I've got 1 GB of ram. That's why I use xfce (besides from liking it more). And although there is a 64 bit processor in it, it has only ever run 32 bit systems (not much advantage running a 64 bit system on that memory). The 64 bit CPU was probably put in there  because it sounds future-proof from an advertising point of view. The machine is eight years old.

---

### Post by Pjotr123 on 2012-12-27
> **Impavidus said:**
> Will my machine be happy when I try running unity from a live dvd? I've got 1 GB of ram. That's why I use xfce (besides from liking it more). And although there is a 64 bit processor in it, it has only ever run 32 bit systems (not much advantage running a 64 bit system on that memory). The 64 bit CPU was probably put in there  because it sounds future-proof from an advertising point of view. The machine is eight years old.

You can also use the Xubuntu LiveCD for a Grub upgrade. In fact, I even recommend it: it's lightweight and snappy. :)

---

### Post by Impavidus on 2013-01-04
Waited a few days to make up my mind (I'm fully aware of the fact that making up your mind happens subconsciously) and decided to install grub2. It now works again. Marking the thread as solved. I still don't know what went wrong, but I don't really care (another user may have done something strange).

---

