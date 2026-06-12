---
title: "Before I switch..."
date: 2007-10-12
forum: General Help
---

### Post by CoreOxide on 2007-10-12
Heya;

I am thinking about installing Ubuntu on my older PC (P4 2.8GHz, 512 DDR400, Radeon 9600Pro), just to play arround with Linux.
I have never used any Linux distribution, this is my first time, so I chose Ubuntu 'coz it's considered the easyest and the most windows-like (linux for human beings, sounds familiar?).

Before I do that, is there anything I need to know?
The PC will be mostly used for surfing, music, movies, occasional gaming (Linage, Fifa).

Also, I have some questions fo ya:
1) What is Edgy?
2) Is it hard to install Beryl and how do I do that?
3) Where do I find drivers for the mobo, video card and such?
4) Commands I need to know about?
5) My ISP gave me a dialer installer, can I use it in linux (under Wine)?
6) Windows-linux compatibility issues?

Tnx :)

---

### Post by banewman on 2007-10-12
OK - ubuntu names the releases as well as giving them numbers that correspond to the date of the release - edgy was released in april '06 and has a three year support cycle and is called 6.04 - feisty is the latest stable release and is supported for 18 months - gutsy is in development and will be released soon.
In edgy beryl is a downloadable package from the synaptic package manager but in feisty it is in the menu as desktop effects.
Ubuntu loads the hardware drivers during installation if they are supported - most are, the very new might give problems as the developers need time to get them working.
If you have problems the forums or google will soon let you know the commands needed - most common are sound and video issues and there are great tutorials here from the home page.
If windows is installed first then ubuntu will recognise it and give the option to boot into either - it is much harder if ubuntu is installed first then windows. :lolflag:

---

### Post by YannL on 2007-10-12
Hello,

Ok, 1st wait few days there is a new distro coming in like 7 days which should solved few user interface issue. (being resolution and refresh rate to start) Ubuntu 7.10

Ubuntu can do anything windows can that isn't the issue. 

To install Beryl you will have to follow a guide - they are plenty of those out there - Excepting if this is added into the next distro you will have to use command line to do this. (copy / paste ) to be honest with you Beryl is ok for 5 minutes then it become a tad "useless" ; it's still cool to play video and being able to rotate that cube with the video still playing. 

Linux use generic Drivers so you don't have to download them.. thats "windows" mind concept which is hard to get around but Linux doesn't "download" drivers. The only driver which need installing is the Video driver and for ATI I have to say I got no clue. I have a nice little program somewhere which auto install the correct video card I'll try to put my hand on it.

In theory you shouldn't need to know any command since it's "Ubuntu" but if you are to ever go to terminal to install anything the command are pretty self explanatory ; however the extension of those command aren't. For the time been I wouldn't worry about this.

I very much doubt the dialer is compatible with Linux. and program running in Windows do not natively work under linux. It's like trying to power a space rocket with diesel fuel.. it just ain't happening. Ubuntu should detect any network card / DHCP connection on that card. If you use a modem to connect to the Internet you will have to set the settings manually. 

6) Windows-linux compatibility issues?
A windows program won't run under linux so you will need an emulator which allow you to run games into linux.. but don't expect anything over 50% playability at best. for windows programs running in linux thats a total different story.

---

### Post by cwhitehouse on 2007-10-12
> **YannL said:**
> Hello,

Ok, 1st wait few days there is a new distro coming in like 7 days which should solved few user interface issue. (being resolution and refresh rate to start) Ubuntu 7.10

You can also download the beta now and install it.  Once the final version is out you can run the update tool and just get the changes which need to be applied to bring your system up to the final release version.

7.10 will also have Comp/Beryl installed by default so you won't need to worry about install them if you want eye candy.

Also, you will want to be prepared to download codecs after your install so you can watch videos and listen to music, as well as play DVD's.

---

### Post by mbeierl on 2007-10-12
The "dialer" is probably just a nice user interface on top of basic settings.  If you use cable or dsl, the pppoe configuration tool (a basic, command line one is pppoeconf) can handle it all for you.  The installation process itself might even autodetect it for you.  You'll just need to know your user name and password for your account with the ISP.

---

### Post by RedSquirrel on 2007-10-12
> **CoreOxide said:**
> 5) My ISP gave me a dialer installer, can I use it in linux (under Wine)?


If you are using a dial-up modem, that might be an adventure.

If you have ADSL or Cable, that's easy to setup.

This link should help with your internet connection:

[https://help.ubuntu.com/7.04/internet/C/connect-to-internet.html](https://help.ubuntu.com/7.04/internet/C/connect-to-internet.html)

---

### Post by CoreOxide on 2007-10-12
I am using cable connection...
I think I will also need the "number" to dial, which is cable.barak.net.il, won't I?

Will wait for 7.10 BTW :)

---

