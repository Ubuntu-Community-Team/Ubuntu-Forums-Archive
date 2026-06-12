---
title: "Diskspace ended."
date: 2015-06-22
forum: General Help
---

### Post by Azyx on 2015-06-22
Have an eee PC 900 with 16GB  disk and Lubuntu 14.04. Have 2 partitions. / 6GB and /home 10GB. Have not installed so much applications, but / are full. On my Ubuntu 14.04 I have more applications installed and using about 8GB in /-partitions.

Can I free up space in /-partition or do I need to change the partitions size on / ?

/Cheers

---

### Post by sudodus on 2015-06-22
You can use the following commands (or install and use Ubuntu-Tweak from its PPA).

```
sudo apt-get update
sudo apt-get autoremove
sudo apt-get autoclean
sudo apt-get clean
```

Search for and remove big files, and maybe remove some program package that you do not really need.

(The GUI program ***baobab*** can help you find where most of the memory is used. You can use it from a USB pendrive, if you don't want to install it into the small internal drive space.)

---

### Post by Azyx on 2015-06-22
Thanx. Now I have more than 100MB free space, so I can make a apt-get upgrade :) Will see how much I can get rid of... Maby 6 GB on the root-partition is to little these days ? ...

---

### Post by sudodus on 2015-06-22
6 GB is plenty for Lubuntu and definitely OK for Xubuntu (and I think Ubuntu Mate too). Particularly when you have a separate home partition.

You may want to start from the Ubuntu **mini.iso** and install only the program packages you want. That way you can get a system that is free from bloatware.

*Edit:* But with such a small drive I think it is better to have one single root partition with /home as a directory. I makes it possible to use the drive space in a more flexible way with one 16 GB partition.

---

### Post by Azyx on 2015-06-22
Yes, could be best and have just one partition, but it quite easy to fill up home, and then it get problems ;)  But after these apt-get  command over here it's just an 70% full /-partition :)  I see now that I have installed Libre-office, instead of Abi-word. Are there a way to see how big an applications are in root-directory in an easy way?

---

### Post by sudodus on 2015-06-22
Maybe this page will give you a hint - it should be about the same size for Lubuntu, but I'm not sure how help libraries are counted.

[http://www.linuxfromscratch.org/blfs/view/svn/xsoft/libreoffice.html](http://www.linuxfromscratch.org/blfs/view/svn/xsoft/libreoffice.html)

---

