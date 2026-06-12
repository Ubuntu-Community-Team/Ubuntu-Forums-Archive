---
title: "symbianOS7.0 and mounting in Ubuntu"
date: 2005-04-10
forum: General Help
---

### Post by b33rc4n on 2005-04-10
Hi there again!
I just got myself an motorola a1000 running symbianOS7.0 and I of course want to mount it in linux.
I got my fat paws on this p3nfs 

> 
Package: p3nfs (5.15-2) [universe]
Mount Psion series 3[ac], 5 drives

A Symbian (Psion/Nokia/Sony-Ericsson/etc) to UNIX/Linux communication program. It allows you to mount the file systems of the Phone/PDA on your UNIX machine. This means that you see all the filesystems of the Phone/PDA as a filesystem on your UNIX machine, and you can copy/backup/edit any file on the Phone/PDA with your preferred tools on the UNIX machine.

Supported devices are those running one of:

 SymbianOS R7.0 (Sony/Ericsson, Motorola, BenQ)
 SymbianOS R6.1 (Some Nokia, Siemens, Samsung)
 SymbianOS R6 (Nokia Communicator)
 EPOC32 R5 (Psion 5/5mx etc.)
 EPOC16 (Psion 3 etc.


I did just that ran it as root created the requested dir (/mn/psion) and fired it up!
No error message!! Wohooo!! 
 :D
So I check the dir and.... no nothing! just empty space! 
aww!! It was so close!!
 ](*,) 

So anybody out there who knows how to get this thing mounted properly? Do I need to insert stuff into fstab or what is the deal here???

HELP this mega n00b!
thnx in advance guys/gals!!

---

### Post by b33rc4n on 2005-04-11
Ok I've also installed USBview and I get a nice list of information about the USB attached A1000 (wont post this here). So my comp apparently sees this device... 

:neutral: 

any linux guru out there that can throw some light on this?

thnx in advance!

---

### Post by kombipom on 2005-06-16
I'm afraid I can't help as I'm in exactly the same situation (except its a SE P800 I can't mount).  I installed p3nfs but it requires a .sis file to be installed on the handheld which isn't in the package for some reason.  The documentation gives instructions for downloading the SDK from SE and installing a cross-compiled version of gcc... and on and on and on it goes, way over my head (I can never get anything to compile from source anyway).  Is it really necissary to go to all these lengths just to mount it and transfer files back and forth?  From what I understand all this cross-compiler-SDK stuff is to develop apps for the P800 in Linux.

If someone could supply the .sis file or tell me where I can get it I think it should work but I've tried searching the net and come up with zilch.

All help/comments welcome.

kombipom

---

### Post by reedlaw on 2005-07-07
I just got my Psion Revo to be accessible through plpftp.  The phpnfs didn't work for me though.  I followed the guide here: [http://timocharis.com/help/mako.html](http://timocharis.com/help/mako.html)

---

### Post by debernardis on 2005-12-17
I am in the same situation with my nokia 9500.
/mnt/psion is empty, BUT...
...if I issue "cd c:" it indeed changes directory... do try, please, and let me know it it's the same for you

---

