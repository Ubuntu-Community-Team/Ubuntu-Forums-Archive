---
title: "Error after Install - Error 15 File not found"
date: 2008-03-26
forum: General Help
---

### Post by SlyerNB on 2008-03-26
Hi all, finally trying ubuntu again on my newer computer but I can't get it to work :(

I used the latest Wubi installer (from last night) and Ubuntu 8.04 Beta.

I tried searching for an answer but I'm not really sure of the problem as I don't fully understand what step I'm at.

Here is the error message I'm getting:

> 
Booting 'Ubuntu hardy (development branch), kernel 2.6.24-12-generic'

Filesystem type is ntfs, partition type 0x7
kernel /boot/vmlinuz-2.6.24-12-generic root=UUID=04E441CDE441C222 loop=/ubuntu/disks/root.disk ro quiet splash

Error 15: File not found

Press any key to continue...

I've tried both the 32 and 64 bit versions and get the same error, it takes ~5mins to install after I install wubi/restart windows, then it says it needs to reboot, displays an error message below that saying the network manager failed.

Any help would be great!

Edit: Doh forgot the computer specs...

Vista 32bit
Evga 8800gts 640
Evga 680i motherboard
2x Seagate 500gb HDs (One is Vista, other is XP, no bootloader for it though I just make it the main HD if I need to boot to it (rarely!))
G15 keyboard
Creative X-FI Extreme Music

Edit2:

I also had to use the verbose mode for the install as the regular and even graphical safe mode just left me with a blank screen for awhile, the verbose mode seemed to work fine however.

---

### Post by ago on 2008-03-26
Do you have multiple disks?
If so edit c:\ubuntu\disks\boot\grub\menu.lst

there should be something like 

root (hd1,1)/ubuntu/disks

change the X in: 

(hdX,Y)

If X is 0 try 1 and if it is 1 try 0

---

### Post by SlyerNB on 2008-03-26
Thanks I'll try that. 

I just tried installing it to my 2nd hd but on reboot the bootloader didn't show, so just reinstalled on the main drive and going to reboot.

---

### Post by SlyerNB on 2008-03-26
Ok that worked (no error), but now its sitting at a pure black screen, which is what I saw when doing the non-verbose install.... can't tell if it working or not so any ideas on what I can try next?

Thanks for the help so far :)

Edit: Fixed it, I had to remove the splash screen and added noapic to the boot command.... guess its not liking my 8800gts?

---

### Post by TrajMag on 2008-03-28
I get the same error 15 but haven't gotten far enough in the original boot to get c:\ubuntu\disks\boot\grub\menu.lst. There is a meni.lst in \install \boot\grub.

Running W2K SP4
Two HD's c: NTFS
               d: fat32
1.8mHz Pentium 4
1 Mag Mem.

Tried the install from both disks.

Is it possible to get acopy of the installed menu.lst and copy it into c:\ubuntu\disks\boot\grub\?

A Noob but have been studing for almost a year and ready to get wet. Long history at the command line. No Fear.

---

### Post by ago on 2008-03-28
No need for command line, just open c:\ubuntu\disks\boot\grub\ in wordpad and wherever you see (hdX,Y) change X to 0 or 1. Then save and reboot.
That's a known bug [https://bugs.launchpad.net/ubuntu/+source/grub/+bug/8497](https://bugs.launchpad.net/ubuntu/+source/grub/+bug/8497)

---

### Post by TrajMag on 2008-03-28
No problem with the text edit but there is no menu.lst in c:\ubuntu\disks\boot\grub. it only exists in c:\ubuntu\install \boot\grub where it appears to be a setup script for the first time boot. I figure it never gets past trying to find the file the first time.

I will take alook at the boot order in the Bios.

Said i was a noob.

---

### Post by ago on 2008-03-28
grub is setup to look for c:\ubuntu\disks\boot\grub\menu.lst and if that fails c:\ubuntu\install\boot\grub\menu.lst

It is normal for grub not to find disks\boot\grub\menu.lst on the first reboot and then load up the install one

It is strange that it does not find c:\ubuntu\install\boot\grub\menu.lst

If it does not find it, use the grub console and try to navigate using tab completion

configfile (hd[HIT TAB KEY]

---

### Post by TrajMag on 2008-03-28
Thanks, we'll give that a try this wekend.

---

### Post by digitalggs on 2008-07-13
> **SlyerNB said:**
> Booting 'Ubuntu hardy (development branch), kernel 2.6.24-12-generic'

Filesystem type is ntfs, partition type 0x7
kernel /boot/vmlinuz-2.6.24-12-generic root=UUID=04E441CDE441C222 loop=/ubuntu/disks/root.disk ro quiet splash

Error 15: File not found

Press any key to continue...


Open the file ?:\ubuntu\disks\boot\grub\menu.lst (?= the drive you installed ubuntu to) in a text editor. Anything with a 'find and replace option. Notepad will do, but I much prefer Notepad++ (can find it at [http://portableapps.com](http://portableapps.com)).

After you open in viewer minimize it and open My Computer. and navigate to ?:\ubuntu\disks\boot. Look for a file named vmlinuz-2.6.24-##-generic, '##' will be an actual number and may not be 16 wich leads me to how to fix your problem.

Back to the text editor with menu.lst do a find and replace
find: vmlinuz-2.6.24-16-generic
replace with: vmlinuz-2.6.24-##-generic ('##' of course matching the file you found in prev step)


the version I had when I installed today was vmlinuz-2.6.24-19-generic.

---

