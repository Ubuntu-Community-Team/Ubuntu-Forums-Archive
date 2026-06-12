---
title: "Another Error 15 on install..."
date: 2008-04-25
forum: General Help
---

### Post by m4cph1sto on 2008-04-25
I'm installing Kubuntu KDE4 using Wubi.  I'm installing on my E: drive, which is a separate, empty physical hard drive with a single partition, Disk 1 according to Vista.  I start Wubi in Vista, reboot, the installation runs fine (goes through what I believe is the entire process), then it automatically reboots, I select Kubuntu from the boot menu, and get this:

booting 'ubuntu 8.04, kernel 2.6.24-16-generic'

filesystem type is ntfs, partition type 0x7
kernel /boot/vmlinuz-2.6.24-16-generic root=uuid=2e22bd0519b701a6 loop=ubuntu/disks/root.disk ro quiet splash

error 15: file not found

I boot back into Vista, go to edit e:\ubuntu\disks\boot\grub\menu.lst.  I see that it has root pointing to (hd1,0)\ubuntu\disks, which should be correct, since my E: drive is "disk 1".  Why am I getting Error 15?

Thanks if anyone can help...

---

### Post by ago on 2008-04-25
[https://wiki.ubuntu.com/WubiGuide#head-281e2c55090fcd96336e6fe3029fec5aede1a230](https://wiki.ubuntu.com/WubiGuide#head-281e2c55090fcd96336e6fe3029fec5aede1a230)

---

### Post by m4cph1sto on 2008-04-25
Another piece to the puzzle: after getting the Error 15, I can press any key to get into the Grub boot menu, which lists all my installed operating systems (Ubuntu, XP32, XP64, and Vista32).  However, if I select any of the Windows installations, I get an error like "NTLDR not found".  To me this means either Grub is not seeing the partitions, or the files are missing.  But the Windows bootloader works fine, so the files must be there.  Grub must not be seeing my various drives/partitions, or not looking in the right place.  But in menu.lst, all the drives/partitions are listed correctly with each OS.  I guess Grub is not seeing them, but I'm no expert so I can't figure this out on my own.  

I've read the installation guide.  I used the 8.04 desktop ISO.  My file system is not corrupt.  I'm not using RAID.  I can't install on my primary C: Windows partition because I don't have enough free disk space.

---

### Post by ago on 2008-04-25
try different values for (hdX
drive 1 by the way is (hd0 but it is difficult to guess
you can use the cat command in the grub shell and tab expansion to see the content of the drive

cat (hd0,[hit tab]

---

### Post by killingdjef on 2008-04-25
I'm having the -exact- same problem as mcph1sto. I've reinstalled Ubuntu already 5 times from Windows, trying different disks but with no luck. Booting from the Live CD works though but I'm affraid installing Ubuntu from the Live CD will destroy my windows bootloader.

To sum it up, i'm getting this message after Wubi asks me to restart:

"booting 'ubuntu 8.04, kernel 2.6.24-16-generic'

filesystem type is ntfs, partition type 0x7
kernel /boot/vmlinuz-2.6.24-16-generic root=uuid=2e22bd0519b701a6 loop=ubuntu/disks/root.disk ro quiet splash

error 15: file not found"

When I do the "cat (hd0,[hit tab]" command in GRUB I see 2 partitions (NTFS) named 0 and 4. Back in Windows I've changed my GROOT to (hd0,0) (initial value) and (hd0,4) but both don't seem to make Ubuntu run. My hd is disk 0 according to Windows.

I have no clue what to do. Still looking forward to testing Ubuntu and see if it can replace my Windows :)

---

### Post by ago on 2008-04-25
> **killingdjef said:**
> but I'm affraid installing Ubuntu from the Live CD will destroy my windows bootloader.
The full installation via CD will overwrite the bootloader so that it points to Grub. Grub will have a menu item to launch the windows bootloader. So it's not the end of the world, in fact it's quite safe and you end up with a better bootloader...

> When I do the "cat (hd0,[hit tab]" command in GRUB I see 2 partitions (NTFS) named 0 and 4. Back in Windows I've changed my GROOT to (hd0,0) (initial value) and (hd0,4) but both don't seem to make Ubuntu run. My hd is disk 0 according to Windows.
It's more likely that it is the first number you have to change and not the second one

---

### Post by killingdjef on 2008-04-25
Thank you for your reply.

Thanks to this post [http://ubuntuforums.org/showpost.php?p=4587202&postcount=9](http://ubuntuforums.org/showpost.php?p=4587202&postcount=9)

I figured out where the problem lied.

Apparantly, changing the GROOT in windows and rebooting into Grub didn't work. I came to that conclusion because in GRUB the GROOT defined was (hd3,0) while in windows I specified (hd0,0). So for some reason, changes in that file aren't taken into account.

Manually editing the commandline worked like a charm.

---

### Post by m4cph1sto on 2008-04-30
I solved this problem by editing menu.lst to point to hd2,0 (seems random to me but fine as long as it works!).  Thanks to everyone for the help.

---

### Post by ago on 2008-04-30
You can simply remove everything in parenthesis.

root (hdX,Y)/ubuntu/disks

becomes

root ()/ubuntu/disks

Same thing for #groot

---

### Post by digitalggs on 2008-07-13
> **killingdjef said:**
> 

To sum it up, i'm getting this message after Wubi asks me to restart:

"booting 'ubuntu 8.04, kernel 2.6.24-16-generic'

filesystem type is ntfs, partition type 0x7
kernel /boot/vmlinuz-2.6.24-16-generic root=uuid=2e22bd0519b701a6 loop=ubuntu/disks/root.disk ro quiet splash

error 15: file not found"

When I do the "cat (hd0,[hit tab]" command in GRUB I see 2 partitions (NTFS) named 0 and 4. Back in Windows I've changed my GROOT to (hd0,0) (initial value) and (hd0,4) but both don't seem to make Ubuntu run. My hd is disk 0 according to Windows.

I have no clue what to do. Still looking forward to testing Ubuntu and see if it can replace my Windows :)


Open the file ?:\ubuntu\disks\boot\grub\menu.lst (?= the drive you installed ubuntu to) in a text editor. Anything with a 'find and replace option. Notepad will do, but I much prefer Notepad++ (can find it at [http://portableapps.com](http://portableapps.com)).

After you open in viewer minimize it and open My Computer. and navigate to ?:\ubuntu\disks\boot. Look for a file named vmlinuz-2.6.24-##-generic, '##' will be an actual number and may not be 16 wich leads me to how to fix your problem.

Back to the text editor with menu.lst do a find and replace
find: vmlinuz-2.6.24-16-generic
replace with: vmlinuz-2.6.24-##-generic ('##' of course matching the file you found in prev step)


the version I had when I installed today was vmlinuz-2.6.24-19-generic.

---

