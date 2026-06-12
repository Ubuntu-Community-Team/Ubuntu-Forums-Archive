---
title: "Anyone know of linux program to recover corrupted jpeg files"
date: 2015-05-23
forum: General Help
---

### Post by Ralph L on 2015-05-23
I recently came back from a trip and found that about 100 photos that I took with a Canon sx280hs camera were unreadable off the micro sd card.  They are all in a sequence at the end of the card (the earlier photos are fine) and all give the same error ```
Error interpreting JPEG image file (Not a JPEG file: starts with 0xff 0xff)
```.  Somehow the camera screwed up recording jpeg images (the videos that were intermixed were fine).  I am looking for a program that could repair the jpeg files and run under linux.  I found some that run under windows, but my windows capability is limited.  
Any help is appreciated...

---

### Post by tgalati4 on 2015-05-23
Install *testdisk* and use *photorec* (photo recovery) to attempt file recovery.

Open a terminal:

```
sudo apt-get install testdisk
man photorec
```

---

### Post by Ralph L on 2015-06-01
tgalati4:  Thank you very much for responding.  I finally did a hex dump of the bad jpeg images and it appears that the camera malfunctioned and wrote 1 bits repeatedly to the entire file.  So nothing is going to bring that back.  Anyway, thanks again.

---

### Post by tgalati4 on 2015-06-01
Did the camera get wet?  I would send an email to Canon explaining your situation.  Send them the camera to investigate.  You may be surprised by their response.

---

