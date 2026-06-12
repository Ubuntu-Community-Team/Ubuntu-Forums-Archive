---
title: "File-system is write-protected"
date: 2008-06-05
forum: General Help
---

### Post by themostunoriginalname on 2008-06-05
I have two ext3 partitions and deluge is reporting that it can download into them because it's a read-only filesystem.

I tried chown-ing the filesystem and sucessfully switched to me as the owner. I tried chmod 777 on everything in both partitions, but I get stuff like chmod: changing permissions of *some file* : Read-only file system while doing so. Anyway I can fix this?

---

### Post by robjoski on 2008-06-05
Print this out before you try it:

1. Reboot.
2. Press Escape when it says "Press Escape to enter the menu".
3. Scroll up or down until you get to "Ubuntu (your version), kernel [whatever]. Press "E" to edit.
4. Go down to the line that starts with "kernel" and press "E".
5. Change "ro" to "rw".
6. Pres "B" to boot.

This is only temporary; once you have write access to the filesystem, ask me for further instructions, or look up "Editing GRUB Menu.lst" in the Ubuntu Documentation...

---

### Post by themostunoriginalname on 2008-06-05
It's not the root partition.

---

### Post by robjoski on 2008-06-05
Try to remount it...

sudo umount /dev/yourdrive0
sudo mount -o rw,user /dev/yourdrive0 /whatever

How is it connected, may I ask?

EDIT: I read some of your other posts, and it sounds like the drive in question is dead. I don't know what I can do for you.

---

### Post by themostunoriginalname on 2008-06-05
I think it's dying too. The BIOS doesn't detect the drive on restart sometimes. It also seems to really overheat compared to my other Seagate drive. I'm going to go contact Seagate and see what I can do about it.

Thanks.

---

