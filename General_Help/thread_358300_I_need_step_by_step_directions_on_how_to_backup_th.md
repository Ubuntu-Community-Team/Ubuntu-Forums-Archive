---
title: "I need step by step directions on how to backup the home &amp; desktop folders on USB HDD"
date: 2007-02-10
forum: General Help
---

### Post by uberlounge_com on 2007-02-10
In the shell (i can't get into the GUI), how do I step by step get all the files from the home and desktop folders and move them onto an external usb hard drive?

Thanks everyone.

---

### Post by sdide on 2007-02-10
Hey., 

you do the following. Jack in your usbkey, and wait for it to mount.
check where it mounts with the mount command.
example:
```
$ mount 
...
/dev/sda1 on /media/usbdisk type vfat ,,,
,,,
$ 
```

so my usbkey is mounted in /media/usbdisk/

then you do a 
```
$ cp -r /home/<your_username>/ /media/usbdisk/
```

the Desktop folder is a subdir of the /home/<your_username>/ folder, so everything should be included in the above line.

after the copy is done, a small check with the command du doesn't hurt.

```
$ du -sh /home/<your_username>/
$ du -sh /media/usbdisk/

```

should yield the same number.

and of course go check see if things look right in /media/usbdisk/

thats what I would do anyways.

---

