---
title: "How to change Ubuntu Kernel 386 to 686"
date: 2005-05-25
forum: General Help
---

### Post by Marcel Firlej on 2005-05-25
Hi.

Sorry for my english  :grin: 

I have two kernels now. Default is i386. What I must do, to configure new i686 kernel? 

with i686 I can`t run nVidia drivers, so my Xserver too. I have configured 3 buttons PS/2 wheel-mouse under IMPS/2, and nVidia display driver. Should I copy nVidia files to new Kernel Libs directory? Reconfigure something?

Some help?

---

### Post by netrattler on 2005-05-25
To get you nvidia module running under your i686 kernel all you need to do is install the linux-restricted-modules-686. At your terminal just do this.

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install linux-restricted-modules-686

Then boot up with your 686 kernel and you should now have video for X again.

Joe

---

### Post by Marcel Firlej on 2005-05-25
Thanks,

It`s working  \\:D/

---

### Post by garnertr on 2005-05-25
[QUOTE=netrattler]To get you nvidia module running under your i686 kernel all you need to do is install the linux-restricted-modules-686. At your terminal just do this.

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install linux-restricted-modules-686

Then boot up with your 686 kernel and you should now have video for X again.

Joe[/QUOTE]


Silly question, I have the 686 installed and it is killing my laptop, so, I also have the 386 installed and works great, how do I remove 686 kernel?

thanks!

---

### Post by Xian on 2005-05-25
[QUOTE=garnertr]Silly question, I have the 686 installed and it is killing my laptop, so, I also have the 386 installed and works great, how do I remove 686 kernel?[/QUOTE]
```
$ sudo apt-get remove linux-image-2.6.10-5-386
```

---

