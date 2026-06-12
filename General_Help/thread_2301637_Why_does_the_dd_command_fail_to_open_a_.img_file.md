---
title: "Why does the dd command fail to open a .img file?"
date: 2015-11-03
forum: General Help
---

### Post by Whalen_Smithers on 2015-11-03
Pretty new to Linux, running Ubuntu 14.04.2 amd64. I have a raspberry pi and I want to  flash raspian onto an 8GB microsd card. I have been unsuccessful. After downloading raspian and preparing the card... 
 
The command I entered is:

  sudo dd if=2015-09-24-raspian-jessie.img of=/dev/mmcblk0 bs=4M

  The error message is:
  
dd: failed to open &#8216;2015-09-24-raspian-jessie.img&#8217;: No such file or directory
  
I then try being more specific in the path to the file:
  
sudo dd if=~/Downloads/2015-09-24-raspian-jessie.img of=/dev/mmcblk0 bs=5M
  
But get the same result:
  
dd: failed to open &#8216;/home/handsome/Downloads/2015-09-24-raspian-jessie.img&#8217;: No such file or directory
  
So then I double check to see if the file is there and it is:
  
cd Downloads
Downloads$ ls
2015-05-05-raspbian-wheezy.img    2015-09-24-raspbian-jessie.img 
  
Is there something I'm missing?

---

### Post by Bucky Ball on 2015-11-03
Welcome. In the terminal, navigate to your Downloads folder: 

```
cd /home/<username>/Downloads
```

Where <username> is your username. Then:

```
sudo dd if=2015-09-24-raspian-jessie.img of=/dev/mmcblk0 bs=4M
```

---

### Post by mcgess on 2015-11-04
Hi, not sure if it's a typo in your question but your dd command refers to raspian... but the output of ls shows raspbian

---

### Post by yetimon_64 on 2015-11-04
> **mcgess said:**
> Hi, not sure if it's a typo in your question but your dd command refers to raspian... but the output of ls shows rasp**b**ian

That appears right by my reading of the opening post as well. Seems to be a typo in the dd command for the image file name and with such that error is normal. 

As Bucky Ball has noted, ensure you cd into the directory holding the download, or alternatively you could include the absolute path if you do not want to navigate in terminal manually first. It does look more like a simple typo here, but either way you will get the same "No such file or directory" error. Cheers, yeti.

---

