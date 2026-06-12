---
title: "Q regarding live CD creation for 16.04"
date: 2016-06-17
forum: General Help
---

### Post by Azkiwi on 2016-06-17
Hi all,
I'm technically so-so.   I have an old 64bit vista system, and 2 old XP systems. I'm interested in putting Ubuntu 16.04 LTS on them. I have d/l'd the .iso images  for the 32 bit and the 64bit  systems. I selected 'desktop' for both images.  I have tried burning the iso image several times for both, they burn correctly,  but I cannot make them bootable.  I've done so much looking and reading on the UBuntu site that I've now confused myself rather well.  

I have used an .iso viewer to look at each and, from what I could find on the site,  - an image that showed a number of files such as autorun, start,  etc,  these images I d/l'd don't seem to be complete for a (windows??) boot as they aren't in my .iso's.  I have followed a number of the instructions for burning a bootable dvd, but it seems the .iso 's I d/l'd do not contain this info.  

As I mentioned, I'm now totally confused and at a dead-end.  I'd like to get bootable (after .iso burn) images for both the 32 and 64 bit  packages, but I just don't know how or where to find them.

Will someone please help out an old f*rt trying so hard.

Thanks

Ken

---

### Post by Bucky Ball on 2016-06-17
How exactly are you burning this? Little point comparing with Windows. You need to burn a disk image. Are you creating a data disk from the iso instead?

Have you had [a read of this]("https://help.ubuntu.com/community/BootFromCD")? If the problem isn't with how you burnt the DVD then it is possibly with how you are trying to boot it. Considering these machines are running Vista and XP I'd presume they are fairly old and would not be using UEFI to boot. Check.

Further to the presumption they are old machines, are you sure they are going to cope with a full blown, Ubuntu 16.04 LTS install? How much RAM do they have and what processor? 

You may be better served by a lighter flavour, Xubuntu or Lubuntu perhaps. When you get Ubuntu booting from the DVD I suggest you choose the 'Try Ubuntu' option and run a desktop from the DVD and see how you go. If it is too sluggish, try one of the others (although you will get a slight speed improvement when the OS is installed on disk).

---

### Post by Azkiwi on 2016-06-17
Bucky Ball - thank you.
Yes, I'm burning the dvd with the ISO correctly, I can scan the dvd and see the folders shown in it and I can access the folders.

I will now dig thru the links (and sub links) you provided to ensure I understand where /what / how I'm doing things -- 

appreciate your help

Ken

---

### Post by Azkiwi on 2016-06-17
Me again -- The xp systems are hp /athlon, circa '03 - '06, the vista is  acer aspire circa '07 - so I doubt that have the UEFI  - just checked - nope, it's the older version bios in all 3...

In the link you sent - [a read of this]("https://help.ubuntu.com/community/BootFromCD")   -  my file display looks very much like that in Diag 1, except it only has the folders and m5sum file, none of the others.. - Hence my wondering about the contents of the .iso.

The hp / xp systems are probably going to be underpowered, 1GB ram, old processor, the Acer / Vista has a turion 64bit, with 3gb ram - so it might take it.. Figuring that out will be part of my summer fun..

Ken

---

### Post by grahammechanical on 2016-06-17
Are you trying to run these burned ISO images in Windows? We do not do that. Have you gone into the BIOS and changed the boot priority so that the motherboard looks to the DVD drive for an OS to load before it looks to the hard drive for an OS?

The autorun.ini file is for automatically loading a CD when Windows is loaded. We put the CD in the drive. Windows accesses the CD drive and runs the autorun.ini file and loads a Windows exe file off of the CD.

This is not how we install Ubuntu. That is why the Ubuntu ISO image does not have an autorun.ini file.

Regards

---

