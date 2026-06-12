---
title: "Can't copy files to portable HD"
date: 2007-04-29
forum: General Help
---

### Post by thesikness on 2007-04-29
I have been trying to copy my music to a portable hard drive, but it comes up with an error. It says that I don't have the permissions because it is a read-only disk. It works fine when the portable hard drive is connected to a Windows computer, but not with Linux. When I was on the Windows computer, I went into the Properties and set the permissions so that anyone can copy files. It still isn't working though. It comes up with the same message. I am completely out of ideas, so some help would be appreciated. Being that I'm sick of this problem, I'd also appreciate as much detail as possible. Thanks in advance.

---

### Post by dagrump on 2007-04-29
You need to use sudo chown yourname /dev/usb?.  you need to see what its listed as & correct the path. I working w/o a net here some one give better info.

---

### Post by dfreer on 2007-04-29
you are probably using a hard drive formatted with NTFS. NTFS is not writable in linux without installing special drivers. Check out NTFS3G and how to install on ubuntu

---

