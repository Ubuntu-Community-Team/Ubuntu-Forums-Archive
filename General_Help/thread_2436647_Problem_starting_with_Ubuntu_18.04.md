---
title: "Problem starting with Ubuntu 18.04"
date: 2020-02-10
forum: General Help
---

### Post by nell-12 on 2020-02-10
Hello, a month ago, I installed a partition in my PC with Windows 10 for Ubuntu 18.04 and, until now, everything went Smoothly. However, now I tried to start Ubuntu as always but it freezed at the beginning, just after de boot menu. I can start in the recovery System and in my windows partition but I can't get to put even my password to enter Ubuntu. Please, help me!! I'm desperate!! Thank you so much!!

---

### Post by mörgæs on 2020-02-12
Hi, welcome to the fora.
Are you sure that you want to struggle with 18.04 at this day and age? You could also use the occasion to install 19.10.

---

### Post by EuclideanCoffee on 2020-02-12
If you installed Windows after installing Ubuntu, there is a strong likelihood that something during the installation of Windows affected your Ubuntu partition.

---

### Post by gsahli on 2020-02-12
You didn't say so I ask - Do you have the install media for Ubuntu? Use that to repair/boot into ubuntu, then run command update-grub to make a permanent fix. (Windows will be a menu choice at boot-up.)

---

### Post by mastablasta on 2020-02-13
> **mörgæs said:**
> 
Are you sure that you want to struggle with 18.04 at this day and age? You could also use the occasion to install 19.10.

why not? it still has 3 years support left and it has most of the major bugs ironed out as well as a number of smaller ones. i too installed 18.04 in January to a new PC and just last week i replaced 14.04 with it. so far it works like a charm in both cases. even the prtscr key is working again and some Fn keys on the old laptop. i did use the latest HWE kernel in both cases. in the first to get the latest drivers for the motherboard and in the second to hopefully get the latest drivers for the old AMD chip that lost fglrx support with the 14.04. though i doubt they actually did any work for it lately :)

---

### Post by mörgæs on 2020-02-13
> **mastablasta said:**
> ...and it has most of the major bugs ironed out as well as a number of smaller ones.

Yes, they were fixed in 18.10, 19.04 and 19.10. After that some of the fixes may have been backported to 18.04.

I'm not saying that it's impossible for original poster to get 18.04 running, especially since it once did install and work, but the safe bet is 19.10.

---

