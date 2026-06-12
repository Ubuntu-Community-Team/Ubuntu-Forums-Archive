---
title: "TestDisk Help."
date: 2007-07-21
forum: General Help
---

### Post by Roasted on 2007-07-21
I've got an SD card here. It has about 200-300 pictures on it. Randomly, the camera said the SD card was unusable and kept asking me if I wanted to format it. I kept saying no. Here I am at my Linux machine trying to use TestDisk to recover what pictures were on the card and I am unable to do so.

After analyzing the disk, I'm supposed to get some partitions up, right? Well, I don't.

What else can I do? Is there other software that's better?

HELP!!

---

### Post by az on 2007-07-21
> **Roasted said:**
> I've got an SD card here. It has about 200-300 pictures on it. Randomly, the camera said the SD card was unusable and kept asking me if I wanted to format it. I kept saying no. Here I am at my Linux machine trying to use TestDisk to recover what pictures were on the card and I am unable to do so.

After analyzing the disk, I'm supposed to get some partitions up, right? Well, I don't.

What else can I do? Is there other software that's better?

HELP!!
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
Use (gnu)ddrescue to image the card and then use foremost or photorec to recover the files from the image.

---

### Post by Roasted on 2007-07-21
I did, however, either I'm incredibly stupid or the directions are kind of ridiculous. I can't even get the program to launch with the method they're describing.

---

### Post by Polygon on 2007-07-21
Try photorec first

so first, install testdisk (which includes photorec)

sudo apt-get install testdisk

now, if your wanting to rescue stuff off your card, so plug in your camera or whatever, and then run

sudo photorec

and it should list your card or camera and then start to recover stuff

NOTE: make sure your in the directory that you want photorec to save all your data in!

---

### Post by Roasted on 2007-07-21
It found 309 items and put them in a directory in my home folder. However, I cannot get into it; permission denied.

I figured I'd try a sudo cd [dir] at terminal but sudo cd isn't a valid command.

How can I access the folder?

EDIT - cancel that. I just granted 777 chmod rights to it.

---

### Post by init1 on 2007-07-21
This shouldn't be here. This should be in "General Help". But I am glad it is working now.

---

### Post by Roasted on 2007-07-22
Well, whatever. There's so many f'n sub categories here I just pick one cause they're all the same to me.

Back on the problem, I recovered 309 items from the SD card, however only 179 of them are in .jpg format. A lot of the remaining ones are in .txt format. I found a thread on here talking about converting them from txt to jpg, however I'm running into a problem.

jason@jason:~/Desktop$ convert f8584.txt f8584.pbm
convert: Improper image header `f8584.txt'.

Improper image header? How do I get around that?

---

### Post by az on 2007-07-22
> **Roasted said:**
> Well, whatever. There's so many f'n sub categories here I just pick one cause they're all the same to me.

Back on the problem, I recovered 309 items from the SD card, however only 179 of them are in .jpg format. A lot of the remaining ones are in .txt format. I found a thread on here talking about converting them from txt to jpg, however I'm running into a problem.

jason@jason:~/Desktop$ convert f8584.txt f8584.pbm
convert: Improper image header `f8584.txt'.

Improper image header? How do I get around that?

That other thread is about converting a jpg file of a scanned page of text into a text file using OCR (Optical Character Recognition).  You cannot convert some text into a jpeg image using netpbm.

If the files are corrupt, I would suggest using gnu ddrescue to read the card over and over until you get an error-free image of the card.  Since you describe the problem as being intermittent, this may work.  If you have already done this and there are no errors, then your data is just not there.

---

### Post by bapoumba on 2007-07-22
Thread moved to "General Help".

---

