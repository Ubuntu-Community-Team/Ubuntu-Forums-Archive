---
title: "installing with out a dvd drive or usb stick?"
date: 2013-07-16
forum: General Help
---

### Post by k1l14 on 2013-07-16
hello everyone.

i wanted to install Linux for awhile now but i have a problem, my DVD drive isn't writable and i don't think this dino is capable of booting off a thumb drive. i turned usb emulation on and the usb controller is also on in the bios. so i dunno wtf is going on, but i can't seem to boot off a thumb drive.

i cleared a 100gig drive off for the install, i can install the live cd? (i think it is, doesn't look like a full install) and when i reboot i get the option to boot Linux, but when go to boot Linux, i get a windows boot manager error and it's pointing to a file in linux on the HD. ;0)

is there a way to install Linux in full inside of windows 7, to a separate drive? getting tired of windows and i wanna check linux out...

sorry if im confusing ppl here, i dont know a lot about Linux...

---

### Post by ibjsb4 on 2013-07-16
Im not following your post very well, but ..

You say you can't burn a DVD.  Can you burn a CD?  Ubuntu 12.04 will fit on a CD and is supported till 2017.

[http://releases.ubuntu.com/precise/](http://releases.ubuntu.com/precise/)

You did not mention what kind of computer you have.  If its low on ram or slow singler core processor, you may not have the specs to run 12.04.  In which case you could go with Xubuntu,  its built to run better/faster on old systems.

[http://ftp.dei.uc.pt/pub/linux/xubuntu/releases/12.04/release/](http://ftp.dei.uc.pt/pub/linux/xubuntu/releases/12.04/release/)

---

### Post by k1l14 on 2013-07-16
sorry about that...

yes i can burn a cd and it reads dvds, but it doesn't write em. ;0(

i have a little bit over a gig in memory, the video card is a geforce3 ti 200 with 64 mb's in memory and the processor is a Pentium 4 2.26ghz... for storage i have, (1) 100gb, (1) 500gb, (1) 80gb and an external 2TB HD.
forgot: its a dell optiplex gx260

im running windows 7 now, had to tweak stuff, but its running good, even running at 1280x768...

if i can run that version, is there a way to update to the newest version, like a live update?

thanks for replying. ;0)

---

### Post by GerryB on 2013-07-17
I have Ubuntu 12.04 running on a Pentium III, so you're good to go. Run the live CD and you'll see how the system behaves. Good luck.

---

### Post by newb85 on 2013-07-17
> **k1l14 said:**
> if i can run that version, is there a way to update to the newest version, like a live update?

Certainly.  The Update Manager/Software Updater (it changed names between releases) gives you the option to upgrade to the next release.  This kind of upgrade can sometimes be problematic if you've done a lot of customization with your system.  But if you're doing it on a fresh install, it should work without a hitch.

I think you'll have to go from 12.04 to 12.10 and then to 13.04.  Before each upgrade, make sure you've installed all updates available to the current release.

---

### Post by k1l14 on 2013-07-17
thanks for all the help.

i got it installed and running, just trying to get the hang of it atm. ;0)

is there a way to get the drivers for the geforce3 ti 200, im stuck on a small rez.... 0_0

---

### Post by GerryB on 2013-07-18
Check for proprietary drivers in Ubuntu Software Center. This might also help: [http://www.howopensource.com/2012/10/install-nvidia-geforce-driver-in-ubuntu-12-10-12-04-using-ppa/](http://www.howopensource.com/2012/10/install-nvidia-geforce-driver-in-ubuntu-12-10-12-04-using-ppa/)
Good luck!

---

### Post by Boab1993 on 2013-07-18
It sounds like you want a dual boot system?, one that you can choose between either booting windows or linux on your computers start-up?
If so i advise you first install 'PLOP', [http://www.plop.at/en/bootmanager/index.html](http://www.plop.at/en/bootmanager/index.html), it is a boot manager that simplifies finding and accessing paritions on HDD's, its just very user friendly.

As for installing linux without using a usb or cd, there are ways around this, you can actually install the live cd onto part of hard drive and boot it from there.
I would recommend using a software called 'Gparted',[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/), it allows you to manage and format all existing storage devices on your computer
However, if your entire hard drive is still a windows partition it becomes slightly more difficult to change things. There are youtube tutorials on how to do this but take your time and be careful, you could end up with no operating system on your computer.

As far as versions of linux go, any ubuntu based OS is user friendly and fairly low usage and run fine on older systems.
Two versions called lubuntu and xubuntu are built specifically for older systems with less RAM and slower processors, none of them are particularly RAM hungry, so either would run seemlessly on your system. Personally with yours id choose xubuntu, it retains most of the functionality of ubuntu. Lubuntu is probably quicker but lacks some features of the standard lubuntu, they can be added but in more roundabout ways, and as your just starting with linux, i think you would find it easier either with xubuntu or standard ubuntu.

If you are feeling adventurous there are more linux systems out there like debian and fedora, i know little about them but im sure you can find some help about them on this site, or their own.

Hope this helps

---

### Post by VMC on 2013-07-18
> **k1l14 said:**
> sorry about that...

yes i can burn a cd and it reads dvds, but it doesn't write em. ;0(

i have a little bit over a gig in memory, the video card is a geforce3 ti 200 with 64 mb's in memory and the processor is a Pentium 4 2.26ghz... for storage i have, (1) 100gb, (1) 500gb, (1) 80gb and an external 2TB HD.
forgot: its a dell optiplex gx260

im running windows 7 now, had to tweak stuff, but its running good, even running at 1280x768...

if i can run that version, is there a way to update to the newest version, like a live update?

thanks for replying. ;0)
I had one of those old Dell Optiplex computers. Yes, you can boot  off the USB. You might need to upgrade the BIOS to A06. In either case read these [instructions]("http://www.pchelpforum.com/xf/threads/optiplex-gx260.61442/") first - Especially [Post#3]("http://www.pchelpforum.com/xf/threads/optiplex-gx260.61442/#post-340517").

---

### Post by k1l14 on 2013-07-18
at Boab1993, my whole os hd was formatted and had windows 7, i couldn't even shrink the portion. i turned off system restore and removed the page file, still a no go. so i tried to put two portions on the 149 gb hd i cleared and that was what i was getting at in the first post, i keept getting a windows bootmanager error. i ended up grabbing 12.04 and burning a cd and im running it now. tried to update it this morning to the next version and i got a blank screen, so ill stick with this version for now. ;0)

i tried xubuntu and yes it is very fast, but i didn't like the looks to much, to old school for my tastes. 12.04 seems to be running great, might look in to tweaking it alil once i get used to this, if it's possiable. so fare it's blowing windows away, usb file transfer is 3mb's faster and the wifi im grabbing seems to be getting alil higher speeds. i also love how my phone (samsung galaxy express with android 4.1.2) just seems to hook right up with no problems. my only thing is this resolution problem. i seen some commands on a few threads around here, gonna give it a go later tonight.

at gerryb, i couldn't find my card in the list of supported devices, but thanks for the link. :0)
it will start out on the ubuntu screen at 640x480 and i didn't think this card supported 480p. it will support 1280x768 but not 1280x720.. im gonna give them commands a g, i just have to find the specs for my tv.

at VMC: yup, my bios is at A00 i think. my wireless keyboard works but i couldn't get the thumb drive to work. ty for the link, ill give that a go to later on.

---

