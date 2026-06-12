---
title: "Can't mount external drive, appears as USB Drive"
date: 2008-04-26
forum: General Help
---

### Post by HermanChess on 2008-04-26
I've never had this problem before. I have an 80gb usb external drive and it has always mounted without a problem, displaying it's name. Recently I unmounted it and disconnected it to connect it to another ubuntu box, running Hardy (the same as me). It didn't connected there, and it won't connect in my box anymore, I'm assuming it didn't unmounted properly. When I connect it in my box it show "USB Drive" but I can't mount it, it shows "Can't mount file" or "No media in the drive" . 

Is there a way to FIX the drive, it is formated in NTFS. Any ideas ?? 

Thanks.

---

### Post by dcstar on 2008-04-26
> **HermanChess said:**
> I've never had this problem before. I have an 80gb usb external drive and it has always mounted without a problem, displaying it's name. Recently I unmounted it and disconnected it to connect it to another ubuntu box, running Hardy (the same as me). It didn't connected there, and it won't connect in my box anymore, I'm assuming it didn't unmounted properly. When I connect it in my box it show "USB Drive" but I can't mount it, it shows "Can't mount file" or "No media in the drive" . 

Is there a way to FIX the drive, it is formated in NTFS. Any ideas ?? 

Thanks.

```
sudo fsck /dev/whatever-the drive-is
```

Or use the "Check" function in System-Partition Editor (does the same thing).

---

### Post by HermanChess on 2008-04-26
Ok the problem is I don't exactly remember the name of the drive, and gparted won't show the drive. I'm I supposed to know the name or /dev/sda(something) by memory, or is there some way to see it?

---

### Post by dcstar on 2008-04-26
> **HermanChess said:**
> Ok the problem is I don't exactly remember the name of the drive, and gparted won't show the drive. I'm I supposed to know the name or /dev/sda(something) by memory, or is there some way to see it?

```
fdisk -l
```

---

### Post by HermanChess on 2008-04-26
Right. I remember I used to see my external drive in fdisk -l , but now it won't show, it just shows the main drive and swap, it means Ubuntu is not recognizing it. What is there to do?

---

### Post by dcstar on 2008-04-26
> **HermanChess said:**
> Right. I remember I used to see my external drive in fdisk -l , but now it won't show, it just shows the main drive and swap, it means Ubuntu is not recognizing it. What is there to do?

Download a partition repair CD and see if you can recover your drive.

---

### Post by HermanChess on 2008-04-26
:popcorn:  arghh I'm starting to get nervous ... I have all my 60gb of music in there, I can't lose it :( 

Where can I find one of these repair cd's ?

---

