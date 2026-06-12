---
title: "Deleting a qemu partition?"
date: 2007-01-13
forum: General Help
---

### Post by Ryupower on 2007-01-13
[SIZE="4"][FONT="Century Gothic"]hi...new too all this. ^^;

I have a question ( I hope this is in the right forum ):

How do I delete the images /partitions I made on qemu?
I tried to emulate Windows 2K...which worked ( though by res. change the window got all buggy ), I downloaded something in it, and noticed that 3GB is NOT ENOUGH!

Now I'm trying to delete those 3 GB and make a new - partition/image whatever they call it - using up 5 or 6 GB, or atleast ennlarge it....


Thanks for any help! :)[/FONT][/SIZE]

---

### Post by Ryupower on 2007-01-14
anybody? ^^;

---

### Post by kebes on 2007-01-14
Deleting a qemu partition is simple... simply find the file (it will end in ".img") and delete it like you would any normal file.

To create a new qemu image, you use the command "qemu-img", so you would enter a command like:

qemu-img create new_win 6G -f qcow

This will create a new file "new_win" that will appear to be 6 gigabytes large inside qemu. The "-f qcow" tells it to create a compressed image. This means that even though the image is 6G large, the file on your hard disk will not be 6G large... it will only be as large as needed to accomodate all the data within it. So you can make images larger without worrying about using up space on your real hard disk.

You can find more information here:
[http://fabrice.bellard.free.fr/qemu/qemu-doc.html#SEC18](http://fabrice.bellard.free.fr/qemu/qemu-doc.html#SEC18)

Hope that helps.

---

### Post by Ryupower on 2007-01-14
> **kebes said:**
> Deleting a qemu partition is simple... simply find the file (it will end in ".img") and delete it like you would any normal file.

To create a new qemu image, you use the command "qemu-img", so you would enter a command like:

qemu-img create new_win 6G -f qcow

This will create a new file "new_win" that will appear to be 6 gigabytes large inside qemu. The "-f qcow" tells it to create a compressed image. This means that even though the image is 6G large, the file on your hard disk will not be 6G large... it will only be as large as needed to accomodate all the data within it. So you can make images larger without worrying about using up space on your real hard disk.

You can find more information here:
[http://fabrice.bellard.free.fr/qemu/qemu-doc.html#SEC18](http://fabrice.bellard.free.fr/qemu/qemu-doc.html#SEC18)

Hope that helps.

AWESOME THANKS!
so uh, how do you know what the name of the .img is? XD

---

### Post by kebes on 2007-01-14
Well the file will probably end in ".img", so you could search for that...

But how do you normally activate that qemu instance? Check the command you're using to activate it, the command will look like, for example:
qemu virtualdisk.img

The "virtualdisk.img" is the disk image! If you launch your qemu from an icon, check the properties and see what command it refers to.

---

### Post by Ryupower on 2007-01-14
> **kebes said:**
> Well the file will probably end in ".img", so you could search for that...

But how do you normally activate that qemu instance? Check the command you're using to activate it, the command will look like, for example:
qemu virtualdisk.img

The "virtualdisk.img" is the disk image! If you launch your qemu from an icon, check the properties and see what command it refers to.



I just copy pasted everything from the quick guide.
But I got it now.
Thanks very much and God bless!! ^^

---

