---
title: "Slow file copy speed"
date: 2006-11-02
forum: General Help
---

### Post by mishranurag on 2006-11-02
I have noticed that whenever I have to move or copy around files from CD or hard drive (to and fro), the speed with UBUNTU is very slow compared to windows! Am I missing something?

Anurag

---

### Post by dannyboy79 on 2006-11-02
do you have dma enabled for your hard drives? what speeds does your cd-rom or whatever you're copying FROM read at? turning dma on for your hard drives is documented in the ubuntu wiki I believe.

---

### Post by mishranurag on 2006-11-02
I have UBUNTU 6.06 which has DMA enabled by default. Moreover, I see the same issue when transferring files from external HD.

---

### Post by dannyboy79 on 2006-11-02
> **mishranurag said:**
> I have UBUNTU 6.06 which has DMA enabled by default. Moreover, I see the same issue when transferring files from external HD.

i have to disagree, how would it be possible for an os to have dma enabled for your devices when the os doesn;t know the devices until after you install it. You need to enable dma on hda if that's your hdd. are you comparing the same specs between winbloz and ubuntu? ram, psu, cpu, etc etc. other than that I can't help ya

---

### Post by rsambuca on 2006-11-03
Sounds to me like dma might not be turned on.  To check your drives, use the hdparm command to check:

```
sudo hdparm /dev/hda
```

In this case, it will list the settings for your hda drive (you can replace hda with hdb, hdc, etc.).  In the resulting listing, there will be a line which indicates 

using_dma    =  1 (on)

or it will be = 0 (off).

If dma is turned off, you can simply turn it back on using the -d1 option for hdparm command.

You should check your CD drives and hard drives from the sound of things.

Good luck

---

### Post by mishranurag on 2006-11-06
Using the above command, I found that dma is on for all the drives!

---

### Post by hikaricore on 2006-11-06
> **dannyboy79 said:**
> i have to disagree, how would it be possible for an os to have dma enabled for your devices when the os doesn;t know the devices until after you install it. You need to enable dma on hda if that's your hdd. are you comparing the same specs between winbloz and ubuntu? ram, psu, cpu, etc etc. other than that I can't help ya

personally every installation of ubuntu I've ever done has enabled DMA by default...

---

### Post by zgornel on 2006-11-06
DMA for CD/DVD drive ?

---

