---
title: "MUnity problem-your 12.04 is running in 2d mode many features unavail-help!"
date: 2014-03-16
forum: General Help
---

### Post by drew14 on 2014-03-16
I was advised to download MUNITY ,but the box comes up w this message , MUnity message- your 12.04 is running in 2d mode Many features will not be available.  Is it my computer?  ub 12.04/ Intel Atom cpu 1.33 / 2g mem /32 bit / 18 gig     thanks for any and all help ( yup, im new)

---

### Post by 3rdalbum on 2014-03-16
Unity 3D should be able to run on your computer. Log out, click the little Ubuntu logo near your name, and choose 'Ubuntu' ( instead of 'Ubuntu-2D'). Log in again and all should be okay.

---

### Post by drew14 on 2014-03-16
i did what you said, and clicking on ubuntu (instead of ubuntu2d, which I never had done earlier), and it brought me right back to the same warning. Seems im locked into 2d,even though logging back in under either choice doesnt make a difference. Im seriously thinking its my pc...but thanks again...if you come up with another solution, id appreciate and and all help. have a good day

---

### Post by deadflowr on 2014-03-16
Your cpu and ram are totally up to snuff to run Ubuntu.
However, it would seem that your graphics card is having some issues.
This can be because it is either not strong enough for Ubuntu's 3d effects.
Or it can be because the driver in use is not the best the card can use.

Having read your other posts, I understand you will need a little help to figure out what card you have.

If Ubuntu's details section was helpful, I would point you toward that.
Unfortunately, it is usually not helpful, and will probably only say unknown, or even worse vesa
(Which is as good as saying nothing at all, as far as I am concerned)

So, we will look to using the command line.
Ubuntu uses a command line interface that we will terminal.
To open a terminal in Ubuntu go to the Ubuntu menu.
(It is the top icon on the left side panel thingy. It should have Ubuntu's logo in it)
Once you open the menu(known as the dash)
use the search box and enter "Terminal"
this should bring up the terminal program, select it to open.

Now enter this command
```
lspci -nnk | grep -iA3 vga
```

and copy what it says and paste it in a post in this thread.
That will tell us what card you have and maybe it will be possible to install a better driver, or something to that affect.
(You can use the right click on your mouse to copy and paste)

---

### Post by drew14 on 2014-03-16
```
drew@ubuntu:~$ lspci -nnk | grep -iA3 vga
00:02.0 VGA compatible controller [0300]: Intel Corporation System Controller Hub (SCH Poulsbo) Graphics Controller [8086:8108] (rev 07)
	Subsystem: Acer Incorporated [ALI] Device [1025:0244]
	Kernel driver in use: gma500
	Kernel modules: gma500_gfx
drew@ubuntu:~$
```

wow, I did something useful, hope this helps you help me...whats next?
  thank you

---

### Post by deadflowr on 2014-03-16
Don't know much about the card other than it is one of the more interesting ones(poulsbo)

Here's a thread on it
[http://ubuntuforums.org/showthread.php?t=2107593&highlight=poulsbo](http://ubuntuforums.org/showthread.php?t=2107593&highlight=poulsbo)

and here's a wiki about it bodhi-zazen pointed to in post 4

[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo)

Seems like an interesting card.

Good reading for you anyway.

---

