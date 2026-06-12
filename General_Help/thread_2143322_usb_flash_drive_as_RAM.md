---
title: "usb flash drive as RAM"
date: 2013-05-08
forum: General Help
---

### Post by greatsirkain on 2013-05-08
Few years back I asked about using a USB stick as RAM (not sure if it was on this forum [looked but couldn't find me] and back then it would have been an old version of Ubuntu not Lubuntu I was using) and everyone said it was pointless because they ran at pretty much the same speed as the hard drive, both of which were A LOT slower than RAM.

I'm using the same set-up now as I was in 2005 (I'm poor, sue me :P ) 2.8Ghz cpu with 512mb RAM but when using windows 7 I can use a USB with 'readyboost' (1.2GB atm) as RAM because it is faster than the HDD pagefile (according to to some). Speed has improved alot but that OS on this system was painfully slow anyway (until I stripped it & added the USB).

I understand linux is a totally different (sexier) animal, what with swap partitions and all but has the situation changed, could I gain any advantage by/is there any way of doing this with the Ubuntu family?

---

### Post by 25tom on 2013-05-08
Personally I would always go for a swap partition on your HDD rather than on a USB, as it would likely be faster on the HDD and would wear out the USB relatively quickly. I have only 465 MiB of RAM, and a very old CPU, so I suffer from slowness a lot on regular Ubuntu! However, a 1GiB or so swap partition helps out. Having Lubuntu should run fine, it's what I do when I need a speed boost, and it runs fine, not too slow.
Hope this helps :)

---

### Post by oldfred on 2013-05-08
Post #14 some flash drives that did not work
[http://ubuntuforums.org/showthread.php?t=2120196](http://ubuntuforums.org/showthread.php?t=2120196)
More tests Flash drives post #5 -  C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=2130234](http://ubuntuforums.org/showthread.php?t=2130234)


 sudo hdparm -tT /dev/sda
Using this command, I get for Timing buffered disk reads MB/Sec
30.9 USB2 flash on USB2 port
34.4 USB3 flash on USB2 port
69.9 hard drive older
184.9 SSD (cheaper OEM)

---

### Post by greatsirkain on 2013-05-08
Lubuntu is quick (not quite as quick as it was, I've had to start removing things ([that's when it starts to go downhill] and the newer versions recognise less hardware {I might as well just get Ubuntu 12.04 and alter it if that's what I'm going to have to do anyhow}) and at the moment I have lubuntu live, ubuntu live, tails (which still doesn't work) and win7 all on the same pc with a 200gb sata and a 250 gb ide (ata?) + 1 4gb usb & 1 1gb usb. Not to mention the numerous live OS on USB/DVD and countless repair cds...You have to on something this old. :P

Thing is, I want to be able to make one master install USB that will maximise the ability of the hardware provided. I'd like to take games into account but it's too early to do that. I'd like to take price into account but it's unfair to do that. I want the Top Gear approach, raw power. 

Main thing I use my computer for is repairing, building other computers. Ooo and watching dubious streaming media before it even becomes illegal to do that too. 
Privacy and speed are the main factors.

---

### Post by greatsirkain on 2013-05-08
Soooo SSD's are the way to go?...& MS are full of...The usual.
Cheers Fred.

---

### Post by greatsirkain on 2013-05-08
Where has 'mark this thread as solved' gone from thread tools? N/m found it in edit post....Nobody likes change whoever decided to alter the forum 'ever so slightly' but just enough so that nothing was where it should be. It's like when the super market moves stuff to make you buy more and all it does is make you leave annoyed.

---

