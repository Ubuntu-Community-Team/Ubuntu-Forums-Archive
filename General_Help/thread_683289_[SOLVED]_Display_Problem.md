---
title: "[SOLVED] Display Problem"
date: 2008-01-30
forum: General Help
---

### Post by Newuser1111 on 2008-01-30
(It's not that laptop, it's a desktop computer that's in the same room.)
(And it's with 7.10 because that 7.04 CD wasn't really working anymore.)

I haven't installed it on this computer yet but I will.
Every thing's working(even the internet) but the display is wrong.
It should be 1024 x 768 but the only available ones are:
1280 x 960
1280 x 800
1152 x 768
800 x 600
640 x 480

---

### Post by Rocket2DMn on 2008-01-30
You mean from the LiveCD you can't get the correct resolution?  If that's your worry, just go ahead and install, and if for some reason the resolution still isn't correct after install, you would run
```
sudo dpkg-reconfigure xserver-xorg
```
That will ask you a bunch of questions about your hardware, just do your best to answer.  At the resolutions page use TAB to move and SPACEBAR to select your monitor's max resolution and everything less.  On the question about video driver, use "ati" if your card is an ATI or "nv" if your card is an nvidia.  After the questionnaire is complete you would then restart X with CTRL+ALT+BACKSPACE

---

### Post by Newuser1111 on 2008-01-30
Ok, so I'll just install it.

---

### Post by Rocket2DMn on 2008-01-30
Cool.

---

### Post by Newuser1111 on 2008-01-30
gparted keeps on having errors.
(I think that's it's name, or what ever that partition program is on the LiveCD.)

Is there a another way to edit the partitions?

I has two hard drives (A 40GB and a 80GB) and I want to put it on the 40GB drive but still keep Win98 and XP, (I mean that I want to have 3 OS's)
40GB- (D:\)Windows XP - WDC WD400BB
80GB- (C:\)Windows 98 - WDC WD800JB
The only special thing on 40GB is WinXP, 80GB has all the stuff I do not want to lose.

EDIT:
I'll try the 7.04 disk again.
So far, it's working.

---

### Post by Rocket2DMn on 2008-01-31
To resize a partition, you will need to open windows first and defragment that hard drive.  This will push everything to the front and make room for you to shrink that partition, thus opening space for a linux partition.
Why stick with windows 98 if you can help it?  You could move all your data to the windows xp drive and wipe 98 completely off.  In the least you can move your stuff over temporarily, wipe the drive, and partition the clean drive with the 2 linux partitions (root and swap, and even a 3rd /home if you want), and use the rest as an NTFS partition to store your data on.  Then you only have a dual boot to deal with.

---

### Post by Newuser1111 on 2008-01-31
I just "converted"(Not format!) the D:\ drive to NTFS and now it works!

Now the 40Gb has 2 partitions, NTFS and unnallocated.
So Ubuntu uses ext3 right?(I think that's the name.)


And BTW, I need to keep Win98 because the XP I have is an upgrade so if XP gets destroyed somehow, I would need Win98 to install XP.

And, this time, more sizes are there! Even 1024 x 768. So what did convertibg a FAT32 drive to NTFS have to do with the screen size?

And 1 last question:
What do I do here?
[http://playstationportablestuff.googlepages.com/UBUNTU_GPARTED.png]("http://playstationportablestuff.googlepages.com/UBUNTU_GPARTED.png")

Or do I just install Ubuntu and it'll do what ever it needs to that "unallocated"?

---

### Post by Newuser1111 on 2008-01-31
Sorry for double posting but I need to know the answer this:
What do I do here?
[http://playstationportablestuff.googlepages.com/UBUNTU_GPARTED.png]("http://playstationportablestuff.googlepages.com/UBUNTU_GPARTED.png")

because the Install comes up with something similar.


Nevermind.
When everything is working and Ubuntu is installed, then I'll mark this thread as solved.

---

