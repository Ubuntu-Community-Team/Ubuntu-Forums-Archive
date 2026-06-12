---
title: "batch file?"
date: 2007-05-03
forum: General Help
---

### Post by ale52 on 2007-05-03
Can you make a batch file in Linux Ubuntu / if so, how?

Alan <><  :)

---

### Post by pebo on 2007-05-03
Yes, very easily. You need to write a bash script. [Here]("http://rute.2038bug.com/node10.html.gz#SECTION001010000000000000000") is a tutorial. HTH!

---

### Post by ale52 on 2007-05-03
> **pebo said:**
> Yes, very easily. You need to write a bash script. [Here]("http://rute.2038bug.com/node10.html.gz#SECTION001010000000000000000") is a tutorial. HTH!

Is it just the first part of the page that applies?  I want to write a simple 'script' to run a program in the Terminal window.

Thanks Pebo for your quick response.  

Alan <>< :KS

---

### Post by pebo on 2007-05-04
Yes, after the first line```
#!/bin/sh
```type in the command you need, then save it. Make it executable: ```
chmod 0755 myfile.sh

```To run the script from your current directory:```
./myfile.sh
```

---

