---
title: "Got Ubuntu, Need Windows (Dual Boot)"
date: 2007-12-08
forum: General Help
---

### Post by Green_biri on 2007-12-08
Hi everyone. First of all, I've searched but found nothing so here it is:

I got my HDD with Ubuntu installed (one partition with 20GB to / and another with 80GB to /home)

Anyway, I'd like to install Windows, by resizing my /home partition, but I don't know how to do It... if I run GParted, It doesn't lemme choose the "Resize" option... any help?

Thanks.:)

---

### Post by teryowen on 2007-12-08
Its because the partition was still mounted whichis why you cant play with it.

Boot of a live CD and resizei t from there.

---

### Post by Green_biri on 2007-12-08
> **teryowen said:**
> Its because the partition was still mounted whichis why you cant play with it.

Boot of a live CD and resizei t from there.

Oh... Thanks, then...:)

---

### Post by Green_biri on 2007-12-08
Well, I succefully installed Windows... but now I got two options in the boot screen:

Windows XP Professional Edition
And...
Windows XP Professional Edition :confused:

I think I've deleted my / partition... my Ubuntu Partition :shock:
But now I can't see what did I really deleted... Any advice? :(

Thanks...

---

### Post by teryowen on 2007-12-08
boot up of the live CD and post the output in terminal of:

sudo fdisk -l

---

### Post by staticvoid on 2007-12-08
boot with your live cd of gparted... if you really need the data in the partition then you will need to reinstall GRUB, Which might be pertty complicated...
You can also see what partitions you have and what is on each one. 

The easiest way:
Wipe your system and install Micro$oft Windoze
Pop in your live cd and install ubuntu on the D drive,

then Ubuntu will recognize windows. You may want to set up a Fat32 shared partition... google "dual boot ubuntu and windows" and check out a tutorial, theres different ways of dual booting..

sv

---

### Post by Green_biri on 2007-12-08
> **teryowen said:**
> boot up of the live CD and post the output in terminal of:

sudo fdisk -l

Ok, lemme just sync my iPod then I'll post the output...

---

### Post by 0600 on 2007-12-14
HI im having a very similer problem I have a partition about 80 gigs each side of it and my windows wasnt working a friend recomended Ubuntu so i said ok installed it and i love it ... BUT i want to have both only thing is im not sure how too reinstall my windows cause wen i pop in the disk restart it says booting from disk then nothing.... and more nothing jus a blanc screen... uhh so plzz help:confused:

---

### Post by HermanAB on 2007-12-14
If you want to dual boot, then you have to install Windows FIRST.  Otherwise, you ll have to jumpo through some hoops to restore grub.

The easiest way to have all kinds of OSs on your machine is to go virtual and install VMware or Virtual box and then install whatever you want as a VM.  That way, you can run Windoze in a window, which is far more convenient than dual booting.

Cheers,

H.

---

### Post by VipeR_11 on 2008-04-15
> **HermanAB said:**
> 
The easiest way to have all kinds of OSs on your machine is to go virtual and install VMware or Virtual box and then install whatever you want as a VM.  That way, you can run Windoze in a window, which is far more convenient than dual booting.

Cheers,

H.


I agree with you but only if yuo need windows for basic staff.
If you try to use heavy software using windows under VM it's going to slow you down like you have install windows vista in a 10 years old PC...!

---

