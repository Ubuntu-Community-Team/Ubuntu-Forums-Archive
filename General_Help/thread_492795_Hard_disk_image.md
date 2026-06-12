---
title: "Hard disk image"
date: 2007-07-05
forum: General Help
---

### Post by Riccardo63 on 2007-07-05
I there any Linux tool to make hard disk images?
Like Ghost or Acronis true image for example.

---

### Post by scxtt on 2007-07-05
the one i know of, and use, is partimage ... can't use it on a mounted f/s, but i boot from a LiveCD, load up partimage, and copy the disk ...

---

### Post by ramjet_1953 on 2007-07-05
[COLOR="Blue"]Ghost for Linux (G4L)[/COLOR] will do exactly what you want.

You just download the iso image, burn it as an iso to a CD and boot the system from it.

One of the options is to make a local clone of your hard drive.

It makes an exact 1:1 copy, including GRUB.

Here is the link to download the iso:

[http://sourceforge.net/projects/g4l](http://sourceforge.net/projects/g4l)

ps remember to burn it SLOWLY. No faster thatn 4X.

Regards,
Roger :cool:

---

### Post by simpsonatwork on 2007-07-31
Does Acronis True Image, running from Windows, work for Ubuntu partition? For example, i have a dual-boot system, XP & Ubuntu, and have True Image installed on Windows (and it's able to work from a standalone boot CD). Will it do its job  for Ubuntu partition? In help they say that ext3 filesystem is supported.

---

### Post by viking777 on 2007-08-09
> **simpsonatwork said:**
> Does Acronis True Image, running from Windows, work for Ubuntu partition? For example, i have a dual-boot system, XP & Ubuntu, and have True Image installed on Windows (and it's able to work from a standalone boot CD). Will it do its job  for Ubuntu partition? In help they say that ext3 filesystem is supported.

Yes Absolutely. I use it every day to make a disc image of Kubuntu Gutsy and it does an absolutely perfect job and very quickly too whether or not you use the disc or run it from windows. I've also restored many times from it and again it does the job perfectly (the only trouble you might have is if you try to restore to a different sized partition, but that is not difficult to deal with). This is one of the best pieces of software I have ever owned - if you have it use it ( and don't bother with partimage it is a real dog)

---

### Post by scxtt on 2007-08-10
in what way is partimage "a real dog"?

---

### Post by mcduck on 2007-08-10
"dd" is a command line tool for this task, and it's installed by default.

---

### Post by viking777 on 2007-08-11
> **scxtt said:**
> in what way is partimage "a real dog"?

Partimage is not a real program it is just a precompiled list of excuses. I've tried dozens of times to get it to do something - anything! and all it does is give a list of reasons as to why it can't do them. There is only one program worse than partimage in the Linux world - Grub.

---

### Post by HermanAB on 2007-08-11
Netcat, gzip and dd are all you need:
[http://aeronetworks.ca/netcat-howto.html](http://aeronetworks.ca/netcat-howto.html)

...and you already have it on your system!

Cheers,

Herman

---

### Post by viking777 on 2007-08-11
> **HermanAB said:**
> Netcat, gzip and dd are all you need:
[http://aeronetworks.ca/netcat-howto.html](http://aeronetworks.ca/netcat-howto.html)

...and you already have it on your system!

Cheers,

Herman

I have had a go with dd and gzip and indeed it did seem to produce a backup. Never tried restoring from it though (don't even know how to!) but the main thing is I don't know if I can trust it with something as important as disc imaging. I know that I can trust Acronis though I've used it countless times without worry. I suppose I should really experiment with dd and see if it is trustworthy.

---

### Post by HermanAB on 2007-08-11
Well, dd has been around for  much longer than Ubuntu.  It is pretty much the standard way that professionals use to roll out copies of systems.  I have used it hundreds of times myself - many thousands of times in the companies I have worked at.

---

### Post by scxtt on 2007-08-11
> **viking777 said:**
> Partimage is not a real program it is just a precompiled list of excuses. I've tried dozens of times to get it to do something - anything! and all it does is give a list of reasons as to why it can't do them. There is only one program worse than partimage in the Linux world - Grub.just because it doesn't work for you (for whatever reason you haven't provided) doesn't make it an unusable tool for anyone else ... i've used it dozens of times and it has served me well (i'm sure i'm not the only one) ...

chances are you're doing something wrong or using it incorrectly ...

---

### Post by viking777 on 2007-08-12
Well as an experiment I just did a backup and restore of my PClinux system using dd. The good news is it worked but the not so good news is the length of time it took to do so.
The disk size is 2.67Gb dd compressed it to 2.4Gb and took 20mins 38sec to do so.
Acronis compressed it to 1.1Gb and took 5mins 29sec and that *includes* the time it took to reboot into windows.
The restore took 10mins 18sec it usually takes Acronis about half that.
Of course the bad news about Acronis is that you have to pay for it and either run it from windows or off a hard disk.

---

### Post by viking777 on 2007-08-12
> **scxtt said:**
> just because it doesn't work for you (for whatever reason you haven't provided) doesn't make it an unusable tool for anyone else ... i've used it dozens of times and it has served me well (i'm sure i'm not the only one) ...

chances are you're doing something wrong or using it incorrectly ...

I am sure you are right that I am doing something wrong with partimage, but I am not a complete dunderhead and I do know a little about Linux and I still can't make it work. The original reply was to a linux newbie and if I can't get it to work then the chances are he won't either, and as he already owns Acronis (which a child of 6 could operate) then I think he is far better off using that for issues as important as disk imaging, and until partimage can come up with a way to make their program more useable I will stick with Acronis as well.

---

### Post by HermanAB on 2007-08-12
One can speed 'dd' up enormously using a couple of simple tricks.  The Block Size parameter 'bs' is the most important.  When copying disks over a 1Gb/s network, a block size of 100K is best.  When copying one disk to another on a single machine, 16K may be best, but do experiment a bit:
dd if=sda of=sdb bs=16K

If using netcat over a fast net, it also helps to gzip the data and compress gigabytes of zeros to next to nothing.  I have copied a 750GB disk in 2 hours over a 1Gbps net like this:

On the destination machine:
nc -l -p 5000 | gunzip | dd of=/dev/sda bs=100K

On the source machine:
dd if=sda bs=100K | gzip --fast| nc 1.2.3.4 5000

You can see the speed by sending 'dd' a signal from another terminal, then you can press Ctrl-C to stop it and try again with different parameters, till you know what is fastest:
ps | grep dd
kill -USR1 PID

'dd' will hiccup and give the speed data, then carry on.

Cheers,

Herman

---

### Post by viking777 on 2007-08-13
Thanks for the reply Herman.

I didn't specify a block size so perhaps that is why the copy was slow. I am only backing up to the same machine, not across a network, so the netcat commands are not applicable, but thanks anyway, you never know I might want to do that some day.

---

### Post by bricksen on 2007-08-13
I downloaded and burnt sysrcd-0.3.7 and tried to make a image of my hda7 and everything seemd to work fine until i saw that i was running out of space. It stored it on detected extfs3 or something?

1) How do I tell partimage where to store the file I want to save it to? Is there a howto?
2) Can i store on hda7 and make a new partition when i see how big it is or do I have to make a new partition first?

---

### Post by bricksen on 2007-08-13
I'm probably stupid but I never got a choise where to save the file only what file to save.
If anyone who nows how this work could write down the right command to write after chosing the partion to save "what file to save" I would really preciate it.

---

### Post by scxtt on 2007-08-13
if you're talking about partimage (you were w/ "1)") - you highlight the partition you want to save - then you type in the path to the file you want to save ... so you'll have a listing like the following (for example):
```
/dev/sda1          100MB ext2
/dev/sda2           70Gb ext3
/dev/sda3            9Gb fat32
/dev/sdb1          160Gb ext3
```

then you'll have a textarea you can type the path too ... so you would highlight /dev/sda2 and then type the path to a mounted partition and a file to save:

/media/sdb1/PARTIMAGE_saves/sda2_ubuntu_save

keep in mind you can't save to the partition you're backing up ;)

