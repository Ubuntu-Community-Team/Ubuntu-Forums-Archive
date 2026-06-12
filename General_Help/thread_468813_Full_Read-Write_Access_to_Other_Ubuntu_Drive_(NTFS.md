---
title: "Full Read-Write Access to Other Ubuntu Drive? (NTFS was Easy in comparison!)"
date: 2007-06-09
forum: General Help
---

### Post by OzzyFrank on 2007-06-09
Hi. First off, amazing how simple it is to get full read-write access to my Windows (NTFS) drive. Hever had any hassles with using ntfs-3g, either manually mounting or sticking one little line in fstab and having it done for me at boot. Using the mount command and -t, or sticking another simple line in fstab, means mounting fat32 drives is just as simple. However, I'm still scatching my head as to how to get similar access to my first Ubuntu drive, as all the examples I've found on the web using "rw" and "exec" and this and that in fstab still have me accessing my other ext3 drive only read-only. I have to resort the the terminal if i need to do something, but would prefer to get the same full access to the other Linux drive as i enjoy with the Windows drive. I have tried MANY different variations of options in fstab, and even tried "auto" instead of "ext3" for the filesystem. If anyone out there has another Ubuntu or Linux partition being mounted in fstab and you have full read-write access, can you please send me the fstab line for that partition. This is getting beyond ridiculous, hehe. Many thanks in advance.

---

### Post by Bakerman on 2007-06-09
Hi,

/dev/sdb1 /media/storage ext3 defaults 0 0

is my fstab line to mount a 2nd ext3 hard drive & I used this to change the mountpoint folder permissions:

sudo chmod -R a+rwx /media/storage

I have no problems with recursive read/write/execute access to this SATA drive.

Hope this helps...

---

### Post by OzzyFrank on 2007-06-09
Hi, and thanks for your input. My knowledge of the use of "chmod" is pretty limited, and I admit I've probably used it more when setting up a web page guestbook from Windows, hehe. I do understand you can change permissions with it, but I've just used "sudo" and "chown" to get around those times. I thought i'd chmod the mount point folder and see what happens. While the drive is not attached at present, the empty mount point folder lets me create files and folders within it, so I would hazzard to guess this is the answer I was looking for... so thanks heaps!

Oh, did try this on my mounted Mac OSX partition, and was almost kicking myself when I saw it trying to change permissions of every folder under it (I usually research a command and its options before using them). Didn't actually achieve anything, as I was told it was a read-only operating system. Just thought I'd put that in for people who might get a shock at something like that (might be better to chmod the empty mount point folder first?).

Thanks again.

---

### Post by OzzyFrank on 2007-06-11
Follow up:

Using **chmod** on the empty mount point folder isn't the way to go, as the permissions are back to the default of RO once the drive is actually mounted. So mount the drive/partition first, then run the **chmod** command on the mount point. I've rebooted a couple of times and can still write to my Edgy drive, so that seems to be the answer.

Still amazed how much easier it is to rw NTFS and FAT32 drives, considering one would expect it to be harder than with a Linux drive. Not that this was that hard, but novices out there might be stumped.

Cheers

---

