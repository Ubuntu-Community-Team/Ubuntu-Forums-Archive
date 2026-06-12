---
title: "Nautilus bug won't let me rename folders until restart"
date: 2015-02-03
forum: General Help
---

### Post by petermartin2 on 2015-02-03
Every now and then nautilus all of a sudden wont let me rename folders and files. I can click "rename" option but then there's just the selected text and nothing happens when I hit backspace or delete or any given button. Anyone know what the problem might be?

---

### Post by petermartin2 on 2015-02-03
Also Nautilus crashes and shuts completely if it may be of help in solving this problem. I don't mind the crashes as much as not being able to give new folders new names and change the names of old ones

---

### Post by mooreted on 2015-02-03
Run the disk utility and look at Smart status and errors. It's possible your hard drive is having issues.

---

### Post by petermartin2 on 2015-02-03
> **mooreted said:**
> Run the disk utility and look at Smart status and errors. It's possible your hard drive is having issues.

No luck there

---

### Post by mooreted on 2015-02-03
It's odd that it happens randomly and that it requires a restart. It can't be file permission problems because the permissions are either correct or they are not. They don't randomly change.

It could be a single file or a group of files that are corrupted causing Nautilus to crash. You can boot to a live cd and run fsck on your main hard drive. For instance, my main hard drive is /dev/sda1 so the command would be:

fsck -a /dev/sda1

You don't want to run this command on a mounted drive, so you have to use a live CD or thumb drive. Make sure you back up your data before you do it or you may lose data depending on how bad the file system is damaged.

Also, right after Nautilus crashes you can open a terminal and enter the following command:

dmesg

This will display the last few errors that ocurred. That might give you an idea of what's going on.

---

