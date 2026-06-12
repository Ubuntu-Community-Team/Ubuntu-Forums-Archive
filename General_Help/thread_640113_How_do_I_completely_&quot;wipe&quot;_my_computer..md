---
title: "How do I completely &quot;wipe&quot; my computer."
date: 2007-12-13
forum: General Help
---

### Post by amazingDentist on 2007-12-13
I need to erase everything and start anew.
How do I do this?
I am currently running Ubuntu 7.10. And I have the boot ISO disc to install it again.

---

### Post by taurus on 2007-12-13
From the LiveCD, run GParted (System -> Administration) and delete all the partitions.  Format it back to fat32/vfat.

---

### Post by jken146 on 2007-12-13
You don't need to do anything prior to installing your new OS.  Just make sure you have everything backed up that yu want to keep, then pop in the Ubuntu install CD and go through the steps.  If you want to read a guide, try the one on psychocats.net

---

### Post by markusf21 on 2007-12-13
If I understand you question, all you have to do is reinstall and let it format the disc(s). Then you are fresh.

---

### Post by astromech on 2007-12-13
> **taurus said:**
> From the LiveCD, run GParted (System -> Administration) and delete all the partitions.  Format it back to fat32/vfat.

That's good also you can use  a utility like Kill Disk download the free one here:

[http://www.killdisk.com/downloadfree.htm](http://www.killdisk.com/downloadfree.htm)

---

### Post by amazingDentist on 2007-12-13
Run GParted?

---

### Post by NET WT on 2007-12-13
Maybe try [DBAN]("http://dban.sourceforge.net/") It is free,  but takes a few hours to run successfully.

---

### Post by astromech on 2007-12-13
> **amazingDentist said:**
> Run GParted?


Boot the live disk you used to install Ubuntu and in the administrator settings menu the should be an entry for gparted or "partion disk" I'm using Xubuntu so I can't remember exactly where it is but it's there.Or just reinstall and tell the partitioner to " use entire disk".

---

### Post by HermanAB on 2007-12-13
Please, utilities like 'killdisk' and 'shred' don't actually work, but as pointed out above, you don't need it either.  Just re-install and let the installer reformat the disk.

Cheers,

Herman

---

### Post by amazingDentist on 2007-12-13
ok thanks for the reply s
i'm going to reinstall from the boot disc...
last time i selected "entire disc" when partitioning, yet windows vista still lingers.
hopefully it will work this time.

thanks again

---

### Post by amazingDentist on 2007-12-13
> **taurus said:**
> Format it back to fat32/vfat.

How is this done?
And perhaps I'm mistaken but isnt' Fat32 a Microsoft-Based FileSystem?

---

### Post by MrFSL on 2007-12-13
> **amazingDentist said:**
> How is this done?
And perhaps I'm mistaken but isnt' Fat32 a Microsoft-Based FileSystem?

You beat me to the post... not exactly sure what you were getting at with the whole format to FAT but... I believe FAT and FAT32 were designed by Microsoft... but are well supported on just about any O/S. 

The "how" is easy... in gparted just select it by right clicking on the partition.

---

### Post by astromech on 2007-12-13
> **amazingDentist said:**
> How is this done?
And perhaps I'm mistaken but isnt' Fat32 a Microsoft-Based FileSystem?

I'm not sure it's a good idea to choose the FAT file system for Linux it may work bu there are  file systems dedicated to linux  such as ext3 reiser.It stands to reason that they would be better suited I have used both and it works.

I would let the installer use the default.

---

### Post by amazingDentist on 2007-12-13
> **astromech said:**
> 
I would let the installer use the default.

'Tis what I did.

And no, I would never rub a magnet on my hard drive.:wink:

\\:D/

---

### Post by HermanAB on 2007-12-14
BTW, common magnets will do nothing to a HDD, unless you scratch the disk with it real bad...

---

### Post by astromech on 2007-12-14
> **HermanAB said:**
> BTW, common magnets will do nothing to a HDD, unless you scratch the disk with it real bad...

maybe a bulk tape eraser. I remember a long time ago a guy in a computer shop had one ,but don't ask me what it was for, i don't remember.

                                                                                   :confused:

---

### Post by astromech on 2007-12-14
> **amazingDentist said:**
> 'Tis what I did.

And no, I would never rub a magnet on my hard drive.:wink:

\\:D/

Glad to hear you've got your Ubuntu back !   :guitar:

---

