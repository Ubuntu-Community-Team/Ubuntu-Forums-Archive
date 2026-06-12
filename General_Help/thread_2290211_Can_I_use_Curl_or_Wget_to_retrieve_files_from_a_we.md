---
title: "Can I use Curl or Wget to retrieve files from a website that asks for credentials?"
date: 2015-08-10
forum: General Help
---

### Post by sarosh2 on 2015-08-10
Hello, I would like to download all my course files from my university website. I have tried to use wget command to get the files and it downloads the files however they are corrupted or fail to open. I have even tried to use the wget and curl command with username and password but it does not work. Is there anyway I can automate the downloading of files as there are more than a 100 files I need to download. I don't know whether it is FTP or not but when I go to the website I always see HTTP in the beginning of the address. Thank you, let me know what other information you need.

---

### Post by howefield on 2015-08-10
Perhaps this is something you could ask your universities IT support, if you already have, what did they say ?

---

### Post by TheFu on 2015-08-10
howefield has a good idea. Perhaps they have a get-everything link?  But beware that sometimes materials are updated during the semester, so getting everything at the start isn't smart.

Many new websites wrap their download in javascript which curl and wget don't support.  OTOH, if you can find the real locations and real file names to download ... 

Firefox has many addons for this stuff.  DownLoadThemAll is one, DownloadHelper is another  .. there are others.

---

### Post by sarosh2 on 2015-08-10
I did ask the IT support guys and they said I will have to download them manually. I am going to try the addons you have suggested TheFu, are they secure/trustworthy?

---

