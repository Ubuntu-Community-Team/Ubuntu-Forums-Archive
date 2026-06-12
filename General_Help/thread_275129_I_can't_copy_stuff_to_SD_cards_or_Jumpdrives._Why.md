---
title: "I can't copy stuff to SD cards or Jumpdrives. Why?"
date: 2006-10-10
forum: General Help
---

### Post by Roasted on 2006-10-10
Simply what the title says. I guess I have some permissions messed up, but I don't know what to do with it.

I just get an error. Says unable to move. Retry/skip/ignore. I can't get them to move at all. How can I get around this?

---

### Post by taurus on 2006-10-10
Try to move/copy your stuff to the drive with sudo...

---

### Post by Roasted on 2006-10-10
I'm not using terminal. I'm just dragging and dropping. So I'm kinda lost... I didn't change anything which completely confuses me as to why it's acting like this.

---

### Post by taurus on 2006-10-10
Maybe because you mount your jumpdrive as root which means only root can write to it!!!  That's why you need to use sudo to move files to it if you've mounted it with root permission...

---

### Post by Roasted on 2006-10-11
Uh. I just plugged the thing in. And I got these errors. Sooooooo yeah. I didn't mount anything. :confused:

---

### Post by Roasted on 2006-10-11
Hi. Still can't do anything. Not sure why Linux is giving me hell...

---

### Post by taurus on 2006-10-11
What filesystem (NTFS, VFAT/FAT32, ext3, etc.) is your jumpdrive then???

---

### Post by Roasted on 2006-10-11
I have no idea. I never, EVER had any problems when it came to transferring music videos and stuff. I used to use it all the time. How would I find out what file system it is?

---

### Post by catlett on 2006-10-11
Open a terminal and launch the file browser with ```
gksudo nautilus
``` Browse to the files you want to drag and drop. Hopefully when you drag now, it will drop because you are root and you are copying to a root file.
You can also change file permissions like this. Launch as gksudo nautilus and go to the file or folder you want to change. Right click on it and select "properties". Then select the "permissions" tab. This will bring up three rows of boxes. You can check them off to give ownership to others (namely yourself instead of root)

---

