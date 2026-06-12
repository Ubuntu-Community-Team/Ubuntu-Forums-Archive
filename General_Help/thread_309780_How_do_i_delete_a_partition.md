---
title: "How do i delete a partition?"
date: 2006-11-30
forum: General Help
---

### Post by johnmxg12 on 2006-11-30
Hey guys, i originally had Windows XP, then i installed Ubuntu and i really like it.  I want to delete the partition i created for XP so that i can have more space for Ubuntu.  How would i go about doing this?  when i reboot, there's options to choose which OS i would like to boot, does my solution lie within that screen before Ubuntu?  Thanks for the help.

---

### Post by jclmusic on 2006-11-30
run gparted from the live cd. it can be done from an installed ubuntu also, but i'd reccomend doing it from the live cd as u can have problems with mounting etc otherwise.

---

### Post by zgornel on 2006-11-30
Use Gparted : It has a intuitive interface, just unmount the windows partition, right click on it and Delete. Create another partition there so you'll be sure that partition names won't change. Delete the Windows entry in /boot/grub/menu.lst

---

### Post by johnmxg12 on 2006-11-30
which sub folder would gparted be in the live cd?

---

### Post by jclmusic on 2006-11-30
> **johnmxg12 said:**
> which sub folder would gparted be in the live cd?

just open a terminal and type:
```
gparted
```

---

### Post by johnmxg12 on 2006-11-30
hey thanks for the help guys, much appreciated. :)

---

### Post by ajgreeny on 2006-11-30
Just beware that you may delete grub with the windows partition if you put grub on the MBR, and then need to reinstall grub again afterwards.  There are plenty of threads about doing this on the forum so do a quick search and you'll easily find it.

---

### Post by unlokia on 2006-11-30
> just open a terminal and type:
Code:

gparted



actually you should do:

```


sudo gparted


```

as this requires SU privelidges!

---

### Post by jclmusic on 2006-11-30
> **unlokia said:**
> actually you should do:

```


sudo gparted


```

as this requires SU privelidges!

yeah, sorry, my mistake. my thinking was that this wouldn't be nessecary from the live cd, tho.

---

