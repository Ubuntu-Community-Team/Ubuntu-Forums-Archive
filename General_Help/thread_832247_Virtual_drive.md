---
title: "Virtual drive?"
date: 2008-06-17
forum: General Help
---

### Post by im_an_alien on 2008-06-17
I'm trying to copy some files to my IBM PC/XT with a 5.25" floppy drive, but when I try to copy files to it, it keeps saying that there's no space left on the disk, even if it's a freshly formatted disk.  I can copy and delete files from it, and I can write and read disk images with dd fine, so I'm pretty sure there's nothing wrong with the drive or the disks.  Unless someone has a better idea, is there a way I can make a virtual drive, copy the files to it, make a disk image, and then write the disk image to the floppy?

Also, I've already copied a few files over, this just randomly started a minute ago.

While I'm posting, when I try to unmount, it says

bash: unmount: command not found

or

sudo: unmount: command not found

---

### Post by kalesh7 on 2008-06-17
first up there is no command unmount, its umount (I used to make this error a lot too)
yes you can make a  virtual drive just create an image file with dd then mount it using mount image_file mount_point type -o loop=loop3
then copy your files to mount_point unmount and use dd to write back.

---

### Post by im_an_alien on 2008-06-17
Thanks, that worked great.  I just had to change "loop=loop3" to just "loop"

---

### Post by kalesh7 on 2008-06-17
> **im_an_alien said:**
> Thanks, that worked great.  I just had to change "loop=loop3" to just "loop"

sorry I just caught the error for benefit of anyone else its 
```

mount file_to_mount mount_point -t type -o loop=/dev/loop3
```the -t type can be left out most of the time.

---

