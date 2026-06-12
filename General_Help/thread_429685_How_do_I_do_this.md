---
title: "How do I do this"
date: 2007-05-01
forum: General Help
---

### Post by Lord de le Warr on 2007-05-01
I followed this awsome guide to get Windows XP on Ubuntu.
[https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo](https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo)

Under the Mounting A Virtual Drive, i dont understand how to do [To mount the drive, create a directory '/media/qemu'.] Can anyone help me with this one.

---

### Post by useResa on 2007-05-01
You can create this directory by opening a terminal (Applications --> Accessories --> Terminal). In the terminal issue the following command
```
cd /media
```
This will take you to the media directory.
Next issue the command
```
sudo mkdir qemu
```
By doing so you create (as root) the sub-directory named qemu in the media directory

Now that you have made this directory you can issue the command from the tutorial
```
sudo mount -o loop,offset=32256 windows.img /media/qemu
```

I hope this will help you finalize the tutorial[FONT=monospace][/FONT]

---

### Post by Lord de le Warr on 2007-05-02
Thanx

---

