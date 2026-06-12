---
title: "Tar Files Extraction Range."
date: 2015-02-06
forum: General Help
---

### Post by Mohsin_khalid on 2015-02-06
hello guys

i am using following command for Extraction tar files.
what i want is i have to change date again and again. i dont want to change date. just want to give Range 

please tell me how to give Range for extraction like if you see date 22112014 in below line.


/application/untar.sh "/media/250/images/0822/22112014/*.tar.gz" /media/250/images/0822/22112014/;


Regards

---

### Post by TheFu on 2015-02-06
Can you not use regex for pattern matching.
[https://www.gnu.org/software/tar/manual/html_chapter/tar_6.html](https://www.gnu.org/software/tar/manual/html_chapter/tar_6.html)

---

