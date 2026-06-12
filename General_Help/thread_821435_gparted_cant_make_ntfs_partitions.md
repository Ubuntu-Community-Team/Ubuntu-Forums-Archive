---
title: "gparted cant make ntfs partitions"
date: 2008-06-07
forum: General Help
---

### Post by hempa on 2008-06-07
hello i have two internal harddrives (Sata). One wich i have ubuntu hardy on, and one that is empty. The empty one (it says unallocated space when i watch it in gparted) i want to partition so i can install windows xp on it.But the problem is that gparted cant make a ntfs partiton, i have the choice to make ntfs in the list were i can choose differnet file systems fat32, ext, and so on. But when i choose to make a ntfs partition i get a error message saying that gparted couldn`t make the partition. So i opened ntfs-config and there are two checkboxes there, one wich will enable write support for external devices and one wich will enable write support for internal devices. Strangely enough i can just check the box for write support for external devices the support for internal devices box is shaded in grey and i cant choose that option.

So what can i do if i want to create a ntfs partition on my empty harddrive
and how do i enable write support for internal devices in ntfs-conf.

any help on this would be great thanks.

---

### Post by housam on 2008-06-07
try to use [[COLOR="Red"]_Gparted live cd_[/COLOR]]("http://gparted.sourceforge.net/livecd.php"). or partition magic.

---

### Post by ChameleonDave on 2008-06-07
> **hempa said:**
>  i want to partition so i can install windows xp on it.But the problem is that gparted cant make a ntfs partiton,

It doesn't matter.

When you install XP, it will want to format the partition itself anyway, and I would recommend letting it do so, as no one knows how to format NTFS partitions better than Microsoft (it being a trade secret of theirs).

Just create a partition (in FAT format, say) for Windows.  Then let Windows format it correctly.

------

As for why gparted is unable to work with NTFS... try entering this at the terminal:

```
sudo apt-get update
sudo apt-get install --reinstall ntfs-progs libntfs10 libntfs-3g23 gparted
```

---

### Post by VMC on 2008-06-07
> **hempa said:**
> ...But the problem is that gparted cant make a ntfs partiton...
To answer this question. Newer Gparted can. I think v 3.7. I know the newest Puppy, and Systemrescuecd v1.0.3 will work. As suggested updating Gparted through Synaptic should work. If I'm doing work using a partition manager I want to use a licecd.

---

### Post by rampageoberon on 2008-06-07
I have used the gparted live cd's to create NTFS partitions, so I'm sure it works.

---

### Post by Yadda on 2008-08-20
Hello there,

The key to getting gparted to make ntfs partitions (for me anyway) is ntfsprogs

```
sudo apt-get install ntfsprogs
```

the above 
```
nfts-progs
``` 

no longer works. They seem to have done away with the dash.

---

