---
title: "Help needed for accessing linux drives (read&amp;WRITE!) in windows"
date: 2007-11-02
forum: General Help
---

### Post by grobar on 2007-11-02
Hi all, 

Is there a software (a windows one ;) to access linux drive thru windows.
I've got Ext2FS but that only reads my ext3 partition, I really need to edit a bashrc file so I need write persmission also!

Before someone mentions to go to ubuntu and to that, I can't access my ubuntu that's why I need to change bashrc,bash-profile and enviroment file...

Thanks!

---

### Post by potam on 2007-11-02
Yes, there is a native ext2(works with ext3) driver for Windows. Just install and all set, no reboot is necessary. Check it's website: [http://www.fs-driver.org/]("http://www.fs-driver.org/")

---

### Post by hikaricore on 2007-11-02
Just be careful editing **IMPORTANT** system files from ***dows.

If I'm not mistaken it _DOES NOT_ perserve file attributes or user/group data.

---

### Post by grobar on 2007-11-02
> **potam said:**
> Yes, there is a native ext2(works with ext3) driver for Windows. Just install and all set, no reboot is necessary. Check it's website: [http://www.fs-driver.org/]("http://www.fs-driver.org/")

I use this one, as I said I can't write to my linux partition.
I can read and save=copy my ubuntu files to windows but I can't write to linux partition!
I have ext3 and it seems that the write option doesn't work here...

---

### Post by KhurramF on 2007-11-02
Why not boot from a live cd (or Knoppix etc) and mount your partitions within it?

---

### Post by grobar on 2007-11-02
I just need to access bashrc file, delete 3 lines,save it and that's it.
Is there a command in windows (using regedit to change permissions for one particular folder?)

---

### Post by hikaricore on 2007-11-02
I'm not sure why you can't access it from ***dows honestly.

File permissions/ownership shouldn't cross over.

---

### Post by bingoUV on 2007-11-02
> **grobar said:**
> I use this one, as I said I can't write to my linux partition.
I can read and save=copy my ubuntu files to windows but I can't write to linux partition!
I have ext3 and it seems that the write option doesn't work here...

grobar, it can write ext3 files. I use it all the time. 

This program seems a little afraid of damaging files, so hides the "enable write" option somewhat deep. Default mount is read only. After mount, try looking for some option to enable write.

---

### Post by starfry on 2007-11-02
I use the ext2 driver for windows at [http://www.fs-driver.org/](http://www.fs-driver.org/) and it works for me.

You need to realise the limitations of the driver - that the ext2 drive us unpermissioned especially. But it does work. Read and Write.

---

### Post by grobar on 2007-11-02
I used this one and it works :-)

[http://sourceforge.net/projects/ext2fsd](http://sourceforge.net/projects/ext2fsd)

My next post will be from ubuntu (hopefully). See ya in a second :-)!

---

### Post by grobar on 2007-11-02
still nothing , I've got the same problem. Oh well, when is next version coming? :-)

[http://ubuntuforums.org/showthread.php?t=600335](http://ubuntuforums.org/showthread.php?t=600335)

---

