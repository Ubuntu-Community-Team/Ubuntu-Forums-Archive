---
title: "Does dd work with different sizes of disks?"
date: 2017-07-07
forum: General Help
---

### Post by Xinghao_Chen on 2017-07-07
I want to migrate Ubuntu 14.04 from a 100GB HDD (in slim-tray) to a 32GB mSATA SSD. The 100GB HDD is only used less than 7%. Would "dd if=/dev/sdX of=/dev/sdY" work for me in this case?

---

### Post by monkeybrain20122 on 2017-07-07
Why do you want to you dd?  fsarchiver is perfect for it, it is easy to use, safe (unlike dd which may screw your hard drive), copy files instead of sector by sector like Clonezilla so you can easily migrate to a smaller drive as long as it is big enough to hold the contents,  and is in the repo.

[http://www.fsarchiver.org/quickstart/](http://www.fsarchiver.org/quickstart/)

[https://ubuntuforums.org/showthread.php?t=2221842](https://ubuntuforums.org/showthread.php?t=2221842)

---

### Post by Xinghao_Chen on 2017-07-07
Well, dd came with the Ubuntu installation and appears to me simple and easy to use. Thank you for introducing fsarchiver to me. I certainly will look into it. But just from the links you provided, it seems complicated - I am an elementary Ubuntu user. My needs here are simple: just migrate everything from HDD to a smaller SSD. I tried using Windows version of disk cloning and the resulting copied-to Ubuntu SSD doesn't boot. Is there a simpler fsarchiver command-line text similar to dd for my simple task?

---

### Post by monkeybrain20122 on 2017-07-07
See the second link. Basically you run one command ("savefs", with the -a -A options if you want to do a live cloning) to create the image, and use another command ("restfs") to restore the image. wherever it maybe.

There is a gui for fsarchiver called qt5-fsarchiver if you prefer point and click (works only for 64 bits). To install it add the [ppa]("https://launchpad.net/~dieterbaum/+archive/ubuntu/qt5-fsarchiver-64-bit") to your source  and install

```
sudo add-apt-repository ppa:dieterbaum/qt5-fsarchiver-64-bit
sudo apt update
sudo apt install qt5-fsarchiver
```

---

### Post by oldfred on 2017-07-07
DD will not work. It really only is for same size to same size drives. But copy to can be larger, but may be then seen as same size drive.
dd also copies all empty space so very inefficient for drives with lots of unused space.

I prefer new clean installs, and then copy /home as that has all your settings and data. Only if you made some specific hardware settings those would be in /etc or installed server software Web, database, etc which them may be somewhere in / in their own folders.

---

### Post by 1clue on 2017-07-07
The unofficial name for dd is "disk destroyer." It's easy to use, hard to get right with respect to block devices. If you copy incompatible data onto a device you're screwed.

---

### Post by Xinghao_Chen on 2017-07-08
Thank you for the advice.

---

