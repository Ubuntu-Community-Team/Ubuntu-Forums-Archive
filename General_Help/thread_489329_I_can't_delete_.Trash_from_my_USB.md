---
title: "I can't delete .Trash from my USB"
date: 2007-07-01
forum: General Help
---

### Post by miLl3niUm on 2007-07-01
I get an error (don't remember what) and I tried this from terminal:

```
root@millenium:/media/MILL3NIUM/.Trash-alter/Trasr/untitled folder# dir
Desktop
root@millenium:/media/MILL3NIUM/.Trash-alter/Trasr/untitled folder# rm -r Desktop
rm: cannot lstat `Desktop/ò7ïö&#9618;=\005ï.S\022&#9632;': Input/output error
```

How can I delete it?

---

### Post by Grigorius on 2007-07-01
Try unmounting it after pressing delete ... sometimes it waits for no good reason.

---

### Post by miLl3niUm on 2007-07-01
I click Empty Trash, I wait for a bit, usb is unmounted, I mount it again but the folder stills there.

---

### Post by miLl3niUm on 2007-07-01
Well?

---

### Post by Grigorius on 2007-07-01
Empty trash?

If you have the file on a USB drive it will never get to the trash folder I meant open the USB folder then crtl+h then delete the file wait a bit and then unmount the device.
(also check if you have permissions in proprieties)

---

### Post by miLl3niUm on 2007-07-02
I know how to delete it, the problem is the file name. Can't you see it? I don't know how the **** it's renamed.

---

### Post by miLl3niUm on 2007-07-03
Anyone?

---

### Post by slimdog360 on 2007-07-03
I usually open it in thunar or whatever, click show hidden files, then cut and paste the .trash out of the folder.

---

### Post by miLl3niUm on 2007-07-03
Thank you, I'll try it.

---

### Post by miLl3niUm on 2007-07-03
I can't because of the file name:

```
Failed to determine file info for "file:///media/MILL3NIUM/.Trash-alter/Trasr/untitled%20folder/Ardamax/%C2%A0v%C3%B1%E2%8C%A1%17y%C3%A6%E2%95%92.%C3%BC%E2%96%8Cj".
```

---

### Post by miLl3niUm on 2007-07-03
I need it in few hours. I am going on vacation and I'll be back on Friday.

Thank You.

---

### Post by Swankyman on 2007-07-03
Hi

I think your problem is the same as my problem. 

You have files on the usb with strange names full of weird symbols and ubuntu can't delete them. The only way I know to get around this is to format the disk

I think it comes from removing the drive before all the data was written to it!!!!

Rich

---

### Post by miLl3niUm on 2007-07-03
This is exactly my problem. I also tried to format it but I don't know how.
How can I format my USB?

---

### Post by Swankyman on 2007-07-03
ok quick easy way is install 

gparted


Rich

---

### Post by miLl3niUm on 2007-07-03
Omg, I did something and I can't mount it now.

EDIT: Yay!! I made it, thank you all.

---

