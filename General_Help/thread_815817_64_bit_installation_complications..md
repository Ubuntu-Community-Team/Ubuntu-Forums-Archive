---
title: "64 bit installation complications."
date: 2008-06-02
forum: General Help
---

### Post by bammeh on 2008-06-02
So, I donwloaded BOTH ubuntu versions off download page.

I burn them to seperate disks.

I try disk one on one computer:

"This kernel requires an x86-64 CPU, but only detected an i586 CPU."

So, i try the other disk:

"This kernel requires an x86-64 CPU, but only detected an i586 CPU."

So, I try it on my laptop:

"This kernel requires an x86-64 CPU, but only detected an i586 CPU."

and im running on a x86 processor with windows xp home on one and windows xp media center on the other =/

---

### Post by jualin on 2008-06-02
According to what you said you should use the Ubuntu version for 64 Bit. Are you completely sure that you downloaded the Ubuntu 64 bit version?

---

### Post by Rocket2DMn on 2008-06-02
When you say both versions do you mean Desktop and Server?  Your hardware requires the i386 aka x86 version, not x86-64 aka AMD64 version.
You should have the "Standard personal computer (x86 architecture, PentiumTM, CeleronTM, AthlonTM, SempronTM)" radio button selected at [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

---

### Post by bammeh on 2008-06-02
I dopwnloaded both of these:

Standard personal computer (x86 architecture, PentiumTM, CeleronTM, AthlonTM, SempronTM)   

64bit AMD and Intel computers

neither works.

same error message.

---

### Post by jualin on 2008-06-02
This may sound silly, but trust me it happens. Are you sure you did not burn the image for the 32 Bit Ubuntu Version in both Cds? 
Maybe you can download the 64-bit Version again and deleting the previous .iso images from your computer.

---

### Post by Rocket2DMn on 2008-06-02
Are you sure you burned the i386 image to the disc instead of accidentally burning the amd64 again?  Try checking the md5sum on the file:
[HowTo]("https://help.ubuntu.com/community/HowToMD5SUM") md5sum
[Hashes]("https://help.ubuntu.com/community/UbuntuHashes") to check against
Then burn the cd-r at a slow speed, like 4x, to help prevent write errors.

Can you tell us what processor you have?

---

### Post by bammeh on 2008-06-02
I will do that :)

It is an Intel pentium 4 processor

Yes, the adm64 desktop version is the one on this computer...
th hashes both match to fc43f665ba51c4be0d95c011aefef45d


i used wubi to install on another computer and it worked fine but after i enabled a driver i had to restart and when i did, i login to ubuntu and after a few seconds, it shows a blank white screen.

---

### Post by Rocket2DMn on 2008-06-02
Since both hashes match to fc43f665ba51c4be0d95c011aefef45d that means that both are the AMD64 desktop cd. You need to download the i386 image file that has hash 8895167a794c5d8dedcc312fc62f1f1f

---

### Post by bammeh on 2008-06-02
Problem Solved.

I needed the x86 disk.

Got it :P

Running on Ubuntu now.

Thanks guys!

---

### Post by jualin on 2008-06-02
I am glad you got it working!

---

