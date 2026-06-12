---
title: "Rabbit TV Pen Drive Will Not Mount 14.04.3"
date: 2015-10-25
forum: General Help
---

### Post by coljohnhannibalsmith on 2015-10-25
Hello,

I just purchased a couple of Rabbit TV pen drives from Amazon at an excellent discount; and the products works extremely well in the Windows environment. The product literature does only list Windows and MAC compatibility. Being an experienced Linux user and having Wine installed, I thought I would just insert the pen drive into an available USB port and install it with Wine; no big deal. This turned out not to be the case. Not only would the device not mount; but it showed-up unmounted in Computer as a CD/DVD ROM drive; odd! Well, it turns out that in Windows that the product doesn't actually install. It has to be started from the pen drive each time; not that strange; but definitely something to take note of. Well, I'm guessing that the drive shows up in Ubuntu as a CD/DVD ROM drive because the device has been formatted as ISO9660. This could probably be have been done in a tool such as UNetBootin; still not that strange; but the fact that it won't mount is. I presume some of this behavior can be explained by the device being write-protected; again not that strange; but could the device also be read protected as well, with just execute permission being enabled? This seems like the most likely scenario. I am however surprised that Ubuntu can't do "anything" with it; especially if the file system is '9660.

Does anyone understand this a little better?

Thanks, Hannibal

---

### Post by Vladlenin5000 on 2015-10-25
According to [this]("http://www.digitaltrends.com/home-theater/rabbit-tv-real-deal-or-swift-swindle/"), Rabbit TV is phasing out the dongle and moving to a web only "service". So, irrespective of the price you payed, it was a waste of money. You said you bought it at Amazon?!? Haven't you read the customer reviews? They say it all: [http://www.amazon.com/Telebrands-6686-6-Rabbit-TV/dp/B00AWC51DW](http://www.amazon.com/Telebrands-6686-6-Rabbit-TV/dp/B00AWC51DW)

The dongle is just a flash drive with software inside; said software is for Windows and MacOS only as you certainly realized already.
The bad news: It won't work in Linux, period.
More bad news: The chances of it NOT even working in the browser are huge, considering the problems we've been experiencing with similar "services" requiring Flash and/or Microsoft Silverlight (and other issues). Granted, it could have been a temporary glitch but my FF froze when I tried to open their homepage.

---

### Post by coljohnhannibalsmith on 2015-10-26
It seemed to work fine with MS Edge. My only concern is that Linux couldn't read the FS.

---

### Post by stalkingwolf on 2015-10-26
there is no need for the USB dongle . hasnt been for at least a year.   rabbit tv is now and has been for some time browser based.  just go to the website and log in

---

### Post by Vladlenin5000 on 2015-10-26
@stalkingwolf

Have you tested it in Linux already? Some workaround required or not (like with Netflix and a few others)?

---

