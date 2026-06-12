---
title: "Create *.img file from folder of files"
date: 2008-06-23
forum: General Help
---

### Post by tatt on 2008-06-23
Hi all.

I have found plenty of tutorials explaining how to create *.img files from a floppy.

I have a slightly different scenario.

I have three folders which contain a small text based OS.

DISK1
DISK2
DSIK3

I need to create three img files which i can mount into virtual box. How can I do this??

Thanks

---

### Post by bodhi.zazen on 2008-06-23
Do those files need to be combined into one ?

If not, put them in a directory in home, say ~/iso

then :

```
mkisofs -o ~/DISK.iso ~/iso/
```

Now mount ~/DISK.iso as a CD (in virtualbox)

---

### Post by prshah on 2008-06-23
> **tatt said:**
> 
I need to create three img files which i can mount into virtual box. How can I do this??

[http://en.wikipedia.org/wiki/RaWrite2](http://en.wikipedia.org/wiki/RaWrite2) has many options.

---

