---
title: "Quicker alternative to du on large directories?"
date: 2008-05-07
forum: General Help
---

### Post by strikenowhere on 2008-05-07
Hello,
I am wondering if there is a quicker way to grab the sizes of directories from the command-line other than using "du -hc <directory> | grep total".  Basically I have several large directories (10+ GB) present on a drive that I want to get disk usage totals for, however running the aforementioned command takes forever (10+ minutes or more depending on size).  I know Windows does some sort of caching in regards to file/directory sizes, but is there something similar in the linux world?

Thanks

---

### Post by bingoUV on 2008-05-07
I don't think there is a cache by default, but it can be made more elegant and very slightly quicker than the command you are using. Instead of  ```
 du -hc  | grep total 
```do  ```
 du -sh  
```This saved du the trouble of printing the sizes of all subdirectories, and saved grep the trouble of waking up at all.

---

### Post by strikenowhere on 2008-05-07
That sped things up immensely, actually...thanks!

---

### Post by bingoUV on 2008-05-07
> **strikenowhere said:**
> That sped things up immensely, actually...thanks!

Some of the improved speed is because you ran it for the second time for the same directory.

---

