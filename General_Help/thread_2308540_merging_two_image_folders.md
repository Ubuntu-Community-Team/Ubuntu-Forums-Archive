---
title: "merging two image folders"
date: 2016-01-04
forum: General Help
---

### Post by smokeyone2 on 2016-01-04
Hello

I have two image folders with about 600 images in each - lots of duplicate images and same image name although different images.
Can I just do a cut and paste from one folder to the next or am I missing something here -

Many thanks

---

### Post by matt_symes on 2016-01-04
Hi

> **smokeyone2 said:**
> Hello

I have two image folders with about 600 images in each - lots of duplicate images and same image name although different images.
Can I just do a cut and paste from one folder to the next or am I missing something here -

Many thanks

There are a couple of utilities that may help you with this.

Command line.

```
sudo apt-get install fdupes
```

Graphical Interface:

```
sudo apt-get install fslint
```

I have not used either of them so i can't really comment but they can both apparently help with duplicate files.

You may find fslint easier to use.

Kind regards

---

### Post by smokeyone2 on 2016-01-04
Thanks very much for the advice - I'll try Fslint -

I am finding Fslint hard going but have found a command line while googling which might do the trick - both my folders on the the Ubuntu desktop -

However

ubuntu@ubuntu:~/Desktop$ rsync -a /images/ /images2/
rsync: change_dir "/images" failed: No such file or directory (2)
rsync: mkdir "/images2" failed: Permission denied (13)
rsync error: error in file IO (code 11) at main.c(674) [Receiver=3.1.0]
xubuntu@xubuntu:~/Desktop$

---

### Post by HermanAB on 2016-01-04
Try putting a tilde in front of your paths (assuming they are in your home dir)

---

