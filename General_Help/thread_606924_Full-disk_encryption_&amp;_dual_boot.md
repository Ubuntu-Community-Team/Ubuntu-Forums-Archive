---
title: "Full-disk encryption &amp; dual boot"
date: 2007-11-08
forum: General Help
---

### Post by Dave / Mosaic on 2007-11-08
I'm in the process of creating a dual-boot laptop, Ubuntu 7.10 and Windows XP, and I want strong, reliable full-disk encryption (or, more accurately, fully encrypted partitions) for both operating systems.

Under Gutsy by itself, this looks to be straightforward, with the LUKS / dm-crypt / LVM stuff built into the alternate intall CD...

Under Windows XP, likewise, things would be straightforward and quite secure, by buying a copy of DriveCrypt or something similar...

However, it's not clear to me, what the best way is to have a fully-encrypted, dual boot system.  Is anybody doing anything similar?

As far as I know (which is not very far) I don't think XP could boot from a dm-crypt encrypted partition... and, I can't see how to make grub boot an XP installation protected by DriveCrypt...  or vice versa,,,  Nor am I aware of any cross-platform full-disk encryption tools that can operate at the OS / bootloader level...

Anybody have any ideas?

--dave

---

### Post by Dave / Mosaic on 2007-11-09
Hmmm...  Okay, well, no bites on this so far.  How about this, then:

Can anybody point me to a good, clear, in-depth description of how booting works in the case of Ubuntu 7.10 with a fully encrypted root filesystem, using dm-crypt, LUKS, etc?  I'm a beginner at this but trying to learn; my understanding is a bit foggy in the area of bootloaders, and particularly what goes on in the master boot record of a dual-boot system when grub is installed in a location other than the MBR.

I'm looking at DriveCrypt for the encryption of the XP portion of my dual-boot system, but they seem to have their own authenticating boot loader that loads some type of encrypting driver or windows kernel, and I'm still at the stage of trying to figure out how it all works in each case, on the way to  (hopefully) figuring out how to construct my own dual-boot fully-encrypted system.

Thanks much--

--dave

---

### Post by Dave / Mosaic on 2007-11-09
Also, I'm wondering if there's any such thing as a program that I could install into the MBR of my partitioned disk, that could allow me to select among different bootloaders...  Sort of like a bootloader-loader...?

The catch that I seem to be running into, is that the linux kernel and drivecrypt each seem to have their own bootloader that asks for a passphrase and uses it to decrypt a filesystem to in turn load a kernel from... and neither of the types of system is able to work for the other OS...

--dave

---

### Post by shappyhopper on 2007-11-09
Hi Dave,

I've just finished writing a similar guide for a dual boot openSuSE 10.3/ Windows XP system, using nothing but free software. I hope you can adapt it for Ubuntu.

It encrypts the whole of the Linux installation (except for /boot) and under XP encrypts the pagefile and moves all personal files etc to an encrypted volume (but leaves C: unencrypted). 

By using XP ext2 drivers you can make this volume ext3 and share with Linux (the guide shows how to make a very large /home that can also be used by Windows).

I hope this is of some use, the page is here:
[http://shappyhopper.co.uk/b2154/encrypteddualboothowto.cgi]("http://shappyhopper.co.uk/b2154/encrypteddualboothowto.cgi")

I am the first to admit that the html version is difficult to read, so I have also posted a PDF version here:
[http://shappyhopper.co.uk/b2154/encryptedhowto.pdf]("http://shappyhopper.co.uk/b2154/encryptedhowto.pdf")

I hope this is of some help, feedback gratefully received:
[http://www.shappyhopper.co.uk/feedback.pl]("http://www.shappyhopper.co.uk/feedback.pl")

Regards,

Ed (shappyhopper)

---

### Post by Dave / Mosaic on 2007-11-12
Well, thanks; I'll have to take a look at the mechanics of that.

However, I'm wanting to get the fully encrypted root filesystem under Windows XP as well, which is the tricky part for me...

Though, reading about grub, it looks like grub should be able to chain load another bootloader, so once I get full-disk encryption under XP, perhaps I'll be able to get grub to boot both it and encrypted linux in the end, after all...

--dave

---

### Post by staticsage on 2007-12-17
Read the comments posted here: [http://blog.incase.de/index.php/2006/11/13/dual-boot-and-full-encryption/](http://blog.incase.de/index.php/2006/11/13/dual-boot-and-full-encryption/)

> However, the following worked for me:

- Install Windows
- Create the partitions intended for use with Linux before encrypting. CompuSec seems to change the partition type of partitions created after encryption to 0×07 (NTFS) at every reboot. It doesn&#8217;t do this if the partitions were there before encryption.
- Install CompuSec and encrypt the entire hard disk
- Install/copy your installed Linux to the partitions you created earlier, using dm-crypt at your convenience
- Follow the steps in Jari Eskelinen&#8217;s HOWTO, using GRUB to launch the CompuSec MBR

You&#8217;re done.

Careful: If you ever decide to decrypt your hard disk using CompuSec, CompuSec will use your Linux partitions as the cipher text and turn them into gibberish, so do backup your data!

Compusec: [http://www.ce-infosys.com/english/downloads/free_compusec/index.html#download](http://www.ce-infosys.com/english/downloads/free_compusec/index.html#download)
Jari Eskelinen's HOWTO: [http://keitin.net/jarpatus/articles/dcpp_grub/index_eng.shtml](http://keitin.net/jarpatus/articles/dcpp_grub/index_eng.shtml)

Basically you use Compusec to encrypt your windows system and dm-crypt for linux. You're using grub to boot into your encrypted linux system and the Compusec MBR (chainloaded by grub)  to boot into windows.

You can probably replace Compusec with your favorite Windows FDE solution, but I have not tried this myself so I really don't know. I would love to know how it works out if you go this route. I plan on doing this in the future... I just need to get some spare hardware and time to kill.

---

### Post by cader47 on 2008-01-02
you can use 2 hardrives thats about it though

---

### Post by epiphiny on 2008-04-22
Hi there,

I've just created a tutorial to tell you exactly how to perform a full disk encryption on windows and ubuntu.

You can find it here:

[http://http://ubuntuforums.org/showthread.php?t=761530]("http://http://ubuntuforums.org/showthread.php?t=761530")

Hope this helps!

---

