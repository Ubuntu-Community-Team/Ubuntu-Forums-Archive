---
title: "LED Not Working for SATA Activity"
date: 2006-12-13
forum: General Help
---

### Post by esaym on 2006-12-13
I have an older abit nf7-s v2 mother board that I just installed 6.06 on last night.  I noticed that even while running the live cd the led for hard drive activity was not working for sata activity.  I still does however work when the pata drives are accessed.  The board has a built in 2 port sil3112 sata controller.

Anyone ever heard of this?  Doing a search I found a bunch of people that had a problem with the light staying on with other motherboards but I haven't found any problem like mine..](*,)

---

### Post by Spitfire567 on 2006-12-13
I have a built in sil3112 SATA controller as well (on an Asus A7N8X deluxe) and the hard drive activity LED has never lit up when my SATA drive is accessed.  I don't think it was designed to do that.  I have worked with a few other motherboards that have a built in SATA controller, which is not integrated into the motherboard chipset, and they do not activate the hard drive LED as well.  

You say its an older board, did it use to work with some other operating system?  Is the SATA drive a new addition to the computer?  Are there separate pins to attach a different LED to the sil3112 controller?

---

### Post by esaym on 2006-12-13
> **Spitfire567 said:**
> I have a built in sil3112 SATA controller as well (on an Asus A7N8X deluxe) and the hard drive activity LED has never lit up when my SATA drive is accessed.  I don't think it was designed to do that.  I have worked with a few other motherboards that have a built in SATA controller, which is not integrated into the motherboard chipset, and they do not activate the hard drive LED as well.  

You say its an older board, did it use to work with some other operating system?  Is the SATA drive a new addition to the computer?  Are there separate pins to attach a different LED to the sil3112 controller?
No everything works fine in windows.  I am on 56k right now so I can't do research.  However I did a hdparm -Tt and I got a read of 20mbs so something is not right.  I tried to enable dma but I got an error saying I didn't have the correct ioctl..hmm

---

### Post by esaym on 2006-12-16
Anyone else with this kind of problem?

What is everyone getting with hdparm -Tt?

---

### Post by Spitfire567 on 2006-12-16
> **esaym said:**
> What is everyone getting with hdparm -Tt?

```
/dev/sda:
 Timing cached reads:   1452 MB in  2.00 seconds = 725.75 MB/sec
 Timing buffered disk reads:  154 MB in  3.00 seconds =  51.26 MB/sec


```

I found another thread where someone else is having problems enabling DMA on a SATA drive.   It appears that hdparm cannot control SATA drives.

[http://ubuntuforums.org/archive/index.php/t-29443.html]("http://ubuntuforums.org/archive/index.php/t-29443.html")

There were some links with more information there that might help you.

---

