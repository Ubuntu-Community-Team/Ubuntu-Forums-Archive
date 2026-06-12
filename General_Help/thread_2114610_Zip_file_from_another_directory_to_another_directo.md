---
title: "Zip file from another directory to another directory?"
date: 2013-02-10
forum: General Help
---

### Post by bigbankclub on 2013-02-10
Ok so let's say I have directory "stats" and I want to zip it up. But I want the zip to be created in Documents directory. The stats directory is located in the Desktop directory. I want to perform this task only via the terminal. 

```
/home/ubuntu$ tar -cvf Downloads/stats.tar Desktop/stats
```This works - archives the file but it take the file structure with it. Thus when I untar I get a tree with Desktop as the root.

---

### Post by SeijiSensei on 2013-02-10
```
cd ~/Desktop; tar -cvf ../Downloads/stats.tar stats
```

---

### Post by Bufeu on 2013-02-10
The easiest way would be to cd to *~/Desktop* first, then use tar to unzip the file.
```
cd ~/Desktop ; tar -cvf ~/Downloads/stats.tar stats
```

---

