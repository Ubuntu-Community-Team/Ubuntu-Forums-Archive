---
title: "compressed format question"
date: 2006-09-08
forum: General Help
---

### Post by TheRingmaster on 2006-09-08
when I download a tar.gz (just an example) and extract it to the desktop is it ok to delete that tar.gz file?:mrgreen:

---

### Post by daller on 2006-09-08
After extracting the file, you probably don't need the tarball (the tar file) again...

The extracted folder is a dublicate of the tarball's content, not a pointer!

---

### Post by TheRingmaster on 2006-09-08
thanks!

---

### Post by TheRingmaster on 2006-09-09
now that I have uncompressed my file (opera web browser that I downloaded from their site) how do I create a desktop shortcut to open it. I have tried for hours with no luck.

---

### Post by elettronicha on 2006-09-09
If you want to install Opera, you can also add this repository to your /etc/apt/sources.list:

> deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) unstable non-free

---

### Post by TheRingmaster on 2006-09-09
> **elettronicha said:**
> If you want to install Opera, you can also add this repository to your /etc/apt/sources.list:
what does that unstable part mean?

ok I added that to my respositories and then reloaded synaptic. I look down where opera is supposed to be and I have two opera's available. 

1) opera version 9.01-20060728.6 (binarys based on fedora core 4)
2) opera static version 9.01-20060728.1 (binarys based on red hat 6.2)

---

### Post by elettronicha on 2006-09-09
[https://help.ubuntu.com/community/OperaBrowser](https://help.ubuntu.com/community/OperaBrowser)

---

### Post by TheRingmaster on 2006-09-09
Is it ok if I have both respositories?


Is there a difference between the opera in the respositories and the opera from the official site?
(I notice that when I scroll (using the opera from the official site) There is a lag in the page at the edges. I think this happens because of the presto rendering engine)

---

### Post by elettronicha on 2006-09-10
> **jpazindustries said:**
> Is it ok if I have both respositories?
No, just one among:
```
deb http://archive.canonical.com/ubuntu dapper-commercial main
deb http://deb.opera.com/opera/ stable non-free
deb http://deb.opera.com/opera/ unstable non-free
```
Check yourself the current version of the 3 repos.

> Is there a difference between the opera in the respositories and the opera from the official site?
(I notice that when I scroll (using the opera from the official site) There is a lag in the page at the edges. I think this happens because of the presto rendering engine)
Maybe the version, but, since I don't use Opera, I'm not able to tell you much more. If you have more difficulties post back here. ;)

---

