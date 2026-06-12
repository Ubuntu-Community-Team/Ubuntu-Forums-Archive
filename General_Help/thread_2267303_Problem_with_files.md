---
title: "Problem with files"
date: 2015-02-28
forum: General Help
---

### Post by aarda-uunlu on 2015-02-28
I can't open pictures, PDFs etc. with Nautilus or writing "file:/..asd.jpg" in Chrome, but I can open them when I write "sudo nautilus" in Terminal.

Sorry for bad English.

---

### Post by kc1di on 2015-02-28
Hello aarda-uunlu  and welcome to Ubuntu,

Sounds like a permissions problem- Where on the drive are the files found if they are in your home folder they should be readable by that user. 

[Here is a tutorial]("https://help.ubuntu.com/community/FilePermissions") on file permissions in Ubuntu.

---

### Post by aarda-uunlu on 2015-02-28
i found solution.
sudo chmod -R 755 /home/username/

---

### Post by kc1di on 2015-02-28
Glad you got it going :)

---

