---
title: "No space left on device Error, even with plently of free space."
date: 2007-11-20
forum: General Help
---

### Post by desudesudesu on 2007-11-20
I am trying to move an ISO to my memory stick for my PSP, the ISO is ~650MB, and the memory stick has 1.5GB free.

I've tried using thunar, and cp.

I am wary of reformatting it, since I've had nothing but bad experiences with either copying files to flash devices, copying files from them, and it is nearly impossible to reformat them to work with anything but linux.

I don't see how linux can have so many problems with what should be a simple and essential action.

---

### Post by taurus on 2007-11-20
What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
df -h
```

---

### Post by Zimmer on 2007-11-20
Have you used linux to delete files from the device?
If so, then there may be 'hidden' .trash folders using the space

mount the usb and look for the hidden files.

Have had this issue before with a USB mp3 player

---

### Post by desudesudesu on 2007-11-20
My PSP won't even read it anymore.
Neither will my grandfather's Windows PC.

I guess it was just a defective card.

Sorry for the false alarm, 
At least it's under warranty.

---

