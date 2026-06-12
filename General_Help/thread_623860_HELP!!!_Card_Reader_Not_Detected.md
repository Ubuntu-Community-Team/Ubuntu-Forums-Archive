---
title: "HELP!!! Card Reader Not Detected"
date: 2007-11-26
forum: General Help
---

### Post by CheeseQueen452 on 2007-11-26
I want to transfer some pictures from my SD card to my hard drive, but it appears that Ubuntu doesn't see my USB card reader. I plugged it in & the light on the card reader lit up, but nothing else happened. I don't see any way of accessing the pictures on the card. I wanted to save battery power in my camera which works fine, so how do I get the card reader to work?

---

### Post by Subban on 2007-11-26
Did you insert the SD Card into the reader, from your description you didn't yet.

The reader itself will most likely have been detected fine and is just waiting on you to put the card in(going off ones I have used)

---

### Post by CheeseQueen452 on 2007-11-26
Yes, I did.

> **Subban said:**
> Did you insert the SD Card into the reader, from your description you didn't yet.

---

### Post by CheeseQueen452 on 2007-11-26
Anyone?

---

### Post by CheeseQueen452 on 2008-01-14
*bump*

---

### Post by Irony on 2008-01-14
Plug the device in an wait till it lights up, then do;

```
sudo fdisk -l
```

I you see it then mount it manually, for example by creating a folder on the desktop and doing something like;

```
sudo mount /dev/sda1 /home/username/Desktop/card
```

to unmount do;

```
sudo umount /home/username/Desktop/card
```

---

### Post by CheeseQueen452 on 2008-01-14
When I plug the reader in, shouldn't it mount automatically, & create an icon on my desktop that I can access as a folder? At least that's what my mp3 player does.... How would manually creating a folder on the desktop help detect a device the computer can't see to begin with? Forgive me, I don't quite understand your instructions. Maybe it's easier to just plug in my camera....


> **Irony said:**
> Plug the device in an wait till it lights up, then do;

```
sudo fdisk -l
```

I you see it then mount it manually, for example by creating a folder on the desktop and doing something like;

```
sudo mount /dev/sda1 /home/username/Desktop/card
```

to unmount do;

```
sudo umount /home/username/Desktop/card
```

---

### Post by Irony on 2008-01-15
Plug the device in an wait till it lights up, then do;

```
sudo fdisk -l
```

If you see it then mount it manually, for example by creating a folder on the desktop and doing something like;

```
sudo mount /dev/sda1 /home/username/Desktop/card
```

to unmount do;

```
sudo umount /home/username/Desktop/card
```

---

### Post by megamania on 2008-01-15
> **CheeseQueen452 said:**
> When I plug the reader in, shouldn't it mount automatically, & create an icon on my desktop that I can access as a folder? At least that's what my mp3 player does.... How would manually creating a folder on the desktop help detect a device the computer can't see to begin with? Forgive me, I don't quite understand your instructions. Maybe it's easier to just plug in my camera....
System -> Preferences (or maybe "settings"? my system is non-english) -> Removable devices

Are the "mount removable..." options enabled?

---

### Post by CheeseQueen452 on 2008-01-15
Yes, it's enabled.

> **megamania said:**
> System -> Preferences (or maybe "settings"? my system is non-english) -> Removable devices

Are the "mount removable..." options enabled?

---

### Post by Irony on 2008-01-15
Plug the device in an wait till it lights up, then do;

```
sudo fdisk -l
```

Paste the output here.

---

