---
title: "Proper Format for Linux-Only External HD?"
date: 2007-11-09
forum: General Help
---

### Post by MSchenker on 2007-11-09
Hello,
I have an external hard drive that I carried over from when I used to run Windows XP.

Well, Windows XP is gone now!  But my external hard drive is still formatted in fat32.  I just left the drive plugged in when I installed Kubuntu and it was detected fine.  But now I'm wondering whether I should reformat it in NTFS or some other system, to optimize it for Linux?

Thanks,
Matt

---

### Post by dabl on 2007-11-09
FAT32 is not a very reliable file system format -- did you notice that Microsoft ran away from it 10 years ago?  :lolflag:

If you need to share that drive with Windows systems, then NTFS is probably the way to go.  If full-time Linux, then ext3.  Don't forget to "eject" it before pulling the plug on the USB connector, if you care about your data.  :)

---

### Post by MSchenker on 2007-11-10
dabl,
Thanks for helping to explain the various formats.  It looks like ntfs is the best one generally for me, since I sometimes take the external drive on the road and might need to plug it into a Windows machine occasionally.  Actually, that will be the only time I use Windows any more, since all of my own computers now run Kubuntu!
Thanks,
Matt

---

### Post by vanadium on 2007-11-10
Better stick to fat32 if you still need compatibility with Windows machines. The issue with ntfs is that linux cannot repair an ntfs system if the file system is damaged (for example by unplugging the drive during a write operation). For repairing the file system, you need a windows system.

Obviously, it is easy to find a windows system somewhere to do your repair, but I don't like the idea of being dependent on Windows for anything ;)

---

### Post by MSchenker on 2007-11-10
vanadium,
Thanks for the help.  FAT32 is the easiest solution, since I can just leave it the way it is.
Matt

---

