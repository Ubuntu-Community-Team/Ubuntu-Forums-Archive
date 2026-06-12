---
title: "How do I access my files from LiveCD?"
date: 2006-11-19
forum: General Help
---

### Post by Oputres on 2006-11-19
Hi!

Grub is giving me error 24 when I'm starting my laptop. It's a dead end, i've tried so many things but none of them have worked, i.e. reinstalling grub etc.

Is it possible to access my files from LiveCD-mode? I've got so much material on that harddrive that's so importent. And the really funny thing - that's my backup. This computer actually crasched while I was formatting my regular computer. What are the odds of that?

I've also tried to put the harddrive into an external HD-case and it seems that Ubuntu regognize a new "USB Mass storage device" but it isn't displayed in the folder (can't remember the name, is it media?) Once Ubuntu actually found the harddrive but couldn't mount it.

What to do, what to do? ](*,)

---

### Post by taurus on 2006-11-19
You need to mount your harddrive from LiveCD before you can access it.  Assuming it's /dev/hda1 (first partition of the first harddrive with ext3 filesystem), open a terminal, Applications -> Accessories -> Terminal, and do

```
sudo mkdir /mnt/harddrive
sudo mount -t ext3 /dev/hda1 /mnt/harddrive
df -h
```

---

### Post by Oputres on 2006-11-20
> **taurus said:**
> You need to mount your harddrive from LiveCD before you can access it.  Assuming it's /dev/hda1 (first partition of the first harddrive with ext3 filesystem), open a terminal, Applications -> Accessories -> Terminal, and do

```
sudo mkdir /mnt/harddrive
sudo mount -t ext3 /dev/hda1 /mnt/harddrive
df -h
```

Hmm. I got this error message:

mount: wrong fs type, bad option, bad superblock on /dev/hda1,
missing codepage or other error
In som cases useful info is found in syslog - try
dmesg | tail or so

Trying the command dmesg | tail results in:
...
EXT3-fs: hda1: couldn't mount because of unsupported optional features (20002000).

I know it's hda1 and I think it is an ext3-fs but how can I check this?

---

### Post by Oputres on 2006-11-20
Running the fdisk -l command gives_

Disk /dev/hda: 20.0 GB, 20003880960 bytes
255 heads, 63 sectors/track, 2432 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device[COLOR="White"]_____[/COLOR]Boot[COLOR="White"]____[/COLOR]Start[COLOR="White"]_____[/COLOR]End[COLOR="White"]____[/COLOR]Blocks[COLOR="White"]__[/COLOR]Id[COLOR="White"]__[/COLOR]System
/dev/hda1[COLOR="White"]____[/COLOR]*[COLOR="White"]________[/COLOR]1[COLOR="White"]____[/COLOR]2339[COLOR="White"]_[/COLOR]18787986[COLOR="White"]__[/COLOR]83[COLOR="White"]__[/COLOR]Linux
/dev/hda2[COLOR="White"]__________[/COLOR]2340[COLOR="White"]____[/COLOR]2432[COLOR="White"]___[/COLOR]747022+[COLOR="White"]__[/COLOR]5[COLOR="White"]__[/COLOR]Extended
/dev/hda5[COLOR="White"]__________[/COLOR]2340[COLOR="White"]____[/COLOR]2432[COLOR="White"]___[/COLOR]746991[COLOR="White"]__[/COLOR]82[COLOR="White"]__[/COLOR]Linux swap / Solaris

Does this look correct? Then why won't the mounting work? :(

What about installing Lilo instead of Grub? Is that easy?

---

