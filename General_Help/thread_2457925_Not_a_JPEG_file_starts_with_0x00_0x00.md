---
title: "Not a JPEG file: starts with 0x00 0x00"
date: 2021-02-12
forum: General Help
---

### Post by mountainman70 on 2021-02-12
I recently had to reinstall Ubuntu 20.04  & W10 on a dual boot. I had copied my docs & pics to a flash drive to reinstall. I have over 50 folders with 50 to over a hundred photos in them. After installing the photos the folders that I opened to check where good. I have since discovered that some folders don't show all the pictures. 

This is what I get: Error interpreting JPEG image file (Not a JPEG file: starts with 0x00 0x00). 

Each pics has a different number at the end.  How do I correct this? 

Thanks for any replys.

---

### Post by HermanAB on 2021-02-12
The first bytes of a picture file is a 'magic number' that defines the picture file type.  The utility which interprets that is called 'file'.  The magic number of a JPEG file is supposed to be FF D8 FF DB. 

Some more info here: [https://en.wikipedia.org/wiki/List_of_file_signatures](https://en.wikipedia.org/wiki/List_of_file_signatures)

You can look at and modify files with the program 'hexedit'.

Some editors are more persnickety about the magic number than others, so try to find an editor/viewer that doesn't care so much.

---

### Post by mountainman70 on 2021-02-12
Is there a program that I can download to correct this problem?

---

### Post by HermanAB on 2021-02-12
Not that I'm aware of - first you need to know what the problem is exactly.  Try hexedit and the jpeg file specification and look at a few files.

---

### Post by mountainman70 on 2021-02-13
I have not been able to find a solution to my problem. I tried a couple of Pro Recover Programs on a trial basis to see if they could recover anything. I was going to buy one if it worked. But they  failed.

However I have found some old cd's that had all my old pictures on them and was able to replace the corrupted ones. I still had the newer ones on my Iphone and after much searching and matching was able to replace the corrupted newer ones. I now have all of my pictures back and have saved them to an old 140 gb HD plus several dvd's. I still have one folder that has three corrupted pics in it. Don't know what they are but will keep experimenting with them.

---

### Post by ajgreeny on 2021-02-13
My memory may be playing tricks on me but I think gimp has in the past opened jpg files that were corrupt like yours were.

I may be remembering wrongly but if you have gimp installed it might be worth trying if you still have any of the corrupt files remaining.

---

