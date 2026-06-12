---
title: "sudo apt-get install g++ problem"
date: 2008-01-12
forum: General Help
---

### Post by tralfas on 2008-01-12
ok so i got my ubuntu cd in the mail a while ago and recently i fscked my system so i had to reinstall. so i used the one i got in the mail. some things that it doesnt like about my computer .........


it wont display the little image of the ubuntu symbol and the words ubuntu with a bar that fills orange under it. instead it say "video image cannot be displayed"

then i go to download g++ by entering this command "sudo apt-get install g++" it goes along good until it reaches the point where it asks me to press y or n and then i press why and it says media change please insert disc labeled "ubuntu 7.10 _Gutsy Gibbon_ - release i386 (20071016 in the drive /cdrom/ and then press enter.

so i put the cd in the drive and i press enter and it doesn't move forward. how do i fix this?

---

### Post by p_quarles on 2008-01-12
Well, the quick fix here is to simply remove the CD-ROM as a source:
```
gksudo gedit /etc/apt/sources.list
```
Then, comment out the lines beginning with deb cdrom: (by placing a "#" mark in front of them). This, of course, only works if the computer in question is online. 

Now, as to why the CD doesn't work where it should, that's a potentially more complex problem. Do other disks work correctly?

---

### Post by taurus on 2008-01-12
And instead of installing g++ by itself, you should install the build-essential package.

```
sudo apt-get update
sudo apt-get install build-essential
```

---

### Post by tralfas on 2008-01-13
i used to only have the distro before gutsy and when i installed that and up graded the graphic worked.

---

