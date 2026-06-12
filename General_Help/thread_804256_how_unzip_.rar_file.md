---
title: "how unzip .rar file"
date: 2008-05-22
forum: General Help
---

### Post by Golddust on 2008-05-22
I'm completely new with Ubuntu.  How do I unzip a .rar file?  With all the applications that are included in this latest version, there is nothing I can find to carry this out.

---

### Post by CRISM on 2008-05-22
I haven't uses a .rar file before, but this website seems to have info relevant to how you handle them under linux.

[http://www.cyberciti.biz/faq/open-rar-file-or-extract-rar-files-under-linux-or-unix/](http://www.cyberciti.biz/faq/open-rar-file-or-extract-rar-files-under-linux-or-unix/)

---

### Post by deanjm1963 on 2008-05-22
if you have enabled the multiverse repository you should be able to install unrar. once installed all you need to do is right click on the archive and extract it.

hope this helps

---

### Post by strabes on 2008-05-23
Applications > Accessories > Terminal

```
sudo aptitude install rar unrar
```

Right click on the file and select "Extract Here"

---

