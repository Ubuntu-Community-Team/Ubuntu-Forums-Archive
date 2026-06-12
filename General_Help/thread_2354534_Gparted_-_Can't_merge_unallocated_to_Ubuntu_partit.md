---
title: "Gparted - Can't merge unallocated to Ubuntu partition"
date: 2017-03-03
forum: General Help
---

### Post by dunya on 2017-03-03
I have allowed some free space in order to try Ubuntu from my HDD. I never thought I would be using Ubuntu as my daily OS, so upon the kind help of the forum members I solved most of my major problems and decided to expand more space for Ubuntu, while keeping Windows for a few specific programs. Here comes the problem;

With a live USB of Ubuntu, I shrinked Windows by gparted and now I have an unallocated space that I want to add to Ubuntu partition. However I can resize the windows partition and merge it with unallocated space, but I can't resize and merge the unallocated space with the Ubuntu partition. Swapoff also did not work out. What am I doing wrong?

---

### Post by howefield on 2017-03-03
Can you screenshot the gparted window with your partitions showing and post it here ?

---

### Post by dunya on 2017-03-03
> **howefield said:**
> Can you screenshot the gparted window with your partitions showing and post it here ?

[http://imgur.com/Yr3qiWi](http://imgur.com/Yr3qiWi)

---

### Post by QIII on 2017-03-03
Hello!

Before you go any further and do anything else:  Have to booted into Windows and checked for proper operation?  Shrinking a Windows partition with gparted is ill-advised.  You should use the Windows partition tools for that.  Just do a quick check to be sure your Windows installation still works.

Cheers!

---

### Post by dunya on 2017-03-03
> **QIII said:**
> Hello!

Before you go any further and do anything else:  Have to booted into Windows and checked for proper operation?  Shrinking a Windows partition with gparted is ill-advised.  You should use the Windows partition tools for that.  Just do a quick check to be sure your Windows installation still works.

Cheers!

Hi, I shrinked windows partition prior to Ubuntu install by Windows disk partition manager, so my Windows still works.

---

### Post by howefield on 2017-03-03
> **dunya said:**
> [http://imgur.com/Yr3qiWi](http://imgur.com/Yr3qiWi)

Notwithstanding QIIIs advice above, you should be able to expand the extended partition (sd3) into the unallocated space but as you said you will need swap off to be in effect. I'm wondering if possibly you tried to expand sda5 before expanding sda3 ?

---

### Post by dunya on 2017-03-03
> **howefield said:**
> Notwithstanding QIIIs advice above, you should be able to expand the extended partition (sd3) into the unallocated space but as you said you will need swap off to be in effect. I'm wondering if possibly you tried to expand sda5 before expanding sda3 ?

Yay, thank you again. I was trying to expand sda5 first, just like you said and now I succeeded to expand unallocated space by expanding sda3.

---

### Post by howefield on 2017-03-03
> **dunya said:**
> Yay, thank you again. I was trying to expand sda5 first, just like you said and now I succeeded to expand unallocated space by expanding sda3.

Cool, well done and glad you sussed it. Feel free to mark the thread as solved.

---

