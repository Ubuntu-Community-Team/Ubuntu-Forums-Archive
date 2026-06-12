---
title: "Large File Splitter - Available?"
date: 2007-11-27
forum: General Help
---

### Post by broggyr on 2007-11-27
I am trying to copy a 10GB VirtualBox virtual drive file (.vdi) to a USB hard drive, but about 33% through, it crashes.  I tried via command line, but after about 8 minutes, it crashes with an I/O Error.  What I want to do is split it up into several smaller files and try that, but I am unaware of a utility to do this with, or what the commands are for ZIP or ARK to do this.  Anyone have any suggestions?

---

### Post by bingoUV on 2007-11-27
command line, use split. The following splits the files into about 10 or 11 1GB parts.
```

split --bytes=1000m <filename>

```It will create files xaa, xab, xac etc.

---

### Post by broggyr on 2007-11-27
Excellent!  Now, the question is, how do I reassemble them when I copy them to the target?

---

### Post by mali2297 on 2007-11-27
> **broggyr said:**
> Excellent!  Now, the question is, how do I reassemble them when I copy them to the target?

```

cd /path/to/target
cat xa* > newfilename

```

---

