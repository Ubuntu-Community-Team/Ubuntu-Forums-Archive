---
title: "Unetbootin and dd not working"
date: 2016-11-25
forum: General Help
---

### Post by entropie2 on 2016-11-25
Hello, 

I am new to the forums and thought maybe you can help me with a problem, I am having for some time now. I am using ubuntu with xfce and it appears that I am doing something wrong, when it comes to creating bootable OS'es from images. I tried to copy retropie, an image for the raspberry pi to the SD card yesterday and it did not work. First of all I did it via the simple "dd if=x of=x" command and it worked for some time, showing me in the end the process was successful. Yet the end result was a SD with unknown file system and nothing on it. The starting format of the SD was FAT32. I then downloaded unetbootin, added the new repository as said on the official page and unetbootin gets stuck at the first step (downloading software), tho I have the image on the harddrive. Then after a while the programm just finishes, saying its done but it isnt. The SD card I get is still FAT32 and there are some files on it, all related to unetbootin but no OS was created. I tried the same with an USB stick and even tried another image file, in this case raspian OS, and again some files are copied, all related to unetbootin but no OS.

I have the feeling that something in the process of re-partioning the disc, is already not working. Cause, except for the dd command that destroyed the filesystem, nothing in the filesystem changes. No boot partition or anything is created. So maybe it could be a rights thing. Ofc I did both commands, dd and unetbootin with sudo. 

Do you maybe have an idea? I am currently searching for my SD to USB stick and will try flashing the OS from my raspberry. If you have any ideas, I am thankful for your help.

Greetings,
ent

---

### Post by sudodus on 2016-11-25
Welcome to the Ubuntu Forums :-)

I checked at the RetroPie site.

1. It is important that you check with md5sum, that the download was successful

```
$ md5sum retropie-4.1-rpi1_zero.img.gz
53b3c455a134f1314979350213cb2ba0  retropie-4.1-rpi1_zero.img.gz
```

or

```
$ md5sum retropie-4.1-rpi2_rpi3.img.gz
4bf44fa37bb9db72b9d7c6dfab6fe015  retropie-4.1-rpi2_rpi3.img.gz
```

2. You can use mkusb to flash directly from the img.gz file to a memory card. mkusb will expand the compressed file and flash it automatically, and it wraps a safety belt around dd, to help writing to the correct target device, the card, and not another drive. See this link (and links from it),

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

Good luck :-)

---

### Post by entropie2 on 2016-11-28
Thank you ! That worked like a charm :).

---

### Post by sudodus on 2016-11-28
Congratulations :KS

Please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

