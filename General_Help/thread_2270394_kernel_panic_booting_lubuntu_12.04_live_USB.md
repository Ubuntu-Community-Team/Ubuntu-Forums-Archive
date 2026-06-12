---
title: "kernel panic booting lubuntu 12.04 live USB"
date: 2015-03-22
forum: General Help
---

### Post by thatguymark on 2015-03-22
I thought it was a BIO update but I've tried three versions (MSI P35 Neo2 FR) and I tried one other live USB disk, as well as another video card... Any ideas? Sorry about the image it's a lot to type.

[IMG]http://s30.postimg.org/54i65kzr5/kernelpanic.jpg[/IMG]

---

### Post by sudodus on 2015-03-22
Please specify more about your computer

- Brand name and model (you specified the motherboard, did you build the computer)?
- CPU
- RAM (size)
- graphics chips/cards (that you tried)
- wifi chip/card/dongle

It will make it easier to give good advice.

Also, please describe in detail, how you try to boot the computer and what happens.

Did you check the md5sum (that the download was good)?

How did you copy/clone/flash the iso to the pendrive (which tool did you use)?

-0-

You should realize that Lubuntu 12.04 is a bad choice, because it passed end of life long ago (so there are no security updates). If you want a light-weight system based on Ubuntu 12.04 LTS, you can try Bento, Bodhi or LXLE, which promise support until April 2017.

You can also try Lubuntu or Xubuntu 14.04.2 LTS, which are also supported until April 2017, and have a newer kernel and drivers.

If still no luck, please try another linux distro, that is made to work well with old and middle-aged hardware:

Knoppix, Wary Puppy, TahrPup, Tiny Core.

---

### Post by thatguymark on 2015-03-23
Thanks. Yes, I am building this machine. I’m testing a used motherboard. Right now it only has a single stick of 2gb DDR2 ram.  
 

 CPU is a Core2 Duo E7200
 

 Cards: (It’s actually a Radeon Mobility 5430)
 [http://us.msi.com/support/vga/R4350MD512HD3.html](http://us.msi.com/support/vga/R4350MD512HD3.html)
 

 Also tried ASUS EN8400GS
 

 There is no WIFI card.
 

 MISC: Reset switch just shuts the system down rather than reboot.
 

 Regarding the boot process, I simply insert the stick in one of the ports in the back and the system defaults to it as I have no other storage connected to this machine at this time, and I choose the option ‘try without making changes to your computer.’
 

 Regarding the Lubuntu live USB stick: It does boot on other machines and I had tried another, I believe that was Xubuntu going by the graphic and color on the bottom but I am not 100% sure. I am sure I checked the MD5SUM when I first downloaded it as I always do, and I've used this stick several times. I didn’t have the intention of using either as the main OS, I was trying to test it and figured if I got as far as the desktop I’m in pretty good shape.

---

### Post by thatguymark on 2015-03-23
Just as a side note for reference info only, I certainly do not expect anyone to support Windows but booting to Win 7 on USB I get a blue screen with system_service_exception, fbwf.sys ....

---

### Post by thatguymark on 2015-03-23
Upon further testing I discovered Memtest will immediately throw out a bunch of errors highlighted in red, but the same stick of memory in another machine does not do this. I had to manually set the memory latency etc. and I may want to use another module. In any case it does appear to be a hardware issue so I guess it is no longer relevant to the Ubuntu Forum. Thanks for your interest though.

---

