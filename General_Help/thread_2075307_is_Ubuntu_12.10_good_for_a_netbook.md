---
title: "is Ubuntu 12.10 good for a netbook"
date: 2012-10-23
forum: General Help
---

### Post by matt129345 on 2012-10-23
i tried to install natty narwhal 11.4 on a usb, but when i plug it in to my netbook it just gives me a bunch of folders...no setup file.

but when i tried Ubuntu 10.10 (Maverick Meerkat), it worked fine.

---

### Post by linuxvstheworld on 2012-10-23
Usually 12.10 and other versions between LTS releases are mostly used to experiment with features, if you plan on updating Ubuntu that much on your netbook, go 12.04 LTS.

---

### Post by matt129345 on 2012-10-23
> **linuxvstheworld said:**
> Usually 12.10 and other versions between LTS releases are mostly used to experiment with features, if you plan on updating Ubuntu that much on your netbook, go 12.04 LTS.

Will I have any issues if I try 12.04 LTS on my netbook?  I mean, is it strictly for desktops?  Because I know there are netbook editions.

thanks for responding so quickly.

like i said, i tried natty narwhal (11.04), i got it installed on the USB no problem, but when i plug it into my windows 7 netbook, I click on my computer, and it just shows a bunch of folders and i don't know what to do next.

if i wanted 12.04 on my netbook for example, i go to this page

