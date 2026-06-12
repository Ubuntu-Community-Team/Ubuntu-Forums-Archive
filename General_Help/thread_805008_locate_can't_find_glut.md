---
title: "locate can't find glut"
date: 2008-05-23
forum: General Help
---

### Post by JayeD on 2008-05-23
I have glut installed on my pc, and can find the file in /usr/local/include/GL but when I type locate -i glut.h I get nothing back. I can do locate -i gl.h and I get the file in the same folder found, but not glut.h. I have tried locate glu and I find a couple of files in the folder, but not glut.h, nor freeglut.h. Any ideas why this would be?

---

### Post by ibuclaw on 2008-05-23
```
sudo updatedb
```
Then try it.

Regards
Iain

---

### Post by JayeD on 2008-05-23
lol, I'm such a noob. Thanks very much :)

---

### Post by ibuclaw on 2008-05-23
There is no need to put yourself down...

Thanks to a huge community of people learning off each other, you can go to sleep today knowing that you know one more thing about Linux!

It's a proud feeling...

Iain

---

