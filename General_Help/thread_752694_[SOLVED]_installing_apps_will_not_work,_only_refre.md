---
title: "[SOLVED] installing apps will not work, only refreshes list"
date: 2008-04-11
forum: General Help
---

### Post by cyc on 2008-04-11
I have been looking everywhere and I can't see to find an answer to my problem.

The following happens when I try to install applications from the Applications -> Add/Remove or when I try to open a mp3 player and it asks for codecs.

-I check on the box to install my applications.
-It says that the list of application is not available and "Click Reload to load it..."
-I click on Refresh.
-It downloads the package information and I'm back to where I was.
-I click on the checkbox again and the whole process repeats.

Anyone have any idea on why this is happening? :confused:


Thanks

---

### Post by SOULRiDER on 2008-04-11
Run
```
sudo aptitude update
```in a terminal and paste the output here, lets see if theres an error.

---

### Post by cyc on 2008-04-11
> **SOULRiDER said:**
> Run
```
sudo aptitude update
```in a terminal and paste the output here, lets see if theres an error.

I finally found the source of my errors. I only had to go to System -> Administration -> Software Sources and check the boxes to allow Ubuntu to install applications. Thanks for the help!

---

