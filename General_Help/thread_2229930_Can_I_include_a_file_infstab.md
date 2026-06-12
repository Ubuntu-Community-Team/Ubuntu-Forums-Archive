---
title: "Can I include a file infstab?"
date: 2014-06-16
forum: General Help
---

### Post by markosjal on 2014-06-16
I want to know if I can include an external file in fstab and what is the syntax to do that?

---

### Post by slickymaster on 2014-06-16
Moved to the **General Help** sub-forum.

---

### Post by yancek on 2014-06-16
You might explain what your intentions are, what you want to accomplish.

---

### Post by jimmyh1972 on 2014-06-16
The fstab is a file itself place in /etc
Its job is to tell the system what devices to mount where to mount it in what filesys etc...
Its not a script and you cant include files in it. Its only a configuration file. I think its better for you to write what's your goal and we'll try to help

---

### Post by markosjal on 2014-06-18
To explain it most simply , My goal is to create a file in a userspace with mounts to mount at startup. This file could be modded by me or any user actually. 

I just want to know if I can put an include in some way in fstab, sorry but that is what I am looking to do,. and although some answers may mean well I am interested only in that possibility as I have a plan B already

---

### Post by slickymaster on 2014-06-18
See if [this]("http://unix.stackexchange.com/questions/62819/can-i-include-another-file-in-fstab") can somehow point you in the right direction.

---

