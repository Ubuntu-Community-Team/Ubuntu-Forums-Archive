---
title: "Clonezilla Live USB"
date: 2016-05-22
forum: General Help
---

### Post by 2milk on 2016-05-22
Not sure if I'm in the right section but I could use some help. 
I finally have an installation of linux that works really well. I have a few questions though. 

1. Will Clonezilla actually create a complete disk image of my current installation? 
2. Will I be able to restore that disk image backup using the same USB or how will I restore it (since kubuntu doesn't seem to have a "restore from image" option)? 

I have tried installing Clonezilla onto a USB but haven't had any luck. 

3. What am I doing wrong? 

[B]FAT partition created
[IMG]http://s32.postimg.org/p4bwn3pit/Screenshot_20160522_123334.png[/IMG]


Files extracted to the USB.
[IMG]http://s32.postimg.org/4y8eo7tv9/Screenshot_20160522_123239.png[/IMG]

Error.
[IMG]http://s32.postimg.org/4o5him4mt/Screenshot_20160522_123656.png[/IMG]

[/B]**GNU/Linux Method B:  Manual**

[http://clonezilla.org/liveusb.php#linux-setup](http://clonezilla.org/liveusb.php#linux-setup)

---

### Post by sudodus on 2016-05-23
Welcome to the Ubuntu Forums :-)

1. Clonezilla can clone or create a compressed image of a whole drive or a partition. It is straightforward to make an image of a whole drive and to restore it.

2. Download a Clonezilla iso file and check the md5sum. I prefer the ***stable*** version of Clonezilla. See [http://www.clonezilla.org/](http://www.clonezilla.org/)

I have Clonezilla both on CD and on USB. I use [mkusb](https://help.ubuntu.com/community/mkusb) to create USB boot drives from iso files.

You boot from the Clonezilla live drive to clone, create a compressed image and also to restore from an image. (An image is a directory with a number of files.)

-o-

It works to restore into a drive of exactly the same size or larger (but not to restore into a smaller drive).

I have been using Clonezilla for several years, and it has been working well for me with drives containing linux as well as Windows (including dual boot and multi boot).

You should only rely on a backup method that you have tested. And to test, you need an extra drive (because you should not take the risk with your original drive).

---

