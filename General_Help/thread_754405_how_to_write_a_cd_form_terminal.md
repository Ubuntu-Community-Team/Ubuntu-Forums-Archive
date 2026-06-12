---
title: "how to write a cd form terminal"
date: 2008-04-13
forum: General Help
---

### Post by d_deniz on 2008-04-13
is "mv filename /media/cdrom" enough to write a cd from terminal?, it doesn't write the data to the cd  
what is the command to write this data to cd?

---

### Post by sekinto on 2008-04-13
1) copy the files you want to burn to a folder:
> mkdir /tmp/burn
cp <file1> <file2> <file3> <file4> <et cetera> /tmp/burn
2) make a .iso:
> mkisofs -RJ -o /tmp/image.iso /tmp/burn
3) burn the .iso:
> cdrecord -v -pad speed=1 dev=0,0,0 /tmp/image.iso

---

### Post by d_deniz on 2008-04-13
thank you for reply
it says at the end of the output:
device seems to be generic css disk.
cdrecord: Sorry, no CD/DVD/BD-Drive found on this target.

---

### Post by d_deniz on 2008-04-13
the device number should be changed in the command right?
how can I get the right device number from the terminal?

---

### Post by d_deniz on 2008-04-13
ok I found it, 
"cdrecord -scanbus" gave me the correct device number it is 1001,0,0
0,0,0 is lloking for a disk
thanks for your help sekinto
you really helped me a lot

---

