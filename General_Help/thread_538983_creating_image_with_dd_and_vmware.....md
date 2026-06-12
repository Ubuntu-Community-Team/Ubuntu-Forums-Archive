---
title: "creating image with dd and vmware...."
date: 2007-08-30
forum: General Help
---

### Post by Mia_tech on 2007-08-30
is it possible to create an image of a hard drive with dd and later importing it to vmware?

---

### Post by spupy on 2007-08-30
Making image with dd is easy (change hda1 for whatever you want to use)
```
dd if=/dev/hda1 of=disk.vmdk
```
Now, there is a thing im not sure about. Vmdk is the format for virtual machine's disk (hence the abbreviation). I don't know is it is formated the same way as a harddisk partition is. 
I know for 100% that this method works with qemu, because qemu uses raw harddisk images. You should check out the options when you import the image in vmware. 
EDIT: Yup, it most probably wont work, because the image wont be bootable/ wont have bootsector/ whatever it is that makes a partition bootable. Copying the bootsector of the PC wont do the job if you run Grub. 

Alternatively, you can use VMware Converter for Windows and convert the Windows to a vmware image (that of course if the target is windows). Don't know how exactly this happens, but i imagine it requires alot of disk space.

---

