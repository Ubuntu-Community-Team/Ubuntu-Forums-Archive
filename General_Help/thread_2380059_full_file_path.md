---
title: "full file path"
date: 2017-12-12
forum: General Help
---

### Post by Robbyx on 2017-12-12
I have linked a folder to a directory. I do not know where the original folder is on my HD. The icon shows it is linked. The location box in the file properties cuts out the centre of the path with ... 

As I can not resize the file properties box, how do I see the true full path?

---

### Post by again? on 2017-12-12
Try in terminal
```
ls -al */path/to/folder*
```
or
```
file */path/to/folder*
```

---

### Post by Robbyx on 2017-12-13
Thank you.

I discovered another approach: copy and paste the location box to a temp doc. It gets expanded  there so the full path can be read.

---

