---
title: "S-ata"
date: 2005-10-16
forum: General Help
---

### Post by sedi on 2005-10-16
Yesterday I updated Ubuntu to 5.10 or at least I tried. Everything worked fine until I turned off the computer. When I turned it back on Ubuntu 5.10 seemed to start fine but after a few second it starts repeating error messages like this one:

libata:ata_scsi_error21

and continues with:

: scsi_mod:scsi_error_handler+290 (this is repeated with different values after + )

the last thing I understand is:

code: bad RIP value

The rest is numbers and then nothing happens anymore.

As far as I understand it 5.10 doesn't like my S-ATA hard drive. 5.04 didn't have any problems and I can still use 5.04. But 5.04 also just said I have an SCSI hard drive and it didn't recognize my S-ATA DVD drive. I tried to install 5.10 with the CD too but it reproduces the same error. Any idea how I can make Ubuntu 5.10 work with S-ATA?

my hardware:

AMD 64 3500+
mainboard: MSI K8T Neo2 (MS-6702E)
S-ATA DVD drive (Plextor PX712SA) connected to the VIA VT8237 chipset
Samsung S-ATA 160 GB connected to Promise 20579

---

### Post by Teroedni on 2005-10-16
Is your board overclocked or any?
It may be giving problems with s-ata(maybe brezzy is more sensy?)

---

### Post by sedi on 2005-10-16
No, my board is not overclocked. I heard that I would need a kernel that already supports sata but where do I get one or does anybody know how I can compile my own kernel with sata support?

---

### Post by sedi on 2005-10-16
Btw, I forgot to mention that I have one DVD drive in my computer that is IDE. Otherwise I wouldn't even be able to install Ubuntu or Windows (which also gave me a hard time installing it).

---

### Post by Teroedni on 2005-10-16
are you running AMD64 kernel or i 386?

---

### Post by jordilin on 2005-10-16
Hi,
I've searched over the net, and I've found the following link. It's quite interesting if you are having problems with sata:
[http://linuxmafia.com/faq/Hardware/sata.html](http://linuxmafia.com/faq/Hardware/sata.html)
Perhaps, this link has the solution for you,
good luck,

---

### Post by sedi on 2005-10-16
@ jordilin Thank you for the link they have some information about my chipset but it'll take me some time to understand that. 

They say libata is the driver that could work on my computer (if I understood that correctly) and it did with 5.04 but doesn't with 5.10 . They also say that there's a patch for libata but how should I patch libata prior to installing 5.10? That would mean I have to compile my own kernel, right?

@Teroedni I'm running an AMD 64 kernel.

---

### Post by sedi on 2005-10-16
Should I hook up my hard disk to the VIA chipset? Could that work or would I damage my hard disk doing that? I mean basically there's no need for one drive to be hooked up to a raid controller but this was the only way Windows could find my hard disk.

---

### Post by Teroedni on 2005-10-16
If your via chipset ia Serial ata yes;) you can hook it up.

Also it may work better in i386 kernl. If you have time you culd install a 386 kernel and see if thath works better.

But check the Bugzilla and see if your problem is listed there
Theres where the developers look out for problems. If your problem doesnt exist there submit it and it may come an fix:)

---

### Post by sedi on 2005-10-16
Ok, thanks. I'll try that and I'll tell you later if it worked.

---

### Post by jordilin on 2005-10-16
Are you using the same kernel as the Hoary version?. As you say you didn't experience any problem with hoary, did you? Do an # uname -r

---

### Post by sedi on 2005-10-16
Nothing worked. Neither the i386 kernel nor hooking up the hard disk to the promise controller. Bugzilla only has a report that my SATA DVD drive is not supported but has no solution whatsoever.
@ Jordilin No, when trying to access my 5.10 installation ther kernel has a different version number than the kernel of the Hoary installation which works.

---

### Post by sedi on 2005-10-16
Anybody knows how to patch libata before installing ubuntu? If I manage to do that it might be possible to get 5.10 running.

---

### Post by Teroedni on 2005-10-17
Stupid me i dident see you had a serial ata dvd drive](*,) ](*,) 
You have tried the dvd drive on both  seriual ata controlers?
and you have tried  your hard drive on both to?

You have tried to install with a brezzy 5.10 cd?

---

