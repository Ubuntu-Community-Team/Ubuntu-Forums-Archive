---
title: "convert does not work from jpg to pdf"
date: 2018-12-09
forum: General Help
---

### Post by marchello_lippi2 on 2018-12-09
Hi all, 
The **convert** console program does not work for me when I try to convert file from jpg to pdf format. 
It does work when I convert from tiff to jpg though.

```

convert ~/folder1/file.jpg ~/folder1/file.pdf
convert: not authorized `/home/user1/folder1/file.pdf' @ error/constitute.c/WriteImage/1028.

```

I thought it is something with access rights, however it is my home folder... 
Anyway, tried with sudo, but error message was the same. 

Not urgent at all, because I was able to convert it using **gimp**.

Please advise.

---

### Post by barbablu on 2018-12-09
Same problem here on Ubuntu 16.04.5.  It used to work.

---

### Post by marchello_lippi2 on 2018-12-09
> **barbablu said:**
> Same problem here on Ubuntu 16.04.5.  It used to work.
As I can see, it worked for me few months ago. Then stopped working after some update. 

Usually updates should improve program, isn't it? )

---

### Post by vanadium on 2018-12-09
This is because security related to working with PDF was implemented. See here: [https://askubuntu.com/questions/1081895/trouble-with-batch-conversion-of-png-to-pdf-using-convert/1081907#1081907](https://askubuntu.com/questions/1081895/trouble-with-batch-conversion-of-png-to-pdf-using-convert/1081907#1081907)

---

### Post by brandonall14 on 2019-05-07
I looked up a number of solutions for this problem and the best one I found was Total Image Converter. You can also try it by visiting [https://www.coolutils.com/TotalImageConverter](https://www.coolutils.com/TotalImageConverter)

---

