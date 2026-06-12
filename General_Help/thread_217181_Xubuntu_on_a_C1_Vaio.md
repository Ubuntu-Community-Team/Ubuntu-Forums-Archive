---
title: "Xubuntu on a C1 Vaio"
date: 2006-07-16
forum: General Help
---

### Post by Shafiq on 2006-07-16
Hi there.
I've been at this all day and I've kinda given up looking for the information myself, so I decided to turn to the community for help. :) 

So, here's the situation: My mum has a Sony Vaio C1XN laptop, you know the really small Sony laptops that they stopped selling about 3 or 4 years ago? Anyway, since MS has stopped support for Win98, I want to move her over to linux, but specifically Ubuntu, as it's nice and easy to use, which is good for her.
Anyway, for most of today I have been trying to get Ubuntu installed on the computer, but it never seems to work out.
The furthest I have got with it is to the point where the netboot version that I downloaded told me that there were no network devices installed (this is somewhat true as there is a Wireless network card plugged into the PCMCIA slot).

So, here's what I've tried so far:
I have used Loadlin and GrubForDOS to get the netboot version of Ubuntu running, and have got as far as stated above.
I have tried loading DSL onto a USB drive, but can not get it to boot from it.

I don't have a CD drive for the laptop, but I do have a floppy drive.
I have not created any partitions yet, although that'll be easy as there are already two partitions on the disk, so one can be destroyed and formatted accordingly.

Please, please, please can someone out there give me some hints as to how to do this!
Ideally I'd like to get xubuntu onto there as the GPU isn't very powerful, and I've heard that the XFce4 desktop is very light on graphical resources.
The way I see getting this done is maybe to get an image of the disc onto the computer, then boot the computer into something that can load the disc as a virtual drive, and can then install linux to the PC, and from there I can set up the wireless network and download all the necessary updates.
Some task, huh!

Any help is muchly appeciated.

Thanks in advance,
 Shafiq.

---

### Post by timhan on 2006-07-26
Hiya!
I also have a little PCG-C1XN, and I've just finished installing Ubuntu. I think it's great (both my laptop and Ubunto ;-)

Anyway, thought you might like to know how I did it. Firstly I got the book Beginning Ubuntu Linux (well I am a newbie to all of this) and the book comes with a DVD and I installed from that. The install went fine, there wasn't really anything for me to do at all, even the partitioning was done automatically! And when the install was finished it went straight into Gnome, cool!

Might sound a bit crap, but I would suggest getting a DVD Rom for your mums c1xn, as if the dvd install worked for me I guess it should work for her machine to? (By the way the book is really good aimed at beginners)

Oh one thing though, I have had problems with the screen, when gnome starts only half the screen is displayed and the screen flickers every 5 seconds. However I found this on a german website ([http://lists.suse.com/archive/suse-linux/2001-Dec/1840.html](http://lists.suse.com/archive/suse-linux/2001-Dec/1840.html)) and I'm going to try and change the refresh and resolution info in the xorg.conf file. There is a howto here: [http://ubuntuforums.org/showpost.php?p=129379&postcount=21](http://ubuntuforums.org/showpost.php?p=129379&postcount=21)

I'll let you know how I get on...

Good luck, Tim.

---

### Post by Shafiq on 2006-07-27
Hi Tim,

Although I appreciate the help, I do want to try and not purchase any unnecessary hardware for the computer. I am a poor student, so my money is best spend elsewhere!

I have come across some boot disks that allow me to boot Debian Sarge as a network installation, but the problem I am now facing is that the Wireless Network Card I have is not in the list of Network device drivers on the boot disks.
I found out that, in fact, Linux doesn't like the Wireless Network card that I have (a Netgear MA521), but have learnt that it's possible to use NDisWrapper to use Windows Drivers and create Linux drivers from them.

Anyway, does anyone know how to make a disk that holds the drivers that the boot disk is able to find? So that I can boot using the first boot disk, then use my own drivers to continue on from that point.

Any help here would be great!
Thanks,
 Shafiq.

---

### Post by timhan on 2006-07-31
Hiya all!

Just thought that I would let anyone know that is also trying to set up Linux on the PCG-C1XN that I gave up trying to get Ubuntu to work with my laptop 8-( It's a great shame as I really wanted to use Ubuntu (or perhaps Xubuntu) but I guess it was never to be!

Anyway, I did succeed in getting it to work eventually with Suse! Use the german link above to edit the xorg.conf file after the install is finished. You have to play around with the setting a bit in Sax2, but it doesn't take that long to get it working. Initally in Sax you have to set the monitor and resolution to 640x480. Then start Sax2 once you have loged in for the first time and edit the xorg.conf file with vi for example.

Anyway, good luck! I'm off to see if I can install Xfce instead as Gnome is just too slow on Suse...

Bye! T.

---

### Post by Shafiq on 2007-04-24
Good news!
I finally got Xubuntu running on my C1 vaio, it turns out that once the UI had loaded, I couldn't seen anything because it was using a 1024x768 resolution, and the screen is only 1024x480. I found that if I added the line 'Option overrideValidateMode' to the xorg.conf file, it would disregard checking the non-standard mode that I had written in there, and use it anyway.

For the life of me I couldn't figure out why, after adding the 1024x480 resolution to the xorg.conf file that it wasn't working, but it was all because of the overrideVaildateMode option.

Now I just have to find some more RAM to make it run at a decent speed!

 Shafiq.

---