### Post by coldraven on 2016-06-17
All versions can be found here, after selecting one scroll down the page for md5sums and download options. I usually use the torrent version, it's quick and also automatically verified.
[http://releases.ubuntu.com/](http://releases.ubuntu.com/)

---

### Post by Azkiwi on 2016-06-17
Grahammechanical -- thanks. I poked around in the bios for the acer /turion 64 system. Changed boot order and a couple of other little items.... put the 64bit dvd in the drive ...... And it booted!!! Slowly of course into 'try it' mode, but it did come up! Progress!  and Vista still booted up afterwards...

Coldraven -- thanks -- I saw that, but know so little about torrent-ing, I opted for the down load method.

New info:   I found an old Ubuntu dvd, 2008, for rlse 8.04 and it sorta worked in the old hp system. It started, but very slowly, and I'm still waiting for the 'try-it' to finish setting up (bout 30 min now) but I'm beginning to think these older xp systems are so way back that about all they're good for is xp, or to occupy space on a garage shelf.

Ken

---

### Post by Impavidus on 2016-06-17
> **Azkiwi said:**
> 
In the link you sent - [a read of this]("https://help.ubuntu.com/community/BootFromCD")   -  my file display looks very much like that in Diag 1, except it only has the folders and m5sum file, none of the others.. - Hence my wondering about the contents of the .iso.
I think that screenshot comes from an older release of Ubuntu.

The older computers may be underpowered for Ubuntu, but may be able to run one of its lighter flavours – Xubuntu, Ubuntu Mate or Lubuntu. Lubuntu is the lightest. Those systems are equally good as Ubuntu and under the hood mostly identical, as they use the same software repositories, but use a lighter (less shiny) desktop environment and lighter default applications. I've got a computer from circa 2005, 1 GiB ram, still happily running Xubuntu 16.04. Going for a current release of a lighter flavour is much better than trying an old release.

30 minutes to boot a live dvd is rather long. Are you sure the dvd drive isn't dusty? And writable dvds (as opposed to factory-stamped ones) deteriorate slowly, so if that disk is 8 years old, it may be broken.

---

### Post by Bucky Ball on 2016-06-18
That you can open the DVD in Windows and see the files means nothing. You can do that with a data disk and sounds like you burnt one. You need to burn a bootable disk image.

---

### Post by coldraven on 2016-06-18
> the Acer / Vista has a turion 64bit, with 3gb ram - so it might take i I'm writing this on a HP Turion 64 bit with 4GB, it runs very well

> I saw that, but know so little about torrent-ing, I opted for the down load method. The torrent seed files are small ~60kb. In Ubuntu when downloading it you are asked "Do you want to open it in Transmission?" Just click "Yes" and it's automatic after that. Transmission is Ubuntu's default torrent client. Downloading with this method takes the strain off the servers because you are actually getting it from maybe 50 other peoples computers.

In whatever disc burning software that you are using you must select "Burn Disc Image" to make a bootable disc.

---

### Post by Azkiwi on 2016-06-18
Coldraven & Buckyball -- thanks for the info and feedback.  

No, I burnt them as .iso, not data, but I've now reached the point of 5-6 DVD's, so it's back to square one. Putting them asside and going to use IsoBurner to create new ones... Blanks are cheap, and it'll remove all doubt about the state / quality / burn of the existing ones.

This project is going on a week or so slow down - schools out and the Grandkids are mine all next week.  Will work with it on a t/a basis and get back to it a couple of weeks from now.

Appreciate your patience with an old noob, and your help

Ken

---

### Post by RobGoss on 2016-06-18
> **Azkiwi said:**
> Grahammechanical -- thanks. I poked around in the bios for the acer /turion 64 system. Changed boot order and a couple of other little items.... put the 64bit dvd in the drive ...... And it booted!!! Slowly of course into 'try it' mode, but it did come up! Progress!  and Vista still booted up afterwards...

Coldraven -- thanks -- I saw that, but know so little about torrent-ing, I opted for the down load method.

New info:   I found an old Ubuntu dvd, 2008, for rlse 8.04 and it sorta worked in the old hp system. It started, but very slowly, and I'm still waiting for the 'try-it' to finish setting up (bout 30 min now) but I'm beginning to think these older xp systems are so way back that about all they're good for is xp, or to occupy space on a garage shelf.

Ken

Hello Azkiwi, Ubuntu can run on those older XP machines but they may not run as good as the newer machines and of course this all depends on the system specs. Some of the older desktops should be able to boot from a **USB **drive and you should be able to install Ubuntu that way. I recommend **USB **because I see more people have success using them including my self. If you're using a **DVD** it should be at least **4-GB** not to say you will need this much disk space but some **DVD** are only **700-MB **and that won't be enough to create a live session of Ubuntu

[Pendrive]("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/") is a great **USB **installer and works well, once you download the [ISO]("http://www.ubuntu.com/download") file you can use Pendrive to install it on your USB drive

On the older machines most of them that have Windows XP are **32-bits** so you would need a **32-bit** ISO file to make things work. There are also lighter versions of Ubuntu that will work better on older computers because they require less resources if things don't work out with Ubuntu 16.04

Here's just two that come to mind, [Lubuntu ]("http://lubuntu.net/") and [Kubuntu]("http://kubuntu.org/")

In any case I wish you all the best with your installation

---

### Post by Azkiwi on 2016-06-19
Status update:
- was successful in booting 16.04/64bit DVD to 'desktop' on both the Acer 64bit and the Asus 64 bit.  I Also created a bootable USB and was success again successful on both.
- Reburned the .iso for 16.04 / 32bit and also created a bootable USB.  The 32bit dvd booted to 'desktop' on both the afore mentioned systems. I also tried on 2 of my 3 netbooks - no dvd - with the 32 bit 16.04 - and both booted to desktop' altho' considerably slower than the 'bigger' notebooks.
- Created a bootable USB for Lubuntu 16.04/32bit and tried all mentioned systems again.  All booted. The netbooks were considerably slower to boot up, but they are a bit underpowered - Atom processor, 1GB memory.
- Created a bootable dvd for Lubuntu  to try on the old hp4315 machines.  Would start okay, and give the welcome screen, but would not proceed much further.  After 6 hours waiting I called it quits.  These 2 machines will not boot from a USB.  They are now obsolete, and back on the garage shelf.

I'm very grateful for the responses and help and direction I've received as I've worked my was thru this process.  Would never have got this far with out it.   This old man says THANK YOU and is looking forward to a summer of playing, learning and experimenting with everything.

Ken

---

