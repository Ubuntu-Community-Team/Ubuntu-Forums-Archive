---
title: "Dual boot slowing Ubuntu?"
date: 2012-10-28
forum: General Help
---

### Post by telcodave on 2012-10-28
First post here!

I have recently installed Ubuntu 12.10 (first time using) and installed it along side Windows XP giving me a dual boot option.  I am really enjoying Ubuntu, but, it seems very sluggish, especially when opening things like the software center, settings, almost everything when opening.  I have it installed on a small HP mini laptop (not all that powerful), is it possible that still having Windows XP installed is slowing things down?

Also, I have another computer so having just Ubuntu on the HP is ok if it will speed things up.  Can I remove the Windows without reinstalling Ubuntu and selecting replace windows instead of run along side?

Hopefully this all makes sense, just want faster and smoother out of Ubuntu.

thanks,,,,

---

### Post by howefield on 2012-10-28
Having XP on the machine is not likely to slow Ubuntu down, (unless you have a Wubi install).

Have you checked for additional drivers, you may need a proprietary graphics driver for best performance.

---

### Post by telcodave on 2012-10-28
Maybe should have posted in the total newbie section...

What is a Wubi install?

How can i find graphics drivers?  when i check, it does not even show a graphics driver.

---

### Post by howefield on 2012-10-28
A Wubi install is where you install Ubuntu to a file that resides on top of the windows file system, but gives you a dual boot option at startup. 

You'd likely know that you had done that, so if your install is on its own partition XP won't be slowing it down.

Open the dash and search for Software Sources and you'll find the Additional Drivers tab in there. Does it suggest any graphics drivers ?

---

### Post by telcodave on 2012-10-28
thanks and yes it does, quite a few of them.  just applied a "proprietary, tested" NVidia driver.   lets see if that helps....

---

### Post by Rebelli0us on 2012-10-28
Having XP on your disk is NOT going to slow down your computer.  Ubuntu 12.10 is more suitable for newer machines, but you can try more lightweight versions like Lubuntu or Xubuntu.

---

### Post by gordintoronto on 2012-10-28
What CPU is in the computer? How much memory? The first screen of "details" should give you this information.

---

### Post by telcodave on 2012-10-29
here are the specs:

Memory 1.7GiB
Processor Intel® Atom™ CPU N270 @ 1.60GHz × 2
Graphics Unknown
OS Type 32-bit
Disk 51.5 GB

These specs are straight from the details screen

---

### Post by Bartender on 2012-10-29
You've got enuf RAM, but an Atom processor is underwhelming.  Have you figured out if this is [Wubi]("http://askubuntu.com/questions/190334/how-do-i-know-if-i-am-running-wubi-or-a-proper-dual-boot"), or a true dual-boot?

---

### Post by telcodave on 2012-10-29
it is a true dual boot.

---

### Post by COMECON on 2012-10-29
Then Windows XP isn't definitively the origin of the slowing issue. With the propietary drivers, are you still having problems?
You could also open the System Monitor and see how many RAM and CPU is Ubuntu using, and tell us?
Thanks!

---

### Post by oscarivera9 on 2012-10-29
> **Rebelli0us said:**
> Having XP on your disk is NOT going to slow down your computer.  Ubuntu 12.10 is more suitable for newer machines, but you can try more lightweight versions like Lubuntu or Xubuntu.

I agree 100%, I have an older Dell Precision  360 with Windows XP and when I first started using Ubuntu I had no problems at all.  In fact, Ubuntu 10.04 was faster than Windows XP at first.  However, when Ubuntu 11.04 came out (and introduced Unity), my Dell began to have problems running Ubuntu.  Eventually I decided to go with Xubuntu and everything's been smooth ever since.  I currently have Xubuntu 12.04 on the Dell and it still has Windows XP.  Xubuntu is faster than XP!
You see, the thing is that the newer Ubuntu releases are meant to be used with newer PCs because of the Unity desktop environment.  Or at least you need a semi-decent graphics card.  So the best choice would be to switch to either Xubuntu or Lubuntu, both of which are great operating systems.

Another thing, how much swap space are you using?  That may be affecting things also.

---

### Post by telcodave on 2012-10-29
CPU1 & CPU2 are ranging between 9.3%-16.0%
Memory 25.1% (441.8MiB)

By the way thanks for all the help.

---

### Post by telcodave on 2012-10-29
Swap space is showing 0.0%........does that seem right?

---

### Post by oscarivera9 on 2012-10-30
Everything seems normal, but like I said a big part of it deals with your graphics card. 
Try running a Live Xubuntu or Lubuntu disc to see how slow that feels in comparison to what's already installed.  Keep in mind that running an operating system from a Live CD will always be slower than the real thing.

---

### Post by gordintoronto on 2012-10-31
One possible cause of slowness is if your hard drive is going South. If you run the program "Disks" there is a gear in the top-right corner of the window. Click on it and select "smart data," and it should display the health of your hard drive. (This is in Ubuntu 12.10, the details might be slightly different in 12.04.)

Are you getting the CPU usage from System Monitor? I would expect it to jump up as you load Software Center. An Atom is pretty low performance.

---

### Post by Champlin93 on 2012-10-31
Does your computer run good after installing the drivers? If it's still slow you might consider installing a lightweight desktop environment like XFCE. It looks ugly and old at first but you can customize it to look pretty nice.

---

### Post by COMECON on 2012-10-31
Definitely, it seems that Unity isn't great with your system. I'd recommend you using either Xubuntu or Lubuntu. You can try XFCE at your actual Ubuntu installing the **xubuntu-desktop** package from the software center or at the Terminal (*Dash >> Terminal*):
```
$ sudo apt-get install xubuntu-desktop
```
Then close your session and, when the login screen appears, select Xubuntu Desktop as your session.

---

### Post by oscarivera9 on 2012-10-31
> **COMECON said:**
> Definitely, it seems that Unity isn't great with your system. I'd recommend you using either Xubuntu or Lubuntu. You can try XFCE at your actual Ubuntu installing the **xubuntu-desktop** package from the software center or at the Terminal (*Dash >> Terminal*):
```
$ sudo apt-get install xubuntu-desktop
```Then close your session and, when the login screen appears, select Xubuntu Desktop as your session.


This is precisely what lots of us here seem to agree on, Unity is too much for your computer to handle & a lightweight desktop environment should help speed things up a bit.  The suggestion that COMECON gave is great because you don't have to install Xubuntu, you are only installing the Xfce desktop environment.  Once it's installed, then all you have to do is select which desktop environment you want to use when you are about to log in.  If you decide you don't like Xfce, then simply log off and log back in using Unity. 
This is by far the best solution yet........if it works (and please let us know what works, that way others with your hardware can find answers in the future thanks to you :)  ).

---

### Post by COMECON on 2012-11-01
> **oscarivera9 said:**
> This is precisely what lots of us here seem to agree on, Unity is too much for your computer to handle & a lightweight desktop environment should help speed things up a bit.  The suggestion that COMECON gave is great because you don't have to install Xubuntu, you are only installing the Xfce desktop environment.  Once it's installed, then all you have to do is select which desktop environment you want to use when you are about to log in.  If you decide you don't like Xfce, then simply log off and log back in using Unity. 
This is by far the best solution yet........if it works (and please let us know what works, that way others with your hardware can find answers in the future thanks to you :)  ).

Yep! If you feel confortable and like the XFCE environment, you can just install a fresh Xubuntu installation, because having multiple desktop environments have some cons also, for instance you'll have some non-lightweight programs installed that came with the Unity version, but those aren't on a fresh Xubuntu installation.

---

