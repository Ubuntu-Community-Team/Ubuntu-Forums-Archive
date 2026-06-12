---
title: "Best compression"
date: 2007-11-22
forum: General Help
---

### Post by malfist on 2007-11-22
I was looking at the announcement warning about malicious commands being posted on the forums here, and it mentioned about a decompression explosion. It said a relatively small file to contain GB's of compressed data, and I"m wondering how that is.  I've compressed GB's of files before using the 'best' compression gzip can give, and at best it will shave off 10-20MB per GB. 

How can I compress gigabytes into a 'relatively small file'?

---

### Post by mister_pink on 2007-11-22
I imagine this is because when you were compressing data it was real (randomish) data, which would be difficult to compress. One of these bombs presumably is made of some regular repeating data so that huge compression ratios could be achieved. (imagine a million files all containing nothing but zeros). In reality I would think that the zip would be made exploiting something about zip archives rather than actually creating the files and compressing them.

---

### Post by malfist on 2007-11-22
Well drats, I wanted to be able to compress all my images and open up a lot of storage space on my harddrive. :(

---

