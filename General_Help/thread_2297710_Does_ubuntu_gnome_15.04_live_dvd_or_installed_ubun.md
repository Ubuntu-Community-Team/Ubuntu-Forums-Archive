---
title: "Does ubuntu gnome 15.04 live dvd or installed ubuntu gnome 15.04 support GPT?"
date: 2015-10-06
forum: General Help
---

### Post by i12 on 2015-10-06
Does ubuntu gnome 15.04 live dvd or installed ubuntu gnome 15.04 support GPT?
Shall I make GPT partitions with parted?

---

### Post by oldfred on 2015-10-06
I have used gpt with both my old BIOS system since 10.10 and now with my new UEFI system.
It will use gpt automatically if you install in UEFI boot mode by booting installer in UEFI mode.
Or it will default to gpt if drive is blank and somewhat over 1.5TB. You have to use gpt if drive is over 2TB.

        I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning....
You also can use gdisk which is the fdisk for gpt partitioned drives.
      
 [http://www.rodsbooks.com/gdisk/walkthrough.html](http://www.rodsbooks.com/gdisk/walkthrough.html)
[http://www.rodsbooks.com/gdisk/advice.html](http://www.rodsbooks.com/gdisk/advice.html)

---

