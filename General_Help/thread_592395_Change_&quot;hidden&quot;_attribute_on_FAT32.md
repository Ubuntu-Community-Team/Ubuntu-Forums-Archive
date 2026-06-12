---
title: "Change &quot;hidden&quot; attribute on FAT32"
date: 2007-10-26
forum: General Help
---

### Post by AdaHacker on 2007-10-26
Is there a command or utility somewhere that can change the "hidden" attribute on a file that's on a FAT32 filesystem?  I would have thought this would be pretty easy, but Google is failing me.

The situation is that I just got a new SanDisk Sansa e280 MP3 player and installed the RockBox open-source firmware on it.  It seems that RockBox respects the hidden attributes, but the Sansa firmware wants to hide the important directories, i.e. the music directory.  I can set RockBox to show all files, but I'd rather just be able to hide system files and show all my data.  I just can't figure out how to adjust the attributes on the FAT32 filesystem from Ubuntu.

Any help would be greatly appreciated.

---

### Post by AdaHacker on 2007-10-26
Never mind, I answered my own question.  I  got the idea from [here]("http://ubuntu.wordpress.com/2006/03/01/editing-fat32-partition-labels-using-mtools/").

The solution is that you can  use mtools for this.  You need to add something like the following to your ~/.mtoolsrc file:
```

drive s: file="/dev/sdb1"
mtools_skip_check=1
```
This associates a DOS-style drive letter with a device file.  You should, obviously, substitute the path to the USB mass storage device appropriate for your system.  The mtools_skip_check line suppresses errors which, I believe, arise from the fact that this is a USB device, not an actual disk.

Once that's set up, you can use the mattrib command to change the file attributes.  In my case, the commands were something like this:
```

mattrib +h S:/TMP
mattrib -h S:/MUSIC
mattrib -h S:/PLAYLISTS
```

---

### Post by superm1 on 2007-12-01
Awesome!  glad I came across this.  I was searching for a good 20 minutes :)

---

