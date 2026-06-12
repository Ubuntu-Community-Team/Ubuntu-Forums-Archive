---
title: "Clonezilla Restore Ubuntu Backup on larger SSD"
date: 2022-05-30
forum: General Help
---

### Post by Sandi1987 on 2022-05-30
Is it possible to restore backup with Clonezilla on larger SSD or it's need to be the same SSD size?

---

### Post by tea for one on 2022-05-30
> The destination partition must be equal or larger than the source one
Taken from [https://clonezilla.org/](https://clonezilla.org/) - Scroll down to Limitations

---

### Post by sudodus on 2022-05-30
- With an MSDOS partition table, the answer above is certainly clear enough: OK to restore to a larger drive.

- With a GUID partition table, GPT, I was not sure if it is enough. You can restore the partitions to a larger drive, but a backup partition table must also be created at the tail end of the drive.

Now I know that current versions of Clonezilla is doing this automatically. So you need not do it yourself, manually with gdisk or with the shellscript [gpt-fix](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS/stable-alternative#gpt-fix) (that uses gdisk). Anyway, it is a minor fix, that might be necessary when using other cloning tools, for example dd.

[hr][/hr]
Finally you should also edit the partition table in order to use the whole new drive, and you can do that with gparted.

---

### Post by tea for one on 2022-05-30
> **sudodus said:**
> With a GUID partition table, GPT, I am not sure if it is enough. You can restore the partitions to a larger drive, but a backup partition table must also be created at the tail end of the drive. I am not sure if current versions of Clonezilla is doing this automatically,

That's an interesting comment and it has never even occurred to me that there may be a dilemma.
> Both MBR and GPT partition formats of hard drive are supported. Clonezilla live also can be booted on a BIOS or uEFI machine
The above is mentioned in Features on the Clonezilla Home page.

I would think that:-
Clones using images would include the GPT
Device to Device clone using an entire disk would use the existing GPT and it must be fine.
Device to Device using partitions - you have to prepare the destination partitions in advance so you would create your GPT during the advance partition allocation.

@sudodus -  Is the option [COLOR="#0000FF"]Device to Device using partitions[/COLOR] the area of concern?

---

### Post by sudodus on 2022-05-30
@ tea for one,

It looks good. So probably Clonezilla has fixed it for GPT :-)

It is worth testing in order to be sure. (So far I have only had to restore Clonezilla backups of MSDOS partition tables.)

I think only images or clones of the whole drive are relevant here. Otherwise (with images or clones of partitions) you have to fix things anyway.

---

### Post by tea for one on 2022-05-30
On rainy winter afternoons, I've amused myself by playing with Clonezilla.
I only have UEFI with GPT installations and so far, I've cloned and restored successfully via all three options mentioned in my post 4.

I'm still surprised when I've cloned an installed Ubuntu 22.04 OS (inc Gnome) to a USB stick and then booted the same stick on older, lower specification PC.
50% due to Clonezilla and 50% due to the robust structure of Ubuntu?

---

### Post by sudodus on 2022-05-30
I'm testing right now, directly cloning a small SSD with GPT and Lubuntu 22.04 LTS for UEFI mode with Clonezilla to a bigger drive ... and yes, Clonezilla works correctly. The GPT is good according to gdisk (which includes checking that there is a correct backup partition table at the tail end of the drive) and Lubuntu works as it should also in the cloned copy :-)

So we need not worry about current versions of Clonezilla.

mkusb is also fixing the backup partition table when cloning image files or compressed image files. But if we use raw cloning with dd or similar tools, the backup partition table at the tail end of the drive must be fixed.

---

