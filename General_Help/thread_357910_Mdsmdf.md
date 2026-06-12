---
title: "Mds/mdf"
date: 2007-02-10
forum: General Help
---

### Post by Rhaddad on 2007-02-10
Hello,
how can i burn these types of images on a CD via Ubuntu

---

### Post by zorkerz on 2007-03-19
Im looking for the same thing.

---

### Post by SBFC on 2007-03-19
You could mount the image file and then copy all the files inside of it, and then burn it.

```
mount file.mdf /mountpath -t iso9660 -o loop
```

I usually mount such files to /media/cdrom0.

---

### Post by zorkerz on 2007-03-19
the mounting has not worked for me yet.
[http://wiki.linuxquestions.org/wiki/CD_Image_Conversion]("http://cd%20image%20conversion/") this site has some solutions
and there is a program in the repositories called mdf2iso that converts mdf into iso.  However im not sure what this does with the copy protection.

---

### Post by Al Biheiri on 2008-06-27
Thank you. This program is what I needed. Although I must tell ppl thats NOT a UI only terminal..

---

