---
title: "New stupid splash theme ruined my compter!"
date: 2007-10-08
forum: General Help
---

### Post by Masterj15 on 2007-10-08
This is the splash theme I wanted so badly:
[http://www.gnome-look.org/content/show.php/Usplash+Theme+-+Fingerprint?content=50468](http://www.gnome-look.org/content/show.php/Usplash+Theme+-+Fingerprint?content=50468)

I did everything it told me to do but when I restarted my computer it came up with this message:

```
Starting up.....
[    0.000000]ACPI:Bios age (1999) fails cutoff (2000), acpi=force isrequired to enable ACPI

[   73.206137]RAMDISK: ran out of compressed data
[   73.206288]invalid compressed fromat (err=1)
[   73.210242]kernel panic - not syncing:VFS: unable to mount root fs on unknown - block
```

I tried going into recovery mode but those number keep growing and they never give me my shell. The only way I excute a shell is in the alternate disk. I tried switching the new splash theme with the old ubuntu theme, by going into ReadME that came with the new splash theme, but that didn't work (or I did it worng)

Any ideas would be nice as I can't go into anything off my computer. I would restart but I still have some important stuff their.

---

### Post by jespdj on 2007-10-08
I don't have a direct solution for your problem. You can boot from a live CD, mount your Linux partition and then do repairs (or save your important data).

---

### Post by Blindraven on 2007-10-08
Easy fix, your lilo/grub is pointing to a non existing drive.

u need to post the O/p of

fdisk -l /dev/hda
and
/etc/lilo.conf or /etc/grub.conf

---

### Post by Masterj15 on 2007-10-08
> **Blindraven said:**
> Easy fix, your lilo/grub is pointing to a non existing drive.

u need to post the O/p of

fdisk -l /dev/hda
and
/etc/lilo.conf or /etc/grub.conf

I am understanding some of what your saying. I'll post the /etc/grub.config. but the o/p I have no clue what your talking about or the fdisk -i /dev/hda.

I will have to post in some hours frm now. I have to go somewhere unfortonatly:sad:

---

### Post by strabes on 2007-10-08
o/p = output

I think an easy fix would be to simply reinstall GRUB. See the link in my signature for how to do that.

---

### Post by Masterj15 on 2007-10-08
I tried to reinstall grub using the repair a harddrive on the ubuntu alternate disc. Its said ok and nothing happened but I'll look at the sig anyway.

---

### Post by mszl_1 on 2007-10-09
i installed very theme using kde!! i went to konqeror settings and played around and in it went.:lolflag:

---

### Post by Masterj15 on 2007-10-10
> **mszl_1 said:**
> i installed very theme using kde!! i went to konqeror settings and played around and in it went.:lolflag:

maybe it doesn't work with gnome

---

### Post by mszl_1 on 2007-10-11
sorry mate i dont know since i use kde and not gnome. have you tired using kde to install this theme and then boot into gnome? who knows??:)

---

### Post by Masterj15 on 2007-10-11
> **mszl_1 said:**
> sorry mate i dont know since i use kde and not gnome. have you tired using kde to install this theme and then boot into gnome? who knows??:)

it works with ultimate so I'm happy for now. Thanks anyway:)

---

### Post by mszl_1 on 2007-10-11
glad to hear. :)

---

