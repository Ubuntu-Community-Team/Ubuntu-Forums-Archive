---
title: "External hard disk partition suggestions"
date: 2007-08-22
forum: General Help
---

### Post by Man_Beach on 2007-08-22
I've just bought a 320 gb external (USB) hard disk which I want to use for backups, although it's possible that I might want to use it to swap files with my (Windows XP using) friend sometime in the future. It's formatted in NTFS at the moment which is no use to me as I only use Ubuntu or (very occasionally) Windows 98. It's far larger than I really need (I'm using less than 25GB of my hard disk), but it seemed silly paying just a few pounds less for a drive with a quarter of the capacity.

From reading the forums, I intend to use the gparted live CD to reformat it to EXT3 - but
a) is it worth splitting the drive up into smaller partitions?
b) is it worth putting a small (say) FAT32 partition on it to swap files with my friend?
c) is it worth keeping a small NTFS partition? Why should I want it?
d) Seagate very kindly put some files on the disk which I don't need - as I can't write to NTFS formatted disks, how do I get rid of them?

---

### Post by merlinus on 2007-08-22
d)  This will give you write privileges for ntfs from ubuntu.

Open a terminal and enter:

```

sudo apt-get install ntfs-config

```then:

```

sudo ntfs-config

```Tick the appropriate boxes and restart.

-merlin

---

### Post by Gary.M on 2007-08-22
My experience is you're better off with Ext-3. It automounts properly when used on an external usb drive. There are messages all over the forums about problems trying to automount usb NTFS drives. I'd make a small FAT32 partition as well for access from Windows.

---

### Post by bodhi.zazen on 2007-08-22
+1 on the small FAT

+1 on ext3

Be careful 'bout transfering files ubuntu- windows

scan them from windows for viruses

---

### Post by rhodry on 2007-08-22
Given that you  are not particularly sqeezed for space, I would leave the Seagate utils etc where they are. A lot of these drives have their drivers and utility software in these areas rather than providing a seperate cd. I just reduced the size of the partition they are on so that it was just a bit bigger than necessary to hold the existing files. The advantage of this is that you can plug the drive into any relevant Windows machine and be able to access the native drivers and utils for repair or setup or ???? .

I would then have an ntfs partition as your share area with your Windows mates. You can now write to such partitions with new linux utils. If you are not comfortable with that you can access it as a Samba share and that works fine.

Have the rest (probably a couple of hundred Gig still) as ext3 partition or partitions as your heart desires. I have 2 on a similarly sized disk. One I use to rotate monthly backups of my entire system (using SBackup) and the other to do all my other backup scripts (using rsync & cron).

Rhodry.

---

### Post by Man_Beach on 2007-08-23
Thank you all for the advice and suggestions.

---

