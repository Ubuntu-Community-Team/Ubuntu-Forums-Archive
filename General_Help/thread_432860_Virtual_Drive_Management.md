---
title: "Virtual Drive Management"
date: 2007-05-04
forum: General Help
---

### Post by Harkainos on 2007-05-04
On Windows I would use Daemon Tools to virtually mount ISOs stored on my hd. Is there any program that does that in Linux? Some games (windows versions) require a CD and I am not sure how to simulate that.

I am running Edgy and Wine 0.9.35

---

### Post by angryfirelord on 2007-05-04
Wine should automatically pick up any cds that you have inserted. Make sure the disk is mounted.

Run winecfg and under the drives, click autodetect. Check the cd or dvd drives that you have mounted, click on the drive letter, and under Media type (or something like that), select CD-ROM.

---

### Post by Harkainos on 2007-05-04
thats pretty cool. I will do that when I need the cd. 

Is there a virtual drive system in linux. So i can 'mount' isos?

---

### Post by rax_m on 2007-05-04
In Linux the abiility to mount ISO images is built into the kernel. So you should just be able to mount the image and then point another application to that filesystem. This link has some details.. hope i didn't misunderstand what you want. 

[http://steinsoft.net/index.php?site=Programming/Articles/linux-mountiso](http://steinsoft.net/index.php?site=Programming/Articles/linux-mountiso)

---

### Post by Harkainos on 2007-05-04
I think that will do fine. I can create shell scripts for each ISO, then just run them when needed. Thanks.

---

### Post by kleam on 2007-05-04
OHKAY SO, I am new to Ubuntu, as well as Linux and I will have the same problem mounting ISO. I didn't really understand when you said the following:

> **Harkainos said:**
> I can create shell scripts for each ISO, then just run them when needed.

The ISO's I have are copys of games that i use to have the cd of, but don't currently have right now. How would I Mount my ISOs so i can install my games?

Would I make shell scripts above?

I really don't understand



-Kleam

---

### Post by Harkainos on 2007-05-04
You dont have to....
You could simply follow those steps in the tutorial, each and everytime you want to mount an ISO.

I would only write a script so that it runs those commands when I click a button, that is all.

---

