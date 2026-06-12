---
title: "Can't boot into windows from GRUB"
date: 2007-02-25
forum: General Help
---

### Post by tomzx on 2007-02-25
I recently installed VISTA which overwrote GRUB (so it was loading from VISTA) and I wanted to get back onto Ubuntu. The problem was that I could not see the GRUB menu anymore so I decided to recover it using the live cd and using recovery mode to reinstall grub. It went ok but when I got to the point to try and get back on XP, I could simply not.

In the recovery mode of the live cd, when I was asked where I wanted to install grub I wrote (hd0). I noticed that the action I had done had cut my first partition into two so it could install GRUB there.

The problem though is that now my NTFS partition which was under XP turned into a W95 extended (LBA) one which I cannot mount nor start from. I wish to keep the data on that partition so is there any way to remove the GRUB partition and get things like they were before?

Here's the result of fdisk -l

/dev/sda1   *           1        9561    76798701    7  HPFS/NTFS
**/dev/sda2            9562       48641   313910100    f  W95 Extended (LBA)**
/dev/sda5            9562       40676   249931206    7  HPFS/NTFS
/dev/sda6   *       40677       41982    10490413+  83  Linux
/dev/sda7           41983       42113     1052226   82  Linux swap / Solaris
/dev/sda8           42114       48641    52436128+   7  HPFS/NTFS

The partition in bold is actually the one where all my stuff is but it seems like the partition list was corrupted or whatever since I cannot access it...

---

### Post by JohnPhys on 2007-02-25
Can you paste the entire output from fdisk -l?

Also, can you tell us exactly which partitions are doing what (where windows is installed, where ubuntu is, where a shared partition is, etc.)?

---

### Post by tomzx on 2007-02-25
Disque /dev/sda: 400.0 Go, 400088457216 octets
255 têtes, 63 secteurs/piste, 48641 cylindres
Unités = cylindres de 16065 * 512 = 8225280 octets

Périphérique Amorce    Début         Fin      Blocs    Id  Système
/dev/sda1   *           1        9561    76798701    7  HPFS/NTFS **-> Should be my Win XP partition**
/dev/sda2            9562       48641   313910100    f  W95 Etendu (LBA)** -> second part of Win XP**
/dev/sda5            9562       40676   249931206    7  HPFS/NTFS **-> A partition, my D: in Win XP**
/dev/sda6   *       40677       41982    10490413+  83  Linux** -> Ubuntu**
/dev/sda7           41983       42113     1052226   82  Linux swap / Solaris **-> Ubuntu Swap partition**
/dev/sda8           42114       48641    52436128+   7  HPFS/NTFS** -> My Vista partition**

---

### Post by rsambuca on 2007-02-25
After you have installed Vista, it takes over the XP bootloader too.  Therefore in grub you usually just see your ubuntu selections, as well as one that says Windows Vista Longhorn loader.  Once you select that, then you have another bootloader screen asking you to select between Vista and an "Earlier Version of Windows".

---

### Post by tomzx on 2007-02-25
> **rsambuca said:**
> After you have installed Vista, it takes over the XP bootloader too.  Therefore in grub you usually just see your ubuntu selections, as well as one that says Windows Vista Longhorn loader.  Once you select that, then you have another bootloader screen asking you to select between Vista and an "Earlier Version of Windows".

I didn't have the option to view GRUB. I only had the "bootloader screen asking you to select between Vista and an "Earlier Version of Windows""

---

### Post by rsambuca on 2007-02-25
Just for my clarity - from this Vista Bootloader, can you select Vista and does it load?  Does XP load, and if not, what happens when you select it.

What instructions did you follow when you tried to reinstall grub from the liveCD?

---

### Post by tomzx on 2007-02-25
The Vista bootloader is not accessible anymore as GRUB has taken over.

I now only have access to GRUB and in the list, I can see Win XP but when I boot it I get an error message and it simply doesn't load. I can only boot into Ubuntu.

---

### Post by rsambuca on 2007-02-25
What is the specific error message that grub is giving you?  error 21?

---

### Post by tomzx on 2007-02-25
Error 12: Invalid device requested

When I try to boot from hd0,0 I get 
Starting up...
GRUB

nothing more.

---

