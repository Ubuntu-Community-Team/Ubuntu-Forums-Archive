---
title: "&lt;&lt; USB driver not recognized after mkusb wipe &gt;&gt;"
date: 2019-03-01
forum: General Help
---

### Post by icamps on 2019-03-01
Hello,

I have an USB driver that was used as a Live Boot Linux tools. Well, it is a micro SD card used in an USB adapter.

I just want to get it back to normal state.

 I tried `gparted` or similar, unsuccessfully. 

So, I found a reference to use `mksub`. After doing a full wipe, the drive is not recognized either from Linux or Windows in my note either in other two Windows boxes and other one Linux box. Also, I tried plugin it to my Android phone with OTG and in my camera.

Any ideas?

Thanks in advance.

Camps

---

### Post by tea for one on 2019-03-01
> **icamps said:**
> 
 I tried `gparted` or similar, unsuccessfully. 

Did you add a partition with gparted?

I think that **mkusb wipe** will remove all the data and partitions from the micro SD card and you have to then reformat it with another operation.

---

### Post by C.S.Cameron on 2019-03-01
Not just a partition, first you also need a partition table.
Use mkusb "restore to a Standard storage device".

---

### Post by vidtek on 2019-03-02
> **icamps said:**
> Hello,

I have an USB driver that was used as a Live Boot Linux tools. Well, it is a micro SD card used in an USB adapter.

I just want to get it back to normal state.

 I tried `gparted` or similar, unsuccessfully. 

So, I found a reference to use `mksub`. After doing a full wipe, the drive is not recognized either from Linux or Windows in my note either in other two Windows boxes and other one Linux box. Also, I tried plugin it to my Android phone with OTG and in my camera.

Any ideas?

Thanks in advance.

Camps

If you can't get it to be recognised, try putting it back into your camera and formatting in there.

---

### Post by icamps on 2019-03-05
[ 						 							]("https://ubuntuforums.org/member.php?u=1219471")@vidtek I already did that with my camera and with my phone. It was not recognized.

---

### Post by icamps on 2019-03-05
@tea.for.one and @C.S.Cameron It is not recognized by Linux, so, I can not associate any /dev/sdX to it.

---

### Post by tea for one on 2019-03-06
Have you tried all the usual hardware checks such as:-

Use a different USB port?
Try a different micro SD card in your USB card reader?
Try the USB card reader on another PC?

Is the card recognised by **gnome-disk-utility**?

There are some options to explore there.

Best wishes

---

### Post by icamps on 2019-03-06
> **tea for one said:**
> Have you tried all the usual hardware checks such as:-

Use a different USB port?
Try a different micro SD card in your USB card reader?
Try the USB card reader on another PC?

Is the card recognised by **gnome-disk-utility**?

There are some options to explore there.

Best wishes

Answering your questions:
Yes
Yes
Yes

Yes. I tried to format, create partition, restore partition but all the options are grayed out. The only available is *Edit Mount options...*, but I already play with it, unsuccessfully.

---

### Post by tea for one on 2019-03-06
As **gnome-disk-utility** recognises your micro SD card, is the delete option available (i.e. the minus sign)?

---

### Post by icamps on 2019-03-06
> **tea for one said:**
> As **gnome-disk-utility** recognises your micro SD card, is the delete option available (i.e. the minus sign)?

Nope, only a *gear* symbol.

---

### Post by tea for one on 2019-03-06
Well, that is a bit unusual because **gnome-disk-utility** should also see your existing hard drive and partitions?

---

### Post by icamps on 2019-03-06
> **tea for one said:**
> Well, that is a bit unusual because **gnome-disk-utility** should also see your existing hard drive and partitions?

Sorry, I may could misunderstand your request.  **gnome-disk-utility** is recognizing all the other existing hard drive, right now, I have plugged in and external HD and a mounted ISO, and both are recognized.

The difference is that for all other HD I have options to format, recover partition, make a partition, etc. but not for the swiped USB drive.

---

### Post by tea for one on 2019-03-06
OK, **gnome-disk-utility** seems to be performing as expected.

Here's a shot in the dark, why not fire up **mkusb**, see if it identifies your SD card and then try and burn your ISO again.

You never know, it may restore it back to something that **gparted** and/or **gnome-disk-utility** may recognise.

Lastly, can you post the output from the following commands with only your usual hard drive and the micro SD card plugged in?

```
sudo fdisk -l
```

```
sudo parted -l
```

---

### Post by dragonfly41 on 2019-03-06
Perhaps switch tactics and try in your Windows OS.

[https://www.easeus.com/partition-master/sd-card-wont-format.html](https://www.easeus.com/partition-master/sd-card-wont-format.html)

Could perhaps the micro SD card be write protected?

---

