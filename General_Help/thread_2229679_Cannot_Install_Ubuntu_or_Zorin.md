---
title: "Cannot Install Ubuntu or Zorin"
date: 2014-06-14
forum: General Help
---

### Post by sean46 on 2014-06-14
**Cannot Install Ubuntu or Zorin**
Im trying to install Ubuntu on a computer which used to run windows XP. Since i don't have any disks lying around i desired to install the OS via a USB flash drive (using YUMI) everything went well until it asks to chose a partition. nothing appears in the list, and if i click on add or Change the program just crashes (installer just closes or gives a error). after formatting the drive i get the same issue. I know that the HHD is working file because it pop's up in the linux demo mode as well as working in windows. as well as this the disk manager detects the partition's on the drive. 

If anyone has any ideas or could tell me if im doing something wrong i will be more than happy 

**Information**

The Hard drive is 164GB

I'm using the 32bit version 

tried on 2 computers (same drive) 
[B]
I have tryed;[/B]

ubuntu-14.04-desktop-i386

zorin-os-8.1-core-32

[B]Images of the errors and instalation

[/B]images are a bit big so i use the url to the images.

[Ubuntu detects the drive]("http://thatraspberrypiserver.raspberryip.com/img/errors%20with%20ubuntu/IMG_4819.JPG") (.jpg)

[No partitions or drives are in the list]("http://thatraspberrypiserver.raspberryip.com/img/errors%20with%20ubuntu/IMG_4820.JPG") (.jpg)
[URL="http://thatraspberrypiserver.raspberryip.com/img/errors%20with%20ubuntu/IMG_4822.JPG"]
the Disk manager on Ubuntu/Zorin [/URL](.jpg)

[Error message when installer crashes]("http://thatraspberrypiserver.raspberryip.com/img/errors%20with%20ubuntu/IMG_4823.JPG") (.jpg)

---

### Post by grahammechanical on 2014-06-14
There are some things that you need to notice.

1) The first screen says "at least 8.6 GB available drive space."

2) The second screen says "7.0 GB free space."

So, you need to create enough free space - 10 GB to 25GB is recommended. At least by me. And you need to turn that free/unallocated space into a partition. That is why the installer in the third screen is not showing any partitions to install into.

Use Windows utilities to re-size the Windows partition but defrag the disk at least twice and make sure that Windows is booting both after defraging and re-sizing. I am also a little concerned that the Disk utility says "partition type unknown." I am wondering if the partition type is a Microsoft Dynamic disk. What does a Windows utility say about this drive. Does it mention Dynamic disks?

Regards.

---

### Post by sean46 on 2014-06-19
Nope still dose not work. i have tryed removeing all the partitions from the drive as well as fomating the drive and even added some partitions, and it still dose not show the partitions in the instalations. as well as this i know that the drive is fine because i have installed windows 7 on it. everything i have tryed dose not work. 
as well as this i have tryed the 64 bit one abd it still dose the same thing. i just find it odd that it detects the partitions in the disk mamager but not in the installer.

---

### Post by sean46 on 2014-06-19
here is a another screen shot of the disk manager;

as you can see its a 164 GB HHD which has 160 free space.

the strange thing is that it detects my memory stick as well a a faulty harddrive.

[Image of disk manager]("http://thatraspberrypiserver.raspberryip.com/img/errors%20with%20ubuntu/Screenshot%20from%202014-06-19%2016_27_40.png") 

[SIZE=4][/SIZE]

---

### Post by sudodus on 2014-06-19
Please do not post such big pictures (screenshots) inline. Instead, go ***[COLOR=#ff0000]Advanced[/COLOR]*** (red button) and click on ***Manage Attachment***, upload and add the file. It will show as a clickable icon, and will not disturb the function for people with slow internet connection.

---

### Post by sean46 on 2014-06-19
oops sorry about that. i made a link to the image.

---

