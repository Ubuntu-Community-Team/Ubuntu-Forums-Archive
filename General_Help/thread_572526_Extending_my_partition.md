---
title: "Extending my partition"
date: 2007-10-10
forum: General Help
---

### Post by Arenlor on 2007-10-10
I finally got sick of having M$ Vista(sucks) on my machine and formatted it last night, now I want to extend my linux partition to cover that entire part (a majority of my disk) how would I go about doing this without reinstalling?

---

### Post by vanadium on 2007-10-10
In principle, this can work by deleting the Windows partition (fast proces) then moving the Ubuntu partition to the start of the disk (slow proces), then enlarging the Ubuntu partition to fill the free space (fast proces). Because Feisty uses UUIDS, partitions would continue to mount fine even if the partition designations would change. However, you will need to edit /boot/grub/menu.lst and change the partition to load Linux: instead of (hd0,1) it will become (hdo,0).

This is just the general concept. I do not have the experience to do it myself. First read more about the topic. You may ask yourself first if just reformatting the Windows partition and using it as a second partition for data storage would not be satisfactory for you. The latter operation is a lot easier and safer to implement.

---

### Post by stchman on 2007-10-10
I concur with vanadium.  There is no advantage to doing what you want.

---

### Post by Arenlor on 2007-10-10
I had been hoping for an easy way to do it that was safe. made it ext3, that right?

---

### Post by vanadium on 2007-10-11
The easy way that is safe involves reformatting your current Windows partition to ext3. This is safe because you do not touch your system partition. It can be done graphically with gparted, which you might first need to install using synaptic. Do not use the gparted live CD, just run gparted after normally starting Ubuntu. That way, your system partition is in use and there is no chance that you accidentely reformat the wrong partition.

The tricky way is to combine both partitions into one, but that is tricky because it involves moving and changing the system partition, and changing the partition table, thus requiring you to tweak at lease /boot/grub/menu.lst to be able to boot again. Do this only if you are sufficiently experienced or if you really want to do this for the challenge and can take the risk to break your system.

Like stchman suggests, it is not necessarily an advantage to combine all disk space into one partition, except if you have a rather small drive.

---

### Post by questpro on 2007-10-11
> **Arenlor said:**
> I had been hoping for an easy way to do it that was safe. made it ext3, that right?

I am also doing a kind of same stuff right now. Please post back the results when you done. Thanks all.

I am trying to read/write to NTFS partiton of windows XP from UBUNTU. I can not write to that disk from ubuntu. only i can read that.

---

### Post by Arenlor on 2007-10-11
> **questpro said:**
> I am also doing a kind of same stuff right now. Please post back the results when you done. Thanks all.

I am trying to read/write to NTFS partiton of windows XP from UBUNTU. I can not write to that disk from ubuntu. only i can read that.
Gutsy provides that.
> **vanadium said:**
> The easy way that is safe involves reformatting your current Windows partition to ext3. This is safe because you do not touch your system partition. It can be done graphically with gparted, which you might first need to install using synaptic. Do not use the gparted live CD, just run gparted after normally starting Ubuntu. That way, your system partition is in use and there is no chance that you accidentely reformat the wrong partition.

The tricky way is to combine both partitions into one, but that is tricky because it involves moving and changing the system partition, and changing the partition table, thus requiring you to tweak at lease /boot/grub/menu.lst to be able to boot again. Do this only if you are sufficiently experienced or if you really want to do this for the challenge and can take the risk to break your system.

Like stchman suggests, it is not necessarily an advantage to combine all disk space into one partition, except if you have a rather small drive.

I edit menu.lst every time the kernel upgrades since I have to append noapic to the end. I'd like to combine them both into one, and I'm willing to risk screwing up the system, plus it'd be a good learning experience even if I do (which I likely won't). I had already used gparted to format it to ext3. So how would I go about doing that, or is there a wiki entry on it?

---

### Post by vanadium on 2007-10-12
The conceptual procedure is outlined in my post in this thread. It all must be done in gparted from a live CD (because your system cannot be in use for the repartitioning. To combine the partitions, you need to delete the one that you just reformatted (sorry), then move your system partition to the front of the disk, then enlarge that partition to take all available space. Before doing anything with a partition, it must be unmounted. All operations are accessed from the right-click menu in gparted. Just like you, I would need to search for a tutorial or a wiki page.

---

### Post by Arenlor on 2007-10-12
I'll try that with my live USB later today. I'm thinking oddly clear today so I can see it happening. (I think that means I hit an all new level of geek)

---

### Post by Arenlor on 2007-10-13
Oddness, all went successfully, except one small detail; the part that I expanded onto is "filled". So the system is reporting it as such and won't use it, I'm just going to reinstall and let the computer format the whole thing, for two reasons, 1 it should fix my problem, 2 I really am that bored. Currently am backing up all my necessary files (mainly just ndiswrapper's install files and some music) yes necessary is up to the user.

---

### Post by vanadium on 2007-10-14
You might still have an extended partition sitting in the "free" space. In an extended partition, you can create logical partitions, but you cannot expand another partition onto the space reserved by an extended partition. Thus, you probably would need to delete that extended partition, or if contains logical partitions, shrink and move it.

Anyway, a reinstall might be quickest and easiest.

---

### Post by Arenlor on 2007-10-14
> **vanadium said:**
> You might still have an extended partition sitting in the "free" space. In an extended partition, you can create logical partitions, but you cannot expand another partition onto the space reserved by an extended partition. Thus, you probably would need to delete that extended partition, or if contains logical partitions, shrink and move it.

Anyway, a reinstall might be quickest and easiest.
I had deleted it, but reinstall went well enough.

---

### Post by strabes on 2007-10-14
> **questpro said:**
> I am also doing a kind of same stuff right now. Please post back the results when you done. Thanks all.

I am trying to read/write to NTFS partiton of windows XP from UBUNTU. I can not write to that disk from ubuntu. only i can read that.

Please search the forums before posting a question. Reading and writing to NTFS can be done easily through the ntfs-config and ntfs-g3 packages. See the first result of [this search](http://www.google.com/search?q=ubuntu+ntfs).

I recommend having a separate data/music/documents partition. That way you don't have to back up all your data/music/documents in order to reinstall.

---