### Post by sedi on 2005-10-17
I tried the hard disk on both controllers but I didn't hook up the DVD drive to the VIA controller because it's a raid controller (I think). Hoary also didn't recognise the DVD drive but this is a problem I found in the Bugzilla (unfortunately no solution was provided).
I tried to install the AMD 64 kernel and the i386 kernel with the CD. It didn't work. I once again tried to start Ubuntu 5.10 and I found another error message that was something like: libata sata_promise unable to load into kernel.

---

### Post by Teroedni on 2005-10-17
so when you install using cdrom paralell ata where does it stops?
have you tried to install via paralell cdrom when
1.Hardrive connected to promise serial chipset
2.hardrive connected to via serial chipset

What error do you get?


also have you tried live cd on parralell cdrom anc checked if you can see your hardrive from it?

---

### Post by sedi on 2005-10-17
The installation stops like 30 seconds after I hit the enter button where you're asked how you want to boot from CD. 20 seconds after I hit the enter button I get a bunch of error messages related to libata.
I tried to install with the hard disk connected to both controllers. The last error messages I get are those I described in my first post but I made a picture of it and as soon as I'm home I'll post it here.
I haven't yet tried that thing with the live CD but i'll try it when I get home.

---

### Post by sedi on 2005-10-17
Voilà the image of my screen when the installation process freezes.

---

### Post by sedi on 2005-10-17
Does the image help in any way?

---

### Post by Teroedni on 2005-10-18
its seems  the cd has no support for it:(
I unfortunaly dont know what to do ?

I will se if i can Google some ,but i dont think i will find the solution.

Is there any other there out which do more about this problem? im lost:(

---

### Post by sedi on 2005-10-18
Thank you very much for yout help Teroedni. If Ubuntu doesn't work on my computer: bad luck. I can just hope that 6.04 will run on my computer and maybe they do some changes to the installer. In the meantime I'll have to find another distro that runs on my computer or I'll use 5.04 without my DVD burner.

---

### Post by jamieson on 2005-11-02
Any luck with this setup?  

I just installed a Plextor PX-716SA DVD drive (SATA) and breezy can't see it at all.  No error messages, nothing in the system logs.

The motherboard detects it and I can boot from the DVD drive, though.  I'm using a Soyo motherboard with a VIA chipset.

Searching around on google I'm finding some suggestions about modifying libata.h because ATAPI is not enabled by default for the Debian stock kernels?  

If someone has encountered this please post some information on what worked for you.

thanks,

jamieson

---

### Post by metoo on 2005-11-03
Attach the hd to the VIA S-ATA this should be OK. The promise could be tricky as it could require firmware to load (not sure). I have a K8T800 Pro and S-ATA works just well. You may have to change something in the BIOS. Make sure, that you have not selected RAID for the VIA there. Try without the S-ATA DVD on the VIA or at all, just to ensure, that it isn't irritating the system. If you updated: the S-ATA devices are now labeled as SCSI devices, starting from sda, no longer hde as in hoary.
Damn, this fooled me, 2 week old post :-)

---

### Post by jwmislan on 2006-01-04
Hi jamieson 

 I have been going through the same problems getting sata, Plextor PX-716SA DVD
to function in linux for some months now.

 I have Soyo KT600 Dragon Ultra Platinum - bought it last year 2-05 .
It uses a VIA 8237 sata controler, and also a Silicon Image, Sil3112 sata controler. Both can do RAID, or Normal ATAPI modes.

  I could never get the plextor dvd to work with the via controler in linux, and either could anyone else
as from what I researched through google. 
After using debian sarge for a while, (couldn't get it to work with sarge either),   
I was able to get the Plextor DVD to work after switching it to master on the Sil3112 and, installing Ubuntu Breezy.
I now have Plextor PX-716SA, and Hatachi 80 gig SATA HD, running off that same controler,  bios is set of course, 
to normal mode, and not RAID .
I've read that the VIA 8237 controler, is noted to have problems with libata functioning with serial ata CD's & DVD's. 
  I don't know if this is any help for your situation , but I sure do hope it is, because  I can Identify with it being a pain when things don't work right.
  
 JohnWM

---

### Post by Toshibi on 2006-03-18
I'm having similar problems. I've been using Ubuntu 5.10 in VMware getting myself used to linux....but now I cant make it my primary OS.

I have an MSI XA52P SATA DVD/CD-RW and a Seagate SATA HDD on an Intel D915GAV Mobo, 3.0 GHz P4 HTT, with a Gig of RAM and PCIe NVidea 128 MB graphics card. 

Ubuntu was so fast and friendly in VMware with piggy Windows....I was salavating at the oportunity to use it all by itself!:-?

---

