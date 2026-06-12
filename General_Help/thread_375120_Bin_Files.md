---
title: "Bin Files"
date: 2007-03-03
forum: General Help
---

### Post by Matt Nichols on 2007-03-03
I recently downloaded the JDK with NetBeans IDE 5.5, and it is a bin file. I assume this is an installer of some sort, but I cannot see how to run it or access the files within. I tried using archive manager to no avail. This is probably a question with a really obvious answer, but I have yet to find it myself. Thanks for your help.

---

### Post by taurus on 2007-03-03
Try something like these from a terminal.

Applications -> Accessories -> Terminal
```
cd ~/Desktop
chmod 755 **filename.bin**
sudo ./**filename.bin**
```

And if it doesn't work, then post the output of this command here, assuming you have saved the download to ~/Desktop.

```
ls -la ~/Desktop
```

---

### Post by Matt Nichols on 2007-03-03
The former worked swimmingly. Thank you.

---

