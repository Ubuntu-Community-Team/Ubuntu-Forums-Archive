---
title: "Install new usplash theme"
date: 2007-01-22
forum: General Help
---

### Post by youthforlinux on 2007-01-22
I downloaded some new usplash themes and untared to /usr/lib/usplash with the other themes
how do i change the link for usplash-artwork.so to the new usplash theme:lolflag: :lolflag:

---

### Post by Mike_Longbow on 2007-01-22
```
sudo update-alternatives --config usplash-artwork.so
```
...then a prompt should appear, just choose the option regarding the usplash you just dowloaded.
Then run:
```
sudo dpkg-reconfigure linux-image-"name-of-your-kernel-here"
```
and that's it! :wink: 

*Note: To know the name of your kernel type:
```
uname -r
```

---

### Post by komputes on 2008-01-10
```
sudo update-alternatives --config usplash-artwork.so
sudo dpkg-reconfigure linux-image-`uname -r`
```
saves you the trouble of running uname, copy, pasting by using `backticks`. Anything between these backticks is ran as a command so this will simplify the process by inserting the kernel version directly into the command line.

Now if anyone knows (and by that I mean they have tried it and succeeded) how to make custom usplash boot splash on Gutsy, please contact me.

---

### Post by ovoskeuiks on 2008-03-16
I've created one before what do you want to know?

---

