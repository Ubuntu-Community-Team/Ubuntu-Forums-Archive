---
title: "Can't write data to usb flash drives,spoil them"
date: 2015-11-04
forum: General Help
---

### Post by Artemio_T on 2015-11-04
Ubuntu 15.04
Laptop Lenovo ideapad s510p

I have a problem writing to usb flash drives. The system when I try 1st behaves like normal, copy file and looks like process is fine. But when you try to open it, you can't, the file is dameged. If you install that flash drive in other computer, it can't be read anymore and needs to be formatted. If you try the second time it may give you error about writing.

Also I have some strange mouse behaviour , I guess this may be related to usb problem too.
Some time my mouse reciver stops working, and plugging in and out doen't fix the problem, sometimes plugging in an other usb fixes the problem, sometimes I have to use an other mouse receiver.

Also sometimes usb port just stop working (once per month)

Does anyone has a clue what it may be?

---

### Post by sudodus on 2015-11-04
Yes, you have problems with the USB system. Generally Lenovo computers work well with Ubuntu, but there are some exceptions.

I suggest that you try to find out if this is a hardware problem or software problem: Download some other versions of Ubuntu:

14.04.1 LTS, 14.04.3 LTS, 15.10 and and try them live. You should also try your current version 15.04 live.

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

If USB works well with one of these versions, I think it is a software problem with your installed system (otherwise it might be a hardware problem - but more testing is necessary to be sure).

-o-

Will it make a difference for the USB pendrive, if your USB mouse receiver is connected or not?

If 'only' the file system of the pendrive is damaged, you can wipe the first megabyte create a new file system with ***mkusb version 10.3***. See these links

[Wipe menu](https://help.ubuntu.com/community/mkusb#Wipe_the_first_megabyte_or_the_whole_device)

```
sudo add-apt-repository ppa:mkusb/unstable
sudo apt-get update
sudo apt-get install mkusb
```


[Pendrive lifetime](http://ubuntuforums.org/showthread.php?t=2196858&p=13199297#post13199297)

---

### Post by HermanAB on 2015-11-04
If the machine has a PCMCIA cardbus slot, then get a cardbus USB adaptor.

---

