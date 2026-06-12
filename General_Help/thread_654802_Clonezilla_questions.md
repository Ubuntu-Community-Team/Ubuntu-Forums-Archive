---
title: "Clonezilla questions"
date: 2007-12-31
forum: General Help
---

### Post by 67GTA on 2007-12-31
I need to reinstall Vista with my recovery disk. It will wipe out my Kubuntu partition. It will use the whole hard drive. If I make an image of Kubuntu with clonezilla, can I save that to my Kubuntu partition>burn it to disc>copy that image to my new Vista installation>and use the clonezilla cd to copy it back to a new partition? I can't find a lot of docs for clonezilla, so I'm not sure if it is what I'm looking for.

---

### Post by p_quarles on 2007-12-31
The Vista recovery disk *won't *overwrite your ext3 partition. I know this from personal experience. It will overwrite GRUB, but that's relatively simple to reinstall. 

Backup any data that you can't lose, of course, but barring a disaster, your Kubuntu partition will be just like you left it.

---

### Post by 67GTA on 2007-12-31
I assumed it would since my old XP recovery disk done the same thing. It would always reformat the whole hard disk. It isn't the original installation disk. It is one that XP/Vista tells you to make when you first fire up your PC for the first time. I made a copy of my Kubuntu partition with Clonezilla. I will go ahead and make an aptoncd from Kubuntu, and backup my home folder just in case. If it won't touch Kubuntu, that will be awesome!

---

### Post by p_quarles on 2007-12-31
Yeah, the last time I reinstalled Windows from a home made recovery disk, it kept my partitions intact, and only reformatted the existing NTFS partition. I'd be surprised if it gives you any trouble, but at least you've got the backup in case it does.

---

### Post by 67GTA on 2008-01-03
You were right. It had the option to use the whole hard drive or use the existing partition. I was skeptical because of my old XP factory restore disk. This is the first home made restore disk I've used. For some reason it kept my old account, and created a new one. I will have to sort that out, but at least I didn't have to screw up my Kubuntu install!

---

