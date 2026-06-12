---
title: "disk permissions"
date: 2007-01-26
forum: General Help
---

### Post by StOnE LiBeRaTiOn on 2007-01-26
Hello...
I have an external hard drive that i have attached to my computer.  I can see, and read files from the harddrive, but when I try and write somthing to it, it says I don't have permission.  How do I change this, and also how do I allow other computers on my network to have write and change permissions aswell?

thanks

---

### Post by taurus on 2007-01-26
What type of filesystem is on that harddrive?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by calford on 2007-01-26
i have a similar problem.
i have an external hard drive (NTFS). Whenever i open a file or folder on ubuntu it somehow gets locked, if i try to open that same file or folder under windows i get an error message (something about ownership) and cant access it anymore.

I was able to solve it in win2k, had to go to properties for the file/folder and change the ownership (quite annoying) but on XP i havent been able to do it.

how can i avoid that?

thanks

---

### Post by StOnE LiBeRaTiOn on 2007-01-26
it looks like its an ntfs disk....

---

### Post by taurus on 2007-01-26
You cannot write to ntfs filesystem unless you install ntfs-3g driver first.

[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

---

