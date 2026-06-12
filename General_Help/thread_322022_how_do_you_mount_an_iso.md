---
title: "how do you mount an iso"
date: 2006-12-19
forum: General Help
---

### Post by mark076h on 2006-12-19
how exactly do you mount an iso image in linux is there a program similar to deamontools or powerISO i could use?

---

### Post by ciscosurfer on 2006-12-19
> **mark076h said:**
> how exactly do you mount an iso image in linux is there a program similar to deamontools or powerISO i could use?This seems to be a very common question lately.  Perhaps I will write up a HOWTO.  In the meantime, take a look [at this thread]("http://ubuntuforums.org/showthread.php?p=1908291") and pay special attention to **guitara**'s advice (my advice is good, too ;)).  Post back to either threads if you have any further questions. :-)

Generally speaking, it's as easy as creating a directory and then mounting the ISO to that directory.  For example:```
sudo mkdir /mnt/iso
```Now, change directories to where the ISO image is located.  Let's say it's on your Desktop....then you'd enter in a terminal:```
cd ~/Desktop
```And then issue the following at a command line```
sudo mount -o loop *name_of_file_here*.iso /mnt/iso
```Sometimes folks will add in the **-t iso9660** switch, but mount should take care of noticing that you are wanting to mount an ISO and so the switch is not normally required.

---

### Post by aysiu on 2006-12-19
> **ciscosurfer said:**
> This seems to be a very common question lately.  Perhaps I will write up a HOWTO.  In the meantime, take a look [at this thread]("http://ubuntuforums.org/showthread.php?p=1908291") and pay special attention to **guitara**'s advice (my advice is good, too ;)).  Post back to either threads if you have any further questions. :-)
There's already a HowTo written:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount.2Funmount_Image_.28ISO.29_files_without_burning](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount.2Funmount_Image_.28ISO.29_files_without_burning)

---

### Post by taurus on 2006-12-19
Applications -> Accessories -> Terminal
```
sudo mkdir /media/iso
sudo mount -t iso9660 -o loop **filename.iso** /media/iso
ls -la /media/iso
```

---

### Post by ciscosurfer on 2006-12-19
> **aysiu said:**
> There's already a HowTo written:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount.2Funmount_Image_.28ISO.29_files_without_burning](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount.2Funmount_Image_.28ISO.29_files_without_burning)Those instructions don't discuss a few issues/facts:[LIST=1]
[*]You don't need to issue modprobe loop if it's compiled in-kernel (which most of us have)
[*]It's unnecessary to use the -t iso9660 switch, mount will (generally speaking) take care of that for you.  You can read more about it in the man pages for mount or elsewhere on the web.[/LIST]And there hasn't been a HOWTO written for the Ubuntu Forums explaining these issues.  I mentioned the need above because I have seen many users recently asking about this procedure.  Ubuntu Guide is quick and dirty and I've used it many times and I've found it helpful.  However, some people might want an explanation.  Granted, the casual user probably doesn't want detailed instructions/explanations, but other users just might ;).

---

### Post by aysiu on 2006-12-19
Ah, good point.

---

### Post by ice60 on 2006-12-19
you might be able to use qemu. i haven't tried it though.
[http://www.grumz.net/?q=node/282](http://www.grumz.net/?q=node/282)

EDIT, ok that doesn't use qemu, but that might work too :D

here's the one i was thinking of -
[http://www.grumz.net/?q=node/216](http://www.grumz.net/?q=node/216)

here's another -
[http://www.grumz.net/?q=node/281](http://www.grumz.net/?q=node/281)

nautilus-actions lets you right-click on a file to run whatever you pick from the right-click menu. i might try that first one, it looks good.

---

