---
title: "File carving with scalpel - taking way too long?"
date: 2013-04-14
forum: General Help
---

### Post by cooperpk on 2013-04-14
Hey everyone

I have searched everywhere and can't seem to find an answer to this...I am using scalpel to carve files out of an image of a disk that was full of read errors and eventually failed. The partition size is 679GB, and the first pass took about 6 hours. It built the carve lists (I set it to recover gif, jpg, png, doc, and wav files - it found about 200 000 matching headers). It has now been running the 2nd pass (where the carving actually occurs) for probably 5 days, and it says it's at 0.9%.
On the first pass, it gave an ETA which was fairly accurate as it progressed. This time, the ETA just read "--:--" which is presumably because it hasn't found the footers yet to determine file size.

What I want to know is whether this second pass is going to read the ENTIRE disk (ie I should cancel because it will take a year) or if it is just counting the size of files it has actually carved. The manual for scalpel states that the second pass is usually faster than the first because it has already located the headers. I don't want to quit the program if it is simply counting the recovered files - it is at 6GB so far. Any help is greatly appreciated!

BASIC SUMMARY: Does the 2nd pass of Scalpel scan and count the entire disk, or does it simply record the size of files recovered thus far (hence no ETA given)?

---

