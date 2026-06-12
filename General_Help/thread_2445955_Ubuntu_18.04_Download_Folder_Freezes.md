---
title: "Ubuntu 18.04 Download Folder Freezes"
date: 2020-06-22
forum: General Help
---

### Post by bludlust2 on 2020-06-22
After a search of this forum, and a general search of the web, I have not been able to find an answer to my specific question. I have Ubuntu 18.04 on a Ryzen3 with 64 GB of memory. Everything works just fine, EXCEPT for my Downloads Folder. Anytime I click on the Downloads folder, there is a significant wait, sometimes as long a 30 seconds, during which the folder is frozen. The rest of the computer runs fine. Sometimes, though, the whole machine will lock up and I have to reboot. Any and all ideas, suggestions, or hints will accepted. This is driving me CRAZY as I use my Downloads folder as my clearing house.

---

### Post by Impavidus on 2020-06-23
When you open a directory in the file manager, it has to scan the contents of the directory, which takes some time if there are many files. 30 seconds sounds excessive. If it has to show thumbnails for your files, it also has to read all files in that directory to generate the thumbnails, which will take far more time. Thumbnails can be cached, but maybe you set it up to automatically clear the cache or put it on tempfs. Disabling thumbnails may help.

---

### Post by ajgreeny on 2020-06-23
What do you mean by "clearing house"?

---

