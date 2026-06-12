---
title: "Turn old desktop to a media player"
date: 2013-11-12
forum: General Help
---

### Post by david98 on 2013-11-12
Hi everyone iv'e just found my old tower in my loft which I want to turn into a media player to connect to my hd television. The spec's are minimal and am wondering which OS will be best to suit my need's. These are the spec's of the tower motherboard MSI K8MM3-V (MS-7181) ,processor AMD sempron 64 3000+ 1.8ghz, Memory 2gb, graphics gigabyte ATI Radeon hd 4650 1gb AGP graphic's card am also going to install a sound card and a wireless card. Like I said the spec's are quite minimal but all I want to do is play music watch film's not through streaming and maybe a little light use net surfing ie youtube,facebook,gmail so what light use os would you recommend to stop this old tower from going in the scrap heap.:o

---

### Post by ibjsb4 on 2013-11-12
Your video card seems to be still supported.

[https://help.ubuntu.com/community/RadeonDriver#Fully_Supported](https://help.ubuntu.com/community/RadeonDriver#Fully_Supported)

Since you do not care about bells and whistles I would go for the less resource hungry [Lubuntu]("http://www.lubuntu.net/").

Edit:  I have installed both L & Xubuntu on a Intel 1.7Ghz machine and found that Lubuntu was snappy and Xubuntu was not (there were hesitations).

---

### Post by Werne on 2013-11-12
Socket 754? Well that's something I haven't seen in a while. Anyway, OS - that thing should handle Xubuntu well, the CPU is not so great and it may prove as a bottleneck in Unity. Though I personally use Debian with deb-multimedia repo for my HTPC, *buntu ain't bad either and I use it in "for sale" multimedia machines since it's easier to set up with all the codecs and stuff. If Xubuntu proves as too heavy, you can get Lubuntu and run it on Openbox instead of LXDE. There are lighter distros like Slitaz that would be quite snappy on that hardware, but they sometimes tend to lack certain codecs and stuff.

I'm not much of a help in the software department, I'm more of a hardware guy. And with that in mind, I'd advise getting an aftermarket cooler for the CPU (if there isn't one on it already) and a different fan for the graphics card. Stock AMD CPU fans are noisy even as new, I threw mine away as soon as I bought the CPU, there are still coolers for socket 754 (like Arctic Cooling Freezer 13 I use) and they're cheap, so there's no problem getting one. And that card has a small fan that also counts as noisy, which should be disconnected and instead you can get an 80mm fan, like Arctic Cooling F8 with a thermal sensor (you can place that sensor on the heatsink to control fan speed based on the temperature), to blow over the card's heatsink.

All in all, that thing can see a few more years of service and serve you well, it's still not ripe for the scrap. ;)

---

### Post by david98 on 2013-11-12
Thank's werne did notice the fan's where a bit loud so am going to upgrade them. I had never seen a socket 754 for a while this was 1 of my first build's and was a little blast from the past. Think am going to use Lubuntu and see how it goes. I myself have a little knowledge on hardware as regularly sell system's but never even seen a 939 socket for a while never mind 754. I usually just deal with intel 775 socket's but once I took this system out of the loft I thought what a waste just binning it so I put it in a small black case and thought id us it to play film's on. Am going to try lubuntu and see how it play's film's with VLC player I may as well breath some new life in it as there's too many computer's getting disposed of even though they have a little life left in them.

---

### Post by Mark Phelps on 2013-11-12
Just so you know, while the default Radeon open-source driver may provide all the graphics power you need, unfortunately, AMD dropped fglrx driver support for that video card over a year ago.  That means there are no restricted Radeon drivers that will work with that card and any Ubuntu version newer than 12.4.01.

---

### Post by david98 on 2013-11-12
Thank's for the head's up mark phelps. iv'e got a few agp card's but they are all getting dropped and rightly so. But am hopeful the default open source will do what I need.

---

