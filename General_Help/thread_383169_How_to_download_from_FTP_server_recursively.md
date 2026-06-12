---
title: "How to download from FTP server recursively"
date: 2007-03-12
forum: General Help
---

### Post by kpkeerthi on 2007-03-12
```

/
  CD1
       folder1
             a.mp3
             b.mp3
             .
             .
             z.mp3  
       folder2
             a.mp3
             b.mp3
             .
             .
             z.mp3  

  CD2
       folder1
             a.mp3
             b.mp3
             .
             .
             z.mp3  
       folder2
             a.mp3
             b.mp3
             .
             .
             z.mp3  
   .
   .
   .
   CDn

```
The files are organized in a FTP server as you see above. What is the best way to download all the files from the server, recursively, starting from the root directory? It would be great if I could get the files organized locally in my PC the same fashion as that in the server. I'm sure there is a command to do this. But not sure how. Any help is appreciated.

---

### Post by ewankho on 2007-03-13
Try wget.

---

### Post by lloyd_b on 2007-03-13
"wget" will work, as was already mentioned.  In addition, the "ncftp" ftp client supports a "get -R" command, which can recursively retrieve files and directories.

Lloyd B.

---

### Post by kpkeerthi on 2007-03-13
Thanks... 
```

wget -rxv ftp://user:pass@host/root_folder

```
super cool!

---

