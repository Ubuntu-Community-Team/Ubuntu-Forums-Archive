---
title: "***Very Urgent*** Mounting Filesystem and USB Device"
date: 2006-10-25
forum: General Help
---

### Post by jrickmar on 2006-10-25
I am having a huge problem with my instalation of Ubuntu.  I can not load the GDM for some reason, and my usplash gets 99% done and then freezes.  So, I enter grub, and choose the recovery single user mode, which gives me a text only screen as root.

The problem is that I have a file that I absolutly need on my disk, and since GDM won't load I can't open it.  I thought that I could save the file by inserting my flash drive and copying the file it over to it.  But, when I tried that, it doesn't auto mount it for some reason, and I can't get it to mount using sudo mount.

So, I thought that I could get around this problem and use my Ubuntu instalation CD as a rescue disk, and mount my hard disk with it, and then just drag and drop the file I need to my flash drive.  My flash drive mounted fine, but now I can't seem to mount my hard disk and save my file.

I really REALLY need this file soon, so any help would be FANTASTIC.

I'm running the Edgy Eft RC in VMware 5.5 on Windows XP.

---

### Post by tzulberti on 2006-10-25
You should try:
sudo mkdir /mnt/PEN
sudo mount -t vfat /dev/sda1 /mnt/PEN

---

### Post by jrickmar on 2006-10-25
That doesn't work.  I get this output

```
mount: /dev/sda1 already mounted or /mnt/PEN busy
mount: according to mtab, /dev/sda1 is mounted on /
```

---

### Post by jrickmar on 2006-10-25
Any ideas how to mount my hard disk from the ubuntu live cd?  Is there a recovery disk I can download that will be able to mount or even auto mount my hard disk?  If so, since it should also mount my flash drive, I could just drag and drop the file.

---

### Post by jrickmar on 2006-10-26
got it working.

I  checked out my Knoppix CD, which worked great as a system recovery disk.  It auto mounted my hard disk, so then I could e-mail the file to myself.

I'm upgrading to 6.10 as I'm writing this, and I made sure that all the files I need were saved, so I'm all good.

Thanks to txulberti for trying to help me fix this problem.

---

### Post by tzulberti on 2006-10-26
> **jrickmar said:**
> That doesn't work.  I get this output

```
mount: /dev/sda1 already mounted or /mnt/PEN busy
mount: according to mtab, /dev/sda1 is mounted on /
```

When you run this the pen was mounted? if so, you should umount it first, and disable automount for Removable devices

---

