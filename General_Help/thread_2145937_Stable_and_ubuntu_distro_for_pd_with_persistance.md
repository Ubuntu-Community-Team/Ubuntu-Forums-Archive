---
title: "Stable and ubuntu distro for pd with persistance ?"
date: 2013-05-17
forum: General Help
---

### Post by bareminimumayush on 2013-05-17
I have been using ubuntu about a year now(glad a switched from windows) and one thing I love about it is Usb booting with persistance storage.
Its quite handy and I have used it quite a fair few times at my friends place or at college.But I have one weird problem that I faced was ,after a few days of working perfectly the pd went corrupt that I couldn't boot with it. I have tried with Ubuntu 12.10,Linux mint Maya(13),Nadia(14).I thought that maybe they were too heavy to boot from usb so i Switched to relatively old Linux mint Isadora(9).But same result again.I also tried Puppy linux,and well,it worked fine without crashing but the interface was not to my taste and i still have very basic knowledge about terminal.

So friends,please suggest a fast,slick(as booting time was very slow with the distro I have tried ), stable and preferably an ubuntu version of an distro to run on pd.  
Also mentioning the software to create bootable pd with also be appreciable.
Currently I am posting this with Ubuntu 12.10 on my desktop.
So friends please help.
And sorry for my messy english.

---

### Post by Megaptera on 2013-05-17
Useful article here, an Ubuntu install on USB (pen drive) in one partition, plus a seperate data partition on same USB [http://www.howtogeek.com/97177/how-to-put-ubuntu-linux-on-a-usb-thumb-drive-without-the-mess/](http://www.howtogeek.com/97177/how-to-put-ubuntu-linux-on-a-usb-thumb-drive-without-the-mess/)

Hope this helps?

---

### Post by bareminimumayush on 2013-05-17
Actually Megaptera thanks for the help.I am sure to use this in future.
But actually my problem is different, I was hoping that someone would tell me which distro to use?
Like is lubuntu or kubuntu stable while running on pd?
Please help

---

### Post by zemega on 2013-05-17
Either is fine, its all depends on the system you're going to use it. Ubuntu 13.04 is faster than 12.04. Some computer can only accept 32 bit, some 64 bit and some both. So maybe 1 USB drive is not enough. Undoubtly, Lubuntu has the lowest requirement needed. Xubuntu is better though. If its old computer, and does not have PAE support, 13.04 probably would not work. 

I don't use persistant disk anymmore. I just use a full install on a thumbdrive these days. First thumbdrive is to be the startup drive. then use that startup drive to install on another thumbdrive. Even though its called its persistance, its only temporary, sooner or later the persistant space will run out, actually its quit soon, its because each write and delete use up the persistance space. A full install on a thumbdrive is just like a full install on a harddisk. That is why a full install on a USB drive is better than persistant. You can even make a full install on external HDD as well. Full install will not go corrupt after a few days (it only goes down when the USB itself is broken), persisntance will.

The trick to perfomance here, the tumbdrive capacilitites is what limiting your perfomance. You need to get a thumbdrive with fast write and read speed. Most thumbdrive write speed are marked as 10MBps or 30MBps, but that is for sequential write/read (for larger files). You will need good 512k and 4k read and write speed. If you get one with low speed on 521k/4k write/read speed, constant freezing will occur. Disable journalling system as well. Essentially any drive that is good for ReadyBoost (win 7) would work wonder and fast. Even better get those with USB 3.0.
The brand Sandisk is pretty good to me, get the one adverstised for speed. Sandisk Pop is bad for this though.

Edit: Install Unity Tweak Tool afterward, and remove transparency, opacity or blurr effect. It will still look nice, but faster. Its like removing Aero transperecy from Win 7 Aero.

---

### Post by bareminimumayush on 2013-05-17
Thanks zemego.I hope this solves my problem.I will post back as soon as I try it.
thanks a lot.

---

### Post by bareminimumayush on 2013-05-17
Also forgot to mention,any further suggestions would be quite welcome.

---

### Post by bareminimumayush on 2013-05-18
> **zemega said:**
> Either is fine, its all depends on the system you're going to use it. Ubuntu 13.04 is faster than 12.04. Some computer can only accept 32 bit, some 64 bit and some both. So maybe 1 USB drive is not enough. Undoubtly, Lubuntu has the lowest requirement needed. Xubuntu is better though. If its old computer, and does not have PAE support, 13.04 probably would not work. 

I don't use persistant disk anymmore. I just use a full install on a thumbdrive these days. First thumbdrive is to be the startup drive. then use that startup drive to install on another thumbdrive. Even though its called its persistance, its only temporary, sooner or later the persistant space will run out, actually its quit soon, its because each write and delete use up the persistance space. A full install on a thumbdrive is just like a full install on a harddisk. That is why a full install on a USB drive is better than persistant. You can even make a full install on external HDD as well. Full install will not go corrupt after a few days (it only goes down when the USB itself is broken), persisntance will.

The trick to perfomance here, the tumbdrive capacilitites is what limiting your perfomance. You need to get a thumbdrive with fast write and read speed. Most thumbdrive write speed are marked as 10MBps or 30MBps, but that is for sequential write/read (for larger files). You will need good 512k and 4k read and write speed. If you get one with low speed on 521k/4k write/read speed, constant freezing will occur. Disable journalling system as well. Essentially any drive that is good for ReadyBoost (win 7) would work wonder and fast. Even better get those with USB 3.0.
The brand Sandisk is pretty good to me, get the one adverstised for speed. Sandisk Pop is bad for this though.

Edit: Install Unity Tweak Tool afterward, and remove transparency, opacity or blurr effect. It will still look nice, but faster. Its like removing Aero transperecy from Win 7 Aero.


Really Really thanks zemega, you are a life saver.Honestly I never gave it a thought before for full installation ,but your method worked like a charm.Had to google a bit about it,but after doing it ,as a plus point,I am all the more confident partitioning,something which I was virtually afraid to do before.
Thanks a lot,Friend.

(Hope my english is ok)

---

