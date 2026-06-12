---
title: "Fixing corrupt Jpeg files"
date: 2017-10-09
forum: General Help
---

### Post by dult on 2017-10-09
Hello,

First of all sorry if this is the wrong forum and if this question has been asked before, but I haven't found a solution that applies to my situation.

I transfered some photos from my camera to my pc and then to an external HDD, deleting them from the PC. They were fine and I was able to see them.

I then had to transfer to the PC and to the external HDD because I needed the space on the HDD.
 
In one of these transfers an error must have occured because most pictures don't open and they just give this error:
Error interpreting JPEG image file (Not a JPEG file: starts with 0xff 0xff)
The images aren't zeroed and have >4mb size.

I have tried the following:


[LIST]
[*]Opening with GIMP: can't open;
[*]Open or convert with Image Magick: can't open;
[*]Change extension and open: can't open;
[*]File IMG_1209.JPG: It says its just Data;
[*]Put on USB drive and use PHOTOREC: Can't find images;
[*]Put on USB drive and use Recuva: Can't find images;
[*]Open with HEX editor and add header: Couldn't add a header, not technical savvy enough, files aren't zeroed though.
[/LIST]

Is there any program to recover these files?

Oh, there is also an mp4 file...

Best regards
NP

---

### Post by dragonfly41 on 2017-10-09
Some other ideas to try ...

(1) Can you try deleting file(s) extension and open without jpg extension?

(2) Can you use photorec (from LiveUSB) on your original camera flash memory to try to recover from source (even though deleted when copying to PC)?

(3) Can you use photorec on your PC to try to recover?

[p.s.] another thread  [https://stackoverflow.com/questions/8048067/converting-jpeg-in-text-format-from-email-message-source-back-into-jpeg](https://stackoverflow.com/questions/8048067/converting-jpeg-in-text-format-from-email-message-source-back-into-jpeg)

---

### Post by ajgreeny on 2017-10-09
If you use the file command on one of those corrupt jpg files you may get a clue about the problem.

Here's a typical output from one of mine.
> file title.JPG 
title.JPG: JPEG image data, JFIF standard 1.01, resolution (DPI), density 180x180, segment length 16, Exif Standard: [TIFF image data, little-endian, direntries=11, manufacturer=Panasonic, model=DMC-FZ38, orientation=upper-left, xresolution=166, yresolution=174, resolutionunit=2, software=GIMP 2.8.10, datetime=2015:10:02 12:12:44], baseline, precision 8, 718x918, frames 3

What do you see?

---

### Post by dult on 2017-10-10
> **dragonfly41 said:**
> Some other ideas to try ...

(1) Can you try deleting file(s) extension and open without jpg extension?

(2) Can you use photorec (from LiveUSB) on your original camera flash memory to try to recover from source (even though deleted when copying to PC)?

(3) Can you use photorec on your PC to try to recover?

[p.s.] another thread  [https://stackoverflow.com/questions/8048067/converting-jpeg-in-text-format-from-email-message-source-back-into-jpeg](https://stackoverflow.com/questions/8048067/converting-jpeg-in-text-format-from-email-message-source-back-into-jpeg)


These photos are over 6 months old and I've filled my card allot of times, as did the PC, because I shoot a lot of video. I'll try it though.

> **ajgreeny said:**
> If you use the file command on one of those corrupt jpg files you may get a clue about the problem.

(...)

What do you see?

Though I'll try it again, it just says "data".

Thanks.

---

### Post by dult on 2017-10-30
Well, to sum up. I will try to recover from my camera, because every windows program I tried to fix the photos "fixed" them into a bunch of garbage data.

Thanks to everyone.
Best regards.

---

