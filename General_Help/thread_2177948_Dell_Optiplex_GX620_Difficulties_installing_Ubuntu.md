---
title: "Dell Optiplex GX620: Difficulties installing Ubuntu"
date: 2013-10-01
forum: General Help
---

### Post by niel3 on 2013-10-01
Hi

After a long time wanting to install Linux on my desktop I almost never used anymore (it was getting way to slow with Windows xp) I finally tried. 

I burned the installation on a dvd,  restarted my computer, pressed F12 and chose to boot from dvd. After*that I get a black window with a little white figure next to an object and a few seconds later the ubuntu loading screen appears. 

The dots beneath 'ubuntu' keep changing from white to red,  indicating that it is loading. But it stays at this screen forever. (I tried waiting for 2 hours already). I also tried it over 3 times. 

When I press esc I get a big list with errors. It gives a lot of 'scripts/casper-bottom/25adduser: line 70: db_unregister: not found' and other words in the place of unregister like get, set, fget and fset. 

I also see 'nstall: invalid user' ubuntu '', 'm: can't stat '/root/usr/share/kde4/services/...


I can post a pic if you like,  because I don't know anything of this computer language. 


Thank you

---

### Post by mörgæs on 2013-10-01
Hi, welcome to the fora.

Please begin with a complete hardware description.

---

### Post by niel3 on 2013-10-01
Ok it is a dell desktop computer optiplex GX620 with:

Processor type: intel pentium 4 CPU 3.20 GHz
Processor clock speed: 3.20 GHz
Processor bus speed: 800 MHz
Processor L2 Cache: 2MB

installed memory: 1.0 gb
memory speed: 533 MHz
memory technology: DDR2 SDRAM

I has 2 gb of ram and is running windows xp. I also changed the video card a long time ago to something better. But I haven't used the desktop a lot the last 3 years. (thats why it so outdated hardware ;) )

Do you need any other information? (this is what I found in the boot screen)





Here is what I get when I press esc at the loading screen:

[IMG]http://i41.tinypic.com/14azlee.jpg[/IMG]




Thanks for the fast response :)

---

### Post by mörgæs on 2013-10-01
The GX620 runs well with Buntu, but I would recommend [Xubuntu]("http://xubuntu.org/getxubuntu/") rather than Ubuntu.

Generally it's safer to install from USB than CD/DVD.

---

### Post by 3rdalbum on 2013-10-01
Ubuntu 12.04 is fine for that computer.

The Input/Output Error, along with the other error messages that make little sense, leads me to think it may be a badly-burnt DVD, a corrupted download, or a faulty DVD drive.

Check the md5 sum of the ISO file you downloaded. If it matches the md5 file on the Ubuntu website, then the ISO is fine. Try burning it again, this time at a slower speed, and onto a decent DVD not a cheapo bargain basement disc.

If that fails and you still get similar error messages, and you also have problems if you try it on other computers, try making a LiveUSB from the ISO file, instead of a live DVD.

If nothing works, then you may have bad RAM in that computer.

---

### Post by niel3 on 2013-10-01
This is the only type of DVD I have (DVD format plus platinum DVD + R 4.7 gb, 8x speed). So it is possible to just put the ISO on an USB stick and install it through that? I'll look up a tutorial. 

About the DVD, this is a screen shot what I see when I open it. 

[IMG]http://i41.tinypic.com/15fiv5x.jpg[/IMG]


So my computer can run ubuntu, but will xbuntu run better? (First time I hear about xbuntu). The only thing I know is that Linux is an OS and Ubuntu a 'version' of it like android is an OS on my smartphone (I heard it also linux based). But there stops my knowledge about this subjects :p Although it really interests me.

---

### Post by mörgæs on 2013-10-01
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

The Buntu family has several desktop environments. Ubuntu and Kubuntu are heavy, Xubuntu is medium and Lubuntu is light. You can see demos on Youtube before deciding.

---

### Post by Impavidus on 2013-10-01
Goeiemiddag,

If you want to put the .iso on a usb stick, use these instructions: [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
It's not about copying the .iso file, it's about copying the file system inside the .iso.

There are several different Linux distributions, Ubuntu being one of them. There are several Ubuntu flavours, like Ubuntu or Xubuntu.

And the missing end-of-line characters in Kladblok (in your screenshot) are caused by the difference in end-of-line convention as used by Windows and Linux. More advanced editors will display the file more readable. Not sure whether the md5sum of the .iso itself is included too. Actually, I'm quite sure it's not, as the whole idea of hashes makes it quite impossible to include the hash of a file into the file itself. You can find the md5sum on the site where you downloaded the .iso.

---

### Post by poettone on 2013-10-01
I've never used or had any reason to install the i386 version of any Ubuntu version but I would try the x686 version not the i386 version on your machine. If they are backward compatible (something I've never attempted) then I will have learned something. 

Hope that helps.

---

### Post by niel3 on 2013-10-01
Thank you for all the explanations, I couldn't have figured it out myself. I'm now creating the bootable USB.

---

### Post by niel3 on 2013-10-01
I managed to install ubuntu :) Im going to test it out, but it seems to work smooth. Now I can learn how it works.

---

### Post by mörgæs on 2013-10-02
Good, then please mark the thread 'solved' using Thread Tools.

---

