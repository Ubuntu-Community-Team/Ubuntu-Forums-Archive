---
title: "cloning usb drive"
date: 2018-07-22
forum: General Help
---

### Post by fresnofred on 2018-07-22
I have a live usb on a sandisk 16 gb drive.  booted up puppy linux and tried to use PUDD to clone this to an IDENTICAL sandisk usb drive and it reports both as correct size and then before the cloning begins tells me the original 16 gb dirve is 32 gb so will not let me proceed.  successfully cloned another identical drive to identical drive but now get this size error.  any suggestions.

---

### Post by Claus7 on 2018-07-25
Hello,

I would suggest you to try clonezilla.
[https://clonezilla.org/](https://clonezilla.org/)

Regards!

---

### Post by HermanAB on 2018-07-25
It is extremely simple actually:
$ sudo cat /dev/sdb > /dev/sdc

Provided that you have only one disk drive in your machine and sdb and sdc are indeed the memory sticks.  If you are not sure and don't know how to make sure, then you are at risk of deleting a disk with valuable data. 

YMMV TIMTOWTDI RTFM DBMFYFU etc.

---

### Post by sudodus on 2018-07-25
> **Claus7 said:**
> Hello,

I would suggest you to try clonezilla.
[https://clonezilla.org/](https://clonezilla.org/)

Regards!

+1 for cloning with Clonezilla

---

