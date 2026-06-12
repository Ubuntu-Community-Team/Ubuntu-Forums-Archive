---
title: "Creating an ISO"
date: 2008-03-12
forum: General Help
---

### Post by johnswb on 2008-03-12
Hello all,

Hope someone can answer this?

I have a bootable CD saved as an .iso on my Desktop.  I also have a folder with files in it.  I would like to take the file in the folder and create a new iso with both.  I found how to "mkisofs -o dir" to make an iso of the folder.  I don't know how to get both the info on the CD "boot sectors" and the files in the same iso.  I can't be the first to do this, please help.

---

### Post by rattking on 2008-03-12
Hi
have you tried mounting the iso then copying the files in? then burning the iso to cd
eg.
first make a backup
cp image.iso image-modified.iso
mkdir ~/Desktop/loop
sudo mount -o loop -t iso9660 image-modified.iso ~/Desktop/loop
copy the files you want on the cd into the new loop directory using sudo.. you will need to be root
then unmount the iso
sudo umount ~/Desktop/loop
and burn the image-modified.iso

hope this helps..

---

### Post by stchman on 2008-03-12
> **johnswb said:**
> Hello all,

Hope someone can answer this?

I have a bootable CD saved as an .iso on my Desktop.  I also have a folder with files in it.  I would like to take the file in the folder and create a new iso with both.  I found how to "mkisofs -o dir" to make an iso of the folder.  I don't know how to get both the info on the CD "boot sectors" and the files in the same iso.  I can't be the first to do this, please help.

K3B can create a .iso file.  Instead of burning to a CD you burn an image.

---

### Post by koenn on 2008-03-12
> **rattking said:**
> Hi
have you tried mounting the iso then copying the files in? then burning the iso to cd
eg.
first make a backup
cp image.iso image-modified.iso
mkdir ~/Desktop/loop
sudo mount -o loop -t iso9660 image-modified.iso ~/Desktop/loop
copy the files you want on the cd into the new loop directory using sudo.. you will need to be root
then unmount the iso
sudo umount ~/Desktop/loop
and burn the image-modified.iso

hope this helps..

you sure this works ? iso9660 is a read-only filesystem IIRC, so you cant write to it, i.e you cant copy files to it.

---

### Post by rattking on 2008-03-12
doh! you are right it is read only..
I got myself confused with the time i did that to a bootable floppy image then burned as a bootable cd

---

### Post by johnswb on 2008-03-12
Thank you for taking the time in helping me.  I've done what you said and I get the following. Even when I use sudo or su -.

cp: cannot create regular file `~/Desktop/loop//logfile.txt': Read-only file system

---

### Post by johnswb on 2008-03-12
> **stchman said:**
> K3B can create a .iso file.  Instead of burning to a CD you burn an image.

Burning an image is not the problem.  I need to include files that are not already in the iso.

---

### Post by koenn on 2008-03-12
modifying an iso  is usually done like this
- mount the cd with -o loop (see rattking's post)
- copy contents of mounted image to a directory
- modify content in directory
- use mkisofs to create iso file from directory
(- burn iso to CD)

problem there is that you loose the boot sector in the process - 
I haven't figured out how to solve that.
A workaround is to use a floppydisk bootsector and create the CD image bootable with "floppy emulation". 
Most other methods I found involve using syslinux / isolinux. I haven't found anything on simply extracting a boot sector from a CD and reuse it to create a "no emulation" bootable CD - I suppose that's what you're looking for

---

### Post by johnswb on 2008-03-12
koenn,

That is what I'm looking for.  I guess I can give the floppy image a try.  I really do appreciate you guy taking the time to look at this with me.

---

### Post by chewearn on 2008-03-12
Here is an old thread that might be useful:
[http://ubuntuforums.org/showthread.php?t=19428](http://ubuntuforums.org/showthread.php?t=19428)

---

