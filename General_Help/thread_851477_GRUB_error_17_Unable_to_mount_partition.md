---
title: "GRUB error 17: Unable to mount partition"
date: 2008-07-06
forum: General Help
---

### Post by stiansoftcore on 2008-07-06
This is my output on sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x37e737e7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12584   101080948+   7  HPFS/NTFS
/dev/sda2           12755       30401   141749527+   f  W95 Ext'd (LBA)
/dev/sda5           12756       24813    96855885    7  HPFS/NTFS
/dev/sda6           24814       27040    17888346   83  Linux
/dev/sda7           27162       30322    25390701    7  HPFS/NTFS
/dev/sda8           30323       30401      634536   82  Linux swap / Solaris


----------------------
I installed (tried to install) XP Pro, and my GRUB disappeared. I got it back using the wiki, but now there\s an error I cant solve by myself. Ubuntu won\t boot, XP wont boot, nothing will boot, it all just returns error 17: Unable to mount partition.
Any help? Thanks.

Sorry for typing errors, havent bothered configuring my keyboard on Live cd.

---

### Post by tyler_roach on 2008-07-06
When the ubuntu choice is highlighted on the Grub menu, hit "e", and tell me what you see. (you're gonna have to write it down by hand.)

---

### Post by stiansoftcore on 2008-07-07
ok. I couldn't see the end of the second line, didn't understand how to.

```

root (hd0,7)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=3e198c465b7a-4d7c (arrow pointing to the right)
```
If it's too hard to do this, I could always install xp again, and install Linux again. I don't have a lot of time on my hands the next days, and I need my pc :)

---

### Post by tyler_roach on 2008-07-07
OK, try doing that again, and deleting everything after "root=" , and making it read:

root=/dev/sda6

Then, I think you hit "b", or "Enter" and then "b" to boot.

If that doesn't work, there are several other things you could try, but the easiest thing to do may be just to reinstall.

---

### Post by tyler_roach on 2008-07-07
That is, edit "root" on the second line, not the first!

---

### Post by wolfen69 on 2008-07-07
we will need to see the menu.lst

boot to a live cd and go to /boot/grub/menu.lst (on the installed ubuntu partition)

post the output here

---

### Post by tyler_roach on 2008-07-07
> **wolfen69 said:**
> we will need to see the menu.lst

boot to a live cd and go to /boot/grub/menu.lst (on the installed ubuntu partition)

post the output here

You don't have to boot into the OS to see the contents of menu.lst. He already posted the relevant part. :-)

---

### Post by Dizzle7677 on 2008-07-07
> **stiansoftcore said:**
> This is my output on sudo fdisk -l
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12584   101080948+   7  HPFS/NTFS
/dev/sda2           12755       30401   141749527+   f  W95 Ext'd (LBA)
/dev/sda5           12756       24813    96855885    7  HPFS/NTFS
/dev/sda6           24814       27040    17888346   83  Linux
/dev/sda7           27162       30322    25390701    7  HPFS/NTFS
/dev/sda8           30323       30401      634536   82  Linux swap / Swap
I installed (tried to install) XP Pro, and my GRUB disappeared.

  If you installed XP over Ubuntu you probably just overwrote the MBR of the root/boot partition. In the terminal do 'grub --help' and look in the man grub pages for help.
  The basic commands in GRUB are: Navigate to /boot/grub first.
    setup (hd0,6) [ex./dev/sda6] -should get some output/writing sectors,etc.
    root  (hd0,6) [ex./dev/sda6] -not sure if this would be just hd0 or hd0,6.

  Think of making a separate ext3 /boot partition say of 100 MB if possible.

---

### Post by stiansoftcore on 2008-07-07
> **Dizzle7677 said:**
> If you installed XP over Ubuntu you probably just overwrote the MBR of the root/boot partition. In the terminal do 'grub --help' and look in the man grub pages for help.
  The basic commands in GRUB are: Navigate to /boot/grub first.
    setup (hd0,6) [ex./dev/sda6] -should get some output/writing sectors,etc.
    root  (hd0,6) [ex./dev/sda6] -not sure if this would be just hd0 or hd0,6.

  Think of making a separate ext3 /boot partition say of 100 MB if possible.

and how would I create a partition like that? Thaks for the help, guys. I installed XP Pro, but cant find my driver cds, including ethernet, so no net in xp. Thank god ubuntu live cd is so great out of the box.
```

grub> find /boot/grub/stage1
 (hd0,5)

grub> setup (hd0,6) 

Error 12: Invalid device requested

grub> setup (hd0,6)

Error 12: Invalid device requested

grub> setup (hd0) 

Error 12: Invalid device requested
```
What about this? Why the hell does ms have to ruin everything? Pisses me off sometimes.

---

### Post by stiansoftcore on 2008-07-07
Please? Im kind of in a hurry, and i need some files on my Ubuntu installation before tomorrow :)

---

### Post by stiansoftcore on 2008-07-08
bump

---

