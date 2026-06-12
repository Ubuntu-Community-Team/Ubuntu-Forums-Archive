---
title: "Reinstalling GRUB won't work (I have got GfxBoot)"
date: 2007-12-04
forum: General Help
---

### Post by warnec on 2007-12-04
Hello. I had Ubuntu 7.10 and installed GfxBoot, all worked fine. Now, suddenly, GRUB just stopped working. I don't know what caused that.My PC just boots Windows XP without any questions. But now, I wanted to reinstall GRUB - and i followed the HOW-TO from this forum. I run Ubuntu from Live CD. Here is what i got:
```

grub> find /boot/grub/stage1
  (hd0,5)

grub> root (hd0,5)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"... 15 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+15 p (hd0,5)/boot/grub/stage2
/boot/grub/menu.lst"... failed

Error 12: Invalid device requested

grub>

```
What should i do now? I think the error has something to do with GfxBoot, because i had to edit menu.lst. GfxBoot worked fine for one day, then this happen. I have got ext2 drivers on my WinXP, maybe i should enter manu.lst from there and remove the line I added? 

Second thing: i removed grub, and installed grub-gfxboot. I'm not sure if the following will work for me. When i explore folders with LiveCD, in "/boot/" there is no folder called "grub/"

PS.: I attached my menu.lst file, the one with the Gfxboot line at the beggining. I had to rename it to .txt, because i could not attach files with .lst extension.

---

### Post by logos34 on 2007-12-04
> maybe i should enter manu.lst from there and remove the line I added?

that's what I'd do...Get rid of 'gfx..' line and move the text back up to line 1.  Because your files are there, 'setup' is failing only at the last trying to make sense of menu.lst (you were looking in the live cd /boot, not the path to the mounted root partition, /media/disk/boot/grub)

---

### Post by warnec on 2007-12-04
Ok. I had no answer before, and i decided to format linux partiton and reinstall Ubuntu :P Now very,very strange thing. Installator did find my hard drive (it asked if i want to install Ubuntu on the whole 320GB space) and i chose to choose myself (i do it always that way,so I can select linux partitions for reinstall by myself, so it won't format any important things) and it did not find any partition! Not any one of them. It isn't like normal bug when LiveCD can't find hard disk, because it finds it, tells me it's 320GB, and can't find any partition. Now i can't install Ubuntu anymore :( the only choice would be to format everything on the drive, and i don't want that.

Ps.: I did edit menu.lst, but it didn't help.

---

### Post by meierfra on 2007-12-05
For everybody's information: warnec started a new thread on the same subject:
[http://ubuntuforums.org/showthread.php?t=631586]("http://ubuntuforums.org/showthread.php?t=631586")

---