---

### Post by earther on 2007-08-15
I already own Acronis True Image 8 and have used it for years.  I have read on the Acronis forum that it will image an XP/Linux dual boot setup.

But when I pop in the disk, there are Xs on the ext3 partitions and I get this message:

> Some partitions contain errors and can be imaged only sector by sector.  It is recommended that you exit Acronis True Image and check the partitions with your systems disk checking tools.

1.  What might be causing this error message to pop up?

2.   Where do I find/run the Ubuntu disk/partition checking tools so can I check for errors manually?  (A disk check is run automatically every 25th boot and there have never been any problems.)

I've had the dual boot running for a few weeks now and getting pretty nervous because I don't have an image backup.

Thanks for your help.

---

### Post by bryanlking on 2007-08-15
I know there are several excellent choices but my favorite is Clonezilla: 

[COLOR="Blue"][http://sourceforge.net/projects/clonezilla/]("http://sourceforge.net/projects/clonezilla/")[/COLOR]

"Clonezilla is a partition or disk clone software similar to Ghost. It saves and restores only used blocks in hard drive. By using clonezilla, you can clone a 5 GB system to 40 clients in about 10 minutes."

When it boots, you simply answer a few questions and let 'er rip!  Couldn't be easier.

---

### Post by Tony3286 on 2007-08-25
Could you tell me which version of Acronis you have used? I also have a dual boot - Ubuntu and Windows XP. I recently purchased Acronis 9 and wonder if that will allow an image of Ubuntu to be installed on my WD Elements USB external hard drive. 
Also does Acronis need to be installed in Windows or can I use it from the CD - no manual came with it

---

### Post by Rick Z on 2007-09-06
Is there a good documentation for Clonezilla?  I know using that part-image has to boot up with the sysresccd.  Is this the same way with Glonezilla?

---

### Post by artinla on 2007-09-07
Why not go the easy route and try mondo rescue?  It can clone an entire disk without needing to reboot, and can clone to a bootable CD/DVD.  I use Acronis True Image usually, but mondo works well in Ubuntu.

They offer excellent documentation as well.  

[http://www.mondorescue.org](http://www.mondorescue.org)

---

### Post by earther on 2007-09-07
> **Tony3286 said:**
> Could you tell me which version of Acronis you have used? I also have a dual boot - Ubuntu and Windows XP. I recently purchased Acronis 9 and wonder if that will allow an image of Ubuntu to be installed on my WD Elements USB external hard drive. 
Also does Acronis need to be installed in Windows or can I use it from the CD - no manual came with it
I am still using Acronis TI 8 - I finally got it to recognize the ext3 partitions.  It created an image successfully from the boot CD (I have never created an image from within Windows) to an internal backup drive.  I have never tried to write directly to an external drive (internal is faster) but It couldn't be that hard.

The latest version allows exploration of ext3 partitions and the ability to clone a image to a machine with different hardware.

DISCLAIMER:  Although Acronis created the image of the dual boot setup, I have not tried restoring it.  Previously, I have successfully restored an image of XP (before the dual boot) on several occasions.

---

### Post by noynac on 2007-09-07
> **Tony3286 said:**
> Could you tell me which version of Acronis you have used? I also have a dual boot - Ubuntu and Windows XP. I recently purchased Acronis 9 and wonder if that will allow an image of Ubuntu to be installed on my WD Elements USB external hard drive. 
Also does Acronis need to be installed in Windows or can I use it from the CD - no manual came with it

A little late, but I just noticed this thread. I dual-boot WinXP and Feisty and use TrueImage 10 Home to backup (image) my hard drive. I normally do this by running TrueImage within WinXP, but I have also done it from the CD and it works fine. I almost always configure TrueImage to save the backup image on an external hard drive and have never had a problem.

As an aside, TrueImage 10 (which has been out for some time) has some nice enhancements and the upgrade version can be downloaded for only $20.00. This is money well spent.

BTW, I have restored my WinXP partition, my Ubuntu partition, and all of the partitions on my hard drive on numerous occasions and have never had a problem. I've heard that TrueImage can have problems with some raid or other unusual configurations, but for a standard setup it's very reliable.

---

### Post by earther on 2007-09-07
Only $20.00?  I just might go do that.  I'm very glad to hear you have had such good success with dual boot imaging.

---

### Post by Mia_tech on 2008-02-05
question when you use any of this tools, to restore your image to multiple workstation, in case of windows, does it change the SID when restoring the image?

---

### Post by heatblazer on 2008-02-07
It`s not a bad idea. Can you do an exact image of the OS? I want to make an image of the XP and boot it via the grub manager from my ubuntu.

---

