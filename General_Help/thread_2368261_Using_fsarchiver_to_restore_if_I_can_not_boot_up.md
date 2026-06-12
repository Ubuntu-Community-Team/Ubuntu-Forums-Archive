---
title: "Using fsarchiver to restore if I can not boot up"
date: 2017-08-08
forum: General Help
---

### Post by raleigh3 on 2017-08-08
I have been using fsarchiver and putting the images on a separate internal drive.

But if a time comes when I can no longer boot up, how can I use fsarchiver restore my primary drive ?

Fsarchiver is not on my install disk.

---

### Post by raleigh3 on 2017-08-08
I just found out that SystemRescue CD has fsarchiver on it.

---

### Post by VMC on 2017-08-08
*Clonezilla* also has *fsarchiver* program installed.

---

### Post by monkeybrain20122 on 2017-08-08
> **raleigh3 said:**
> I have been using fsarchiver and putting the images on a separate internal drive.

But if a time comes when I can no longer boot up, how can I use fsarchiver restore my primary drive ?

Fsarchiver is not on my install disk.


You can use a systemrescue cd as you have said, or just boot from a ubuntu live usb and install fsarchiver and then run resfs from there (with your external hd where the image is connected of course)

---

### Post by raleigh3 on 2017-08-09
So I could install fsarchiver on a drive with no O.S. ?

But then, I would still have to use a CD to bootup.

I already made the systemrescue CD.

---

### Post by raleigh3 on 2017-08-09
> **VMC said:**
> *Clonezilla* also has *fsarchiver* program installed.

Thanks. I have a flash drive with Clonezilla.

And it boots faster that a CD.

---

### Post by monkeybrain20122 on 2017-08-09
> **raleigh3 said:**
> So I could install fsarchiver on a drive with no O.S. ?

But then, I would still have to use a CD to bootup.

I already made the systemrescue CD.
No, you install it in the live usb form which you boot, then restore the image to the target hard drive. You have the internal hard drive, the live usb (don't even bother with CD) and the other drive where your image is stored. You install and run fsarchiver from the live usb with command like
```

sudo fsarchiver [COLOR=#000000]restfs /path/to/image id=0,dest=/dev/sda1[/COLOR]
```

where /path/to/image is the path to where the .fsa file is as seen in the live session and /dev/sda1 (say) is your internal drive where you want to restore to.

---

### Post by raleigh3 on 2017-08-09
I am confused.

If I can not normally boot, I have to boot from either a CD or flash drive.

---

