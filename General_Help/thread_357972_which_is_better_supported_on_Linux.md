---
title: "which is better supported on Linux?"
date: 2007-02-10
forum: General Help
---

### Post by Jeffa on 2007-02-10
Hello all, 

I'd like to build a file server running Ubuntu. Being new to Linux, I was just wondering if anyone could tell me which was better supported, Areca or 3ware. 

Thanks for the insight.

---

### Post by koenn on 2007-02-10
Unless you have a specific reason to only choose between Areca or 3ware, you might want to chack out Samba. It's in the Ubuntu repositories.

---

### Post by Jeffa on 2007-02-10
Well, I wanted to build a hardware array, not software.

---

### Post by koenn on 2007-02-10
oh, ok. 
is that NAS we're talking about then or am I still getting it wrong ?

EDIT - ah, RAID Controllers - now I get it. 
Sorry - no experience with those.

---

### Post by koenn on 2007-02-11
you may have to go looking for some compatibility lists, such as 
[http://www.linuxcompatible.org/compatlistcat11.html](http://www.linuxcompatible.org/compatlistcat11.html)
Areca seems supported - with tweaking : [http://www.wlug.org.nz/ArecaNotes](http://www.wlug.org.nz/ArecaNotes)
3Ware offers linux drivers on their website [http://www.3ware.com/support/download.asp](http://www.3ware.com/support/download.asp) but those will probably not be ubuntu-specific. 

Other than that : hopefully someone will come along who has actually used those controllers before with ubuntu  :)

---

### Post by Corvo78 on 2007-02-23
I'm in the middle of installing my fileserver. I made several failed attempts to setup my nvidia FakeRaid...
...which quicky lead to the fact that I bought myself a **"3Ware Escalade 8006-2LP" SATA2 Raid controller**.

I bought this card because 3ware actively supports Linux.


Booting up Ubuntu's installer and the array worked from the get-go... the OS simply sees 1 drive :)
The drivers for 3ware cards are included in the current (Ubuntu) Linux kernels!

If you want to manage the RAID array from within the OS (instead of the BIOS) you can choose the install 3DM2 (web-based configuration) and a CLI interface.
(Though it is advised to only install 3DM2 or CLI, not both)

3DM2 and the CLI interface are available as DEB packages in the Debian repositories and work flawlessly when installed on Ubuntu.
The DEB packages should be easy to find, the package maintainer even has his own website, iirc.

Good luck :KS

---

### Post by Jeffa on 2007-02-23
Thanks! that was very helpful. I'm leaning towards the 3ware now! 

(i only hope it will work in the Asus p5w dh!!!)

---

### Post by Corvo78 on 2007-02-23
Glad to help out.

*One more thing:*
The 3ware controller I mentioned is PCI-X, which is 64-bit / 66Mhz card (3 volt).
My motherboard (ASUS A8N SLI deluxe) only supports regular PCI, which is 32-bit / 33Mhz (5 volt).

In form-factor PCI-X is compatible to PCI (allthough they are larger)... but bitwise and voltage wise... good news:
The 3ware PCI-X card is nicely _backwards compatible_ to regular PCI ;)

---

### Post by Jeffa on 2007-02-23
Also good to know. Thanks again. 

what kind of performance do you get from the controller when it is in a standard pci slot?

---

### Post by Corvo78 on 2007-02-23
I haven't done any benchmarks, but as far as I can tell the array performs just a well/fast as a regular drive.


*From what I read:*
PCI 32-bit simply works in RAID0 or RAID1, if you go RAID5 and such the lack of bandwith seems to become evident.

Above mentioned 3ware controller has only 2 SATA ports and thus only supports RAID0 or RAID1.
So for that controller, a PCI 32-bit does the job.

---

### Post by Jeffa on 2007-02-23
Dang, i was hoping to set up a raid 5. 

Thanks for the info though. You've definitely helped. I have some ideas now. I'll have to do a little more research.

---

### Post by Corvo78 on 2007-02-23
I don't know if 3ware has them (I doubt they don't though), but there are also PCI express (PCI-e) RAID controllers.
I believe those can sustain RAID5 and such without any problems. Allthough it requires you have a corresponding PCI expresse slot available on your motherboard.


*(I think I've shared about everything I read up on :) )*

---

### Post by Jeffa on 2007-02-23
yeah, i've been looking at the areca 1220, which is a pci-e card. but i'm looking at using the Asus p5w dh mobo, which has two pci-e slots. but asus' official stance is that they design their pci-e slots specifically for graphics cards, and other controllers aren't officially supported. any other card used in those slots is solely at the risk of the user. from what i've read, some people have had success with pci-e raid controllers in this mobo, others have not. So i was looking for an alternative to the pci-e option. 

so, thanks again, sounds like there is hope yet!

---

### Post by Jeffa on 2007-07-02
Update:

I went with the Areca. For more info check out [this]("http://ubuntuforums.org/showthread.php?t=390401") thread

---

