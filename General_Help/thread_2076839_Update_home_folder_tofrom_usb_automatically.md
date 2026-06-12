---
title: "Update home folder to/from usb automatically"
date: 2012-10-27
forum: General Help
---

### Post by naki69 on 2012-10-27
This is my first post, and I am not sure if it belongs in here.

I have a usb flash drive I use when I am away from my home computer.  I would like to use udev to automatically update files in my documents folder with the usb files based on Date Modified.

an example might clarify:
Home computer 
contents /home/user/documents:
file1.txt 3/14/2012
file2.txt 10/27/2012

usb flash drive
contents documents:
file1.txt 9/27/2012
file2.txt 9/27/2012

upon connecting flash drive I want file1.txt to get updated on my home folder while file2.txt to get updated on my usb flash drive.

Is there a way to do this?  

Thanks in advance.

---

### Post by C.S.Cameron on 2012-10-27
Welcome to the forums.
You might have a google at **rsync**.

---

### Post by jerrrys on 2012-10-27
A rsync GUI may make it easier.

[http://luckybackup.sourceforge.net/](http://luckybackup.sourceforge.net/)

or

[http://www.opbyte.it/grsync/](http://www.opbyte.it/grsync/)

Both are in the software center.

---