[http://releases.ubuntu.com/precise/](http://releases.ubuntu.com/precise/)

which download would i select to put it on a USB then on my netbook?

---

### Post by linuxvstheworld on 2012-10-23
> **matt129345 said:**
> Will I have any issues if I try 12.04 LTS on my netbook?  I mean, is it strictly for desktops?  Because I know there are netbook editions.

thanks for responding so quickly.

like i said, i tried natty narwhal (11.04), i got it installed on the USB no problem, but when i plug it into my windows 7 netbook, I click on my computer, and it just shows a bunch of folders and i don't know what to do next.

if i wanted 12.04 on my netbook for example, i go to this page

[http://releases.ubuntu.com/precise/](http://releases.ubuntu.com/precise/)

which download would i select to put it on a USB then on my netbook?

What are your specs for the netbook? I have a Dell Inspiron 6400 that ran 12.04 LTS just fine.

---

### Post by matt129345 on 2012-10-23
> **linuxvstheworld said:**
> What are your specs for the netbook? I have a Dell Inspiron 6400 that ran 12.04 LTS just fine.

it's an ASUS 1018p

2gb ram
intel Atom n450 @1.66ghz 
32bit

---

### Post by matt129345 on 2012-10-23
when I haev 10.10 downloaded onto my USB stick, i plug it into my netbook (windows7) then in my computer, it says devices with removable storage and shows the WUbi icon saying "install ubuntu Netbook (D:)

I click that, and it just says a bunch of folders:
.disk
boot
casper
dists
install

etc.

I try all of them, but they're just filled with text documents?


am i supposed to restart the computer with the usb in it?

---

### Post by MG&amp;TL on 2012-10-23
> **matt129345 said:**
> 
am i supposed to restart the computer with the usb in it?

Yes, that's one way of doing it. Note that this method will partition drives. Follow this guide here: [http://psychocats.net/ubuntu/installing]("http://psychocats.net/ubuntu/installing"), mentally replacing "CD" with "usb stick". :)

Post if you've got any problems.

Backup your stuff first.

---

### Post by sandyd on 2012-10-23
You will have to set your netbook to boot from a USB drive in order to boot Ubuntu. This netbook is a bit wonky, so you have to disable the Boot Booster from the BIOS settings. The ESC key raises the boot menu (during boot) so that you can choose to boot to USB. You have to start mashing the ESC key right after your turn your computer on.

Also, I would recommend going with Ubuntu 12.04 LTS for now, then upgrading to 12.10 later on. New releases generally have a few bugs that get sorted out by the 12.10.1 release.

In addition: [http://www.linlap.com/wiki/asus+eee+pc+1018p](http://www.linlap.com/wiki/asus+eee+pc+1018p)

---

### Post by matt129345 on 2012-10-23
thanks for the guide, looks like that was exactly what i needed.

any opinions on 12.04 LTS vs. 11.04 (natty narwhal) for the netbook?

i am downloading both of them now, and ill check back if that guide works.

---

### Post by matt129345 on 2012-10-23
well, when i restart my netbook it never goes to the bios screen or gives me a key to press ie; escape, delete f# to boot from usb

is this because i am using windows 7 starter edition?  what gives?

edit: nevermind, solved that

---

### Post by GreatDanton on 2012-10-23
Go with 12.04, since 11.04 will be supported only until April 2013. Take a look here: [http://en.wikipedia.org/wiki/List_of_Ubuntu_releases](http://en.wikipedia.org/wiki/List_of_Ubuntu_releases)

---

### Post by matt129345 on 2012-10-23
well I got into the bios, but all I see is windows 7 and windows memory diagnostic.


im even using the left usb port like it says for this specific netbook

---

### Post by matt129345 on 2012-10-23
how do i disable boot booster?

i can access Windows Boot Manager no problem.

here it says I can choose Windows 7, specify an advanced option for this choice, or use Windows memory diagnostic.

Nothing Ubuntu here...what am I doing wrong?

edit: i disabled boot booster, lets try again

---

### Post by Paqman on 2012-10-23
> **matt129345 said:**
> 
any opinions on 12.04 LTS vs. 11.04 (natty narwhal) for the netbook?


I wouldn't use 11.04 on anything. Support for it ends this month, and after that you won't get security updates.

Go with 12.04, it's a Long Term Support version and has the Unity 2D interface that's good for netbooks. It's supported until 2017.

---

### Post by grusty on 2012-10-23
I have a netbook Lenovo S10-2. Everybody know that KDE use a lot of memory. But. Now KDE (Kubuntu) have a file called "kubuntu-low-fat-settings". this file turn off many services that take a lot of memory and most users don't use it.

Too, KDE have a desktop designed specially for tiny netbook screens. Is great and very beautiful. I don't know why is unknow it.

Look images of Kubuntu netbook plasma (or kde netbook plasma) at web and see what i talking about.

Then if you decide install it, at your first session, open Muon Software center and install kubuntu-low-fat-settings. And restart.

You will be a very beautiful, fast and efficient environment for netbook. The best desktop for netbooks.

At my desktop i don't use Ubuntu/Unity because is to slow (AMD sempron is my chip)

Good luck.

---

### Post by matt129345 on 2012-10-23
this is driving me insane.

I disabled boot booster, I made sure that removable device was set too 2nd position in the boot order.  saved changes.

restart the computer, go to the bios, and still...  my usb does not show up.  like that asus poster suggested, i am using the usb port on the left as the one's on the right don't work with OS for whatever reason.  i just don't get it.

---

### Post by matt129345 on 2012-10-23
do i need to Create a bootable USB-drive in Windows using something like UNetbootin?

---

### Post by Scott Baker on 2012-10-23
Howdy Matt. Welcome to the world of Ubuntu. A couple of things here. First, it sounds as if you have the correct files, but you missed a step. These files need to be converted into a "bootable" .iso file. It's been a VERY long time since I've done this through Windows, so if someone could please assist. Next, regarding choice of versions. 12.04 LTS is the latest long term version, providing support for 5 years. I have it installed on all of my machines, and it works fine. It's also still able to be put onto a CD (12.10 is too large for a CD, it has to be put onto a DVD, if you choose to go with disk). You could also try earlier releases if you choose (nothing earlier than 10.XX though). The very BEST thing about this operating system is that you don't have to commit to permanent installation of you don't want to. Good luck, hope this little bit helps.

(@ Matt, yes, Unetbootin to convert, 4 gig or better on your USB stick (for fewer headaches), Once again, good luck)

---

### Post by matt129345 on 2012-10-23
Okay, so how do I convert it to a bootable .iso file? 

:P

any takers?

---

### Post by GreatDanton on 2012-10-23
[How to make bootable usb on Windows]("http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows")
Take a look at this. You will have to place removable device to first place in boot order, otherwise you will not be able to boot from usb.

Regards.
[]("http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows")

---

### Post by matt129345 on 2012-10-23
i already set removable device to the first sequence and it still isn't working

about ready to give up, can't believe how much a pain in the butt this is

---

### Post by GreatDanton on 2012-10-23
Okay, let's start once again. Format USB, make bootable usb according to the link I gave you in my previous post. After that change boot order (so the removable device is on the first place) and save your settings and exit bios. Now you should be able to boot into Ubuntu.

---

### Post by linuxvstheworld on 2012-10-23
> **matt129345 said:**
> thanks for the guide, looks like that was exactly what i needed.

any opinions on 12.04 LTS vs. 11.04 (natty narwhal) for the netbook?

i am downloading both of them now, and ill check back if that guide works.

This'll help you decide: [http://askubuntu.com/questions/128542/11-10-vs-12-04-which-should-i-choose-for-stability](http://askubuntu.com/questions/128542/11-10-vs-12-04-which-should-i-choose-for-stability)

I assume you want more stability than anything right?

---

### Post by Linuxisfast on 2012-10-23
I am using Ubuntu 12.10 with my AMD powered ASUS 1015B, from the day I purchased this netbook, I couldn't get myself used to the Win7 starter it came with as I found it too slow. I installed 11.04 and then 11.10 and 12.04, all ran well, now I updated to 12.10 which runs equally well, just had to install linux-headers before installing ATI Catalyst. The only reason I upgraded from LTS was due to the fact that Ubuntu includes microcode updates for the AMD cpu which is not available in 12.04

---

### Post by rg4w on 2012-10-24
FWIW, my netbook is one of the oldest around, ASUS EeePC 901.  I recently updated it from 10.10 to 12.04 LTS, and it runs better than ever - seemingly faster, definitely more stable.

---

### Post by Linuxisfast on 2012-10-24
> **rg4w said:**
> FWIW, my netbook is one of the oldest around, ASUS EeePC 901.  I recently updated it from 10.10 to 12.04 LTS, and it runs better than ever - seemingly faster, definitely more stable.

Don't forget to add intel-microcide and microcode_ctl file as they would upgrade your CPU's microcode. In case you are using 12.10, only first file is needed, the loading is done by the kernel.

---

### Post by rg4w on 2012-10-24
> **Linuxisfast said:**
> Don't forget to add intel-microcide and microcode_ctl file as they would upgrade your CPU's microcode. In case you are using 12.10, only first file is needed, the loading is done by the kernel.
I've never done that. Should I?  How?

---

### Post by linuxvstheworld on 2012-10-25
> **matt129345 said:**
> do i need to Create a bootable USB-drive in Windows using something like UNetbootin?

Yep, ran into that problem when I first tried, if it's bootable, it'll surely work if you choose boot via USB in the boot menu.

---

### Post by jmckean on 2012-11-19
> **matt129345 said:**
> 
it's an ASUS 1018p

2gb ram
intel Atom n450 @1.66ghz 
32bit

I have exactly this machine and have been running 12.04 and 12.10 on it for a while. 12.04 was flawless. Much faster than Win7. 12.10 have been a bit troublesome getting the webcam to work.  

Sorry you are having trouble getting it on.  I did a full install with 12.04 -- no dual boot -- and an upgrade for 12.10.

---

