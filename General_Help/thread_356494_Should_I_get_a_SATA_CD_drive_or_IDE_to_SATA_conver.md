---
title: "Should I get a SATA CD drive or IDE to SATA converter--need SATA to boot CDs"
date: 2007-02-08
forum: General Help
---

### Post by presbp on 2007-02-08
I have a
JMicron controller on my motherboard.. I have an Asus P5B Deluxe/Wi-Fi
AP motherboard Intel P965 Express northbridge and Intel ICH8R
southbridge.


I am only getting a SATA interface to connect with one of my IDE drives so I can boot CDs. I currently cannot because the JMicron controller HAS to have a driver installed to work The thing is with the converter that it would be good if I ever had to boot a DVD.



My questions are.. Will a drive connected to the same SATA controller as the hard drive disrupt the hard drive?



Which should I get.. the $15 SATA CD drive or the IDE to SATA adapter?



that is the IDE to SATA converter [http://www.newegg.com/Product/Produc...82E16822998001](http://www.newegg.com/Product/Produc...82E16822998001)



here is the SATA CD drive

[http://www.newegg.com/Product/Produc...82E16827106038](http://www.newegg.com/Product/Produc...82E16827106038)

---

### Post by disturbedite on 2007-02-08
i'd say get the sata cd drive.  i have a sata300 hdd installed along side an ide hdd and an ide cdwriter and ide dvdwriter.  all works fine.  i had to get a pci sata300 card, since my mobo is too old to support sata.  :(
the way sata works is different than ide, there isn't any master/slave/cs crap to worry about any more.  the sata protocol/standard apparently is "intelligent" so it shouldn't interfere with any other sata drives you have.

---

### Post by dannyboy79 on 2007-02-08
you don't have to do either, according to the JMicron website, you just have to add this to your boot line in Grub before the Ubuntu Live CD starts booting.
I don't see why this wouldn't work with Ubuntu.

Can I install Fedora or Redhat from IDE cdrom which attached on JMB pata port in early kernel version ? 
Ans: Yes , kernel already built-in parameter "all-generic-ide=1" to support newer controller 
Ex: "boot:linux all-generic-ide=1" 

I also found this on another website:

on the Intel P965 (may be include G965/Q965) + ICH8R (+ JMicron) based motherboard that has no native PATA support, and instead using the JMicron chip for its PATA controller, and while your hard drive(s) are using ports of the ICH8R and your PATA DVD drives is under the port of the JMicron chip... 

the workaround for this problem which myself have suceesfully tested it out is to set in the BIOS for the JMicron controller to be in AHCI mode, and at the very first phase of the setup add "insmod=pata_jmicron' to the boot options 
 
good luck

---

### Post by dannyboy79 on 2007-02-08
actually sorry, I just read thru this bug report here: [https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/57502](https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/57502)
and it states that the above solution by adding that thing in the boot line doesn't work for ubuntu because when they compiled the kernel they didn't add that support in. It depends though, so you should try it first before going out and buying anything. If I were you I would NOT get an adapter, then you are losing the speed of SATA.

---

### Post by kebes on 2007-02-08
I've dealt with this JMicron problem in Intel 965 chipsets. It is basically impossible to boot off of IDE devices with it, unless your kernel version is 2.6.18 or higher. Unfortunately Edgy doesn't ship with that kernel, although Feisty will. (Fedora Core 6 and OpenSUSE currently do, which is why they can be coaxed into booting from IDE CD-ROMs.)

I would buy a SATA optical drive. You'll be taking full advantage of SATA, which is nice.

---

### Post by dannyboy79 on 2007-02-08
or check this out, [https://wiki.ubuntu.com/Core_2_Duo_Support](https://wiki.ubuntu.com/Core_2_Duo_Support) and go down to the section that talks about the JMicron pata controller.

---

### Post by presbp on 2007-02-08
I am trying to boot Linux From Scratch and Puppy Linux but the only CD I have been able to boot from is the Ubuntu CD.

---

