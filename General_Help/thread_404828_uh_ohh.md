---
title: "uh ohh"
date: 2007-04-08
forum: General Help
---

### Post by CadMasterAdam on 2007-04-08
Okay so i hade Vista Home installed then i stick in my Ubtuntu 6.06 disk and do the install thing. i chose to resize my partition and give it 80Gigs to use. with about 150 left for vista.

i remember basically just hitting next , its finished off its thing.

 but i still want to boot to vista (if i didn't screw it up) but there is no dual boot thing where i can chose.

is there anything that i can do to confirm if my vista is still on. or my data?

---

### Post by scxtt on 2007-04-08
what is the output of **sudo fdisk -l**?

---

### Post by CadMasterAdam on 2007-04-09
cadmasteradam@cadmasteradam:~$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       11588    93080578+   7  HPFS/NTFS
/dev/sda2   *       11589       38156   213407460   83  Linux
/dev/sda3           38157       38913     6080602+   5  Extended
/dev/sda5           38157       38913     6080571   82  Linux swap / Solaris
cadmasteradam@cadmasteradam:~$

---

### Post by scxtt on 2007-04-09
you still have a NTFS partition [ /dev/sda1 ] - so windows should still be there ...

when grub starts up, after your computer has booted - do you see something that tells you to hit escape for a menu?  i'm guessing it has set **hiddenmenu** and boots ubuntu by default ...

also, post the output from **cat /boot/grub/menu.lst** ...

---

### Post by hikaricore on 2007-04-09
**/dev/sda1 1 11588 93080578+ 7 HPFS/NTFS**

It looks like Vista is still there.  There are known issues with the grub bootloader and Vista.

I don't have any other info about this, just giving my 2 cents.

---

### Post by CadMasterAdam on 2007-04-09
thanks scxtt (love ATHF)

when i do hit ESc to goto boot menu Vista isn't there. i did this when i have XP and it worked then that i saw "microsoft Windows XP Pro" as a boot option.  so hopefully the problem is with grub, and Vista is still OK fyi hear is my menu.lst:

[B]cadmasteradam@cadmasteradam:~$ cat /boot/grub/menu.lst




/snip
title           Ubuntu, kernel 2.6.15-28-386
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.15-28-386 root=/dev/sda2 ro quiet splash
initrd          /boot/initrd.img-2.6.15-28-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-28-386 (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.15-28-386 root=/dev/sda2 ro single
initrd          /boot/initrd.img-2.6.15-28-386
boot

title           Ubuntu, kernel 2.6.15-23-386
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.15-23-386 root=/dev/sda2 ro quiet splash
initrd          /boot/initrd.img-2.6.15-23-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.15-23-386 root=/dev/sda2 ro single
initrd          /boot/initrd.img-2.6.15-23-386
boot

title           Ubuntu, memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin
boot
/snip


cadmasteradam@cadmasteradam:~$
[/B]

---

### Post by CadMasterAdam on 2007-04-09
do i need to add something like

[B]title            Vista
rootnoverify     (hd0,1) 
savedefault
makeactive
chainloader      +1[/B]

to the end of menu.lst

---

### Post by CadMasterAdam on 2007-04-09
alright so it turns out that i needed to do 

[B]title Vista
rootnoverify (hd0,0)
savedefault
makeactive
chainloader +1[/B]

so now windows does the scrolling bar to show that its loading, but that is it. it doesn't go past that point.. same thing when i goto windows safemode, it just lists all the drivers its loading stops at the last one and just stays there.. 

any suggestions?

---

### Post by Outrunner on 2007-04-09
I'm not sure about this, but if you have the Vista disk, you might be able to do a Repair to your Vista install. I'm thinking that that might be helpful(don't get your hopes up though, I'm not sure)

---

### Post by scxtt on 2007-04-09
yeah, i don't own vista myself - so i've not had this problem (actually i haven't booted windows in almost 2 years) ... if it comes down to wiping grub in order to use the vista bootloader (which i think will be the case) - that should be ok, at least to get you into vista ...

you'd then be able to boot Ubuntu off some other media (floppy, if you have one, or a USB stick if your motherboard can boot off one) ... but DON'T wipe out your working grub yet since you can use the MBR on it for what i mentioned above ...

if floppy/usb an option for you?

---

