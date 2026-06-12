---
title: "Wine can access windows installation?"
date: 2006-11-20
forum: General Help
---

### Post by olieviya on 2006-11-20
Basically the title: Can you use wine to access your already present windows installation?

In my case a winXP installation on an ntfs partition...

---

### Post by musicinmybrain on 2006-11-20
Sort of.

[This link]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only") shows how to mount and access your Windows partition from Linux.

Note that those instructions mount it read-only.

NTFS read/write support has made much progress lately, and it is now possible (see lower on the linked page) but not considered entirely "safe".

Assuming you have mounted your Windows partition read-only, then you should be able to run some programs from that partition in wine. This assumes they are self-contained and don't need to write back to disk. Even if you use the beta driver to enable read/write access, the programs may have trouble if they need to access the registry or other system files. There may be a configuration that makes this possible; I don't know wine well enough to say.

So, yes, it's possible in a limited sense. However, you may find it simpler to install the programs you want by running the installers in wine; this will install them to ~/.wine/drive_c/. Or, for many programs, running them from a shared FAT32 or [ext3]("http://www.fs-driver.org/") partition will work.

---

### Post by olieviya on 2006-11-20
> **musicinmybrain said:**
> Sort of.

[This link]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only") shows how to mount and access your Windows partition from Linux.

Note that those instructions mount it read-only.

NTFS read/write support has made much progress lately, and it is now possible (see lower on the linked page) but not considered entirely "safe".

Assuming you have mounted your Windows partition read-only, then you should be able to run some programs from that partition in wine. This assumes they are self-contained and don't need to write back to disk. Even if you use the beta driver to enable read/write access, the programs may have trouble if they need to access the registry or other system files. There may be a configuration that makes this possible; I don't know wine well enough to say.

So, yes, it's possible in a limited sense. However, you may find it simpler to install the programs you want by running the installers in wine; this will install them to ~/.wine/drive_c/. Or, for many programs, running them from a shared FAT32 or [ext3]("http://www.fs-driver.org/") partition will work.
Thanks, what i really want is to play win-only games from Linux and use PS and access some files

Why does it say? mount: special device /dev/hda1 does not exist



PS: I have a 250gb FAT external disk which I will use for shared stuff.

---

### Post by musicinmybrain on 2006-11-20
> **olieviya said:**
> Why does it say? mount: special device /dev/hda1 does not exist

Make sure you're trying to mount your Windows partition and not, as it appears, your swap partition. Try using the following command:

```
sudo fdisk -l | grep NTFS
```

That should return the correct device corresponding to your Windows partition.

---

### Post by olieviya on 2006-11-22
> **musicinmybrain said:**
> Make sure you're trying to mount your Windows partition and not, as it appears, your swap partition. Try using the following command:

```
sudo fdisk -l | grep NTFS
```

That should return the correct device corresponding to your Windows partition.

Oh, cheers, is was sda1 instead of hda1, do you have any idea why Photoshop doesnt work? It loads up and then says invalid user name or something like that...

---

### Post by musicinmybrain on 2006-11-22
> **olieviya said:**
> Oh, cheers, is was sda1 instead of hda1, do you have any idea why Photoshop doesnt work? It loads up and then says invalid user name or something like that...

sda1? Really? That's your external disk. **edit:** assuming (pretty safely, but still perhaps incorrectly) that you don't have any internal SCSI disks

Odd.

[The Wine AppDB]("http://appdb.winehq.org/appview.php?iVersionId=1815") can give you an idea of whether and how well a program might work on Wine. You can also look for known bugs. However, something as complex as Photoshop, if it does work under Wine, is likely to require installing under Wine rather than simply running off the Windows partition.

---

### Post by olieviya on 2006-11-22
> **musicinmybrain said:**
> sda1? Really? That's your external disk. **edit:** assuming (pretty safely, but still perhaps incorrectly) that you don't have any internal SCSI disks

Odd.

[The Wine AppDB]("http://appdb.winehq.org/appview.php?iVersionId=1815") can give you an idea of whether and how well a program might work on Wine. You can also look for known bugs. However, something as complex as Photoshop, if it does work under Wine, is likely to require installing under Wine rather than simply running off the Windows partition.

But windows isn't on an external disk... Windows is on the same physical disk as Linux... :-k 

It works though so what have I done? :confused: 

Thanks for the link - will read.

---

### Post by CatKiller on 2006-11-22
> **musicinmybrain said:**
> sda1? Really? That's your external disk. **edit:** assuming (pretty safely, but still perhaps incorrectly) that you don't have any internal SCSI disks

Odd.

SATA drives also count as sd*xn*.

---

### Post by musicinmybrain on 2006-11-22
> **CatKiller said:**
> SATA drives also count as sd*xn*.

Aha! I had forgotten. Y'all and your newfangled hardware. ;)

---

### Post by olieviya on 2006-11-23
> **CatKiller said:**
> SATA drives also count as sd*xn*.

SATA is what I have :)

What is it anyway....? (going to wikipedia to check :P)

---

