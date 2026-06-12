---
title: "Curiosity of why 10.04 will work and not 14.04 on a certain hardware"
date: 2014-05-07
forum: General Help
---

### Post by AfrikaDietmar on 2014-05-07
Hi Ubuntu Community,

I'm curious to know what could be the reasons why the Ubuntu OS 10.04 is more tolerant to operate on a mother board: [COLOR=#000000][INDENT][COLOR=#000000]ASUS P8H61-PRO (Intel H61 Chipset)[/COLOR][/INDENT]
[/COLOR]
While other versions such as 12.04 - 14.04 will deliver the black screen of death with the blink. 

What is it that is different with those Ubuntu architectures that they will not tolerate such a main board?
The question arises especially since Ubuntu 10.04 does work but the newer ones don't.

I'm not looking for a fix, but rather curious what could be the cause of such differences.

Here are also some references of my posts in the past where I struggled to fix it but failed in vain and come to accept that the newer Ubuntu releases just don't work on this Windows7 optimised mainboard:
[http://ubuntuforums.org/showthread.php?t=2146906](http://ubuntuforums.org/showthread.php?t=2146906) 
[http://superuser.com/questions/324921/cant-install-ubuntu-64-bit-on-my-asus-destop ]("http://superuser.com/questions/324921/cant-install-ubuntu-64-bit-on-my-asus-destop") 

Looking forward for your replies!

---

### Post by Bucky Ball on 2014-05-07
*Thread moved to **General Help**.*

... and I'm curious to know why you posted this in ***Programming Talk*** ... You stand a better chance here. 

14.04 LTS is quite a bit more demanding on hardware than 10.04 LTS was (four years ago, and that is a long time in technology). Perhaps try Xubuntu or Lubuntu or another, lighter flavour and see how you go ... Good luck. ;)

---

### Post by Bucky Ball on 2014-05-07
*Thread moved to **General Help**.*

I'm curious to know why you posted this in Programming Talk ... You stand a better chance here. 

14.04 LTS is quite a bit more demanding on hardware than 10.04 LTS was (four years ago, and that is a long time in technology). Perhaps try Xubuntu or Lubuntu or another, lighter flavour and see how you go ... Good luck. ;)

---

### Post by monkeybrain20122 on 2014-05-07
Well what is your graphic card? I had an old laptop with a very old Nvidia card that only 10.04 worked, even 10.10 didn't because Nvidia pulled the support and noveau happened to have a bug for that card since the big bang and it was sort of forgotten.

---

### Post by AfrikaDietmar on 2014-05-07
This is my PC Specs:
[COLOR=#000000][COLOR=#000000][COLOR=#000000]PC Specs: CORE I5-3470 3.2/3.6 GHz Turbo, 6MB Cache, ASUS P8H61-PRO (Intel H61 Chipset), DVD LGA1155, RAM Dual Channel 2 x 4 GB DDR3 1333, 500 GB Hard Drive SATA[/COLOR][/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000][COLOR=#000000]Power: Cooler Master 625W Extreme2[/COLOR][/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000][COLOR=#000000]Graphic Card: ASUS GT620 (Connected 2x 24" LED LCD Viewsonics, one on HDMI one on the blue connector)
8 GB Ram

It's not really that old stuff. I don't see what is the relationship with the demand of 14.04 and not being able to operate with such hardware. I posted in the programming section considering that Ubuntu has been programmed in a way not supporting such type of mother board. My curiosity is what has been done to the newer Ubuntus to make it NOT work on such hardware while older releases do. You can keep my post in General Help wherever as an admin you deem seem fit best. But I just want to get the discussion started for general interest and as a Ubuntu fan.


[/COLOR][/COLOR][/COLOR]

---

### Post by kc1di on 2014-05-07
The biggest change between 10.04 and later versions it that Xorg Changed and many video drives would no longer work without a rework in the newer version. If your card depends on propriety drivers it would have been up to the manufacturer to update their drivers to work, nvidia and some others eventually did that.  So it's not Ubuntu's fault. If that's the case, they are not allowed to change propriety drivers. 
That being said your ASUS gt620 is really a Nvidia GT620 and should be able to use the Nvidia 331 driver.  See if that one is installed.  if not install it in a terminal by typing the following ```
sudo apt-get update
sudo apt-get install nvidia-331
```

---

### Post by AfrikaDietmar on 2014-05-07
Hi kc1di,

there is no way to access the terminal because Ubuntu cannot be installed. I even tried taking a hard drive from a working PC that has 14.04 running on it and placed it in that PC which had a similar graphic card and it didn't work. It's more main board related. At least it should have been running in a low graphics mode but as said above I get the black screen of death with the blink. The mainboard [COLOR=#000000]ASUS P8H61-PRO (Intel H61 Chipset) also has written on it optimised for Windows7 and on twitter someone recently also told me its more mainboard related :/
[/COLOR]
But still Ubuntu 10.04 will accept to work on this mainboard, but the newer ones deliver the black screen of death. I also tried minimal ubuntu, from CD, usb sticks, original cd ordered from ubuntu etc. The graphic card problem is popular but what about the mainboard?

---

### Post by kc1di on 2014-05-07
Ok my mistake thought it was installed already , but in that case try booting in nomodeset parameter. 
insert live, dvd/usb stick when it begins to boot hit and hold down the left shift key
that should take you to a screen with a list of f key options at the bottom. select f6 and from that menu select nomodeset  hit esc and enter see if it will boot.
if it boots do the install and you will have to install the 331 driver after the install is complete.

P.S. very seldom will removing a H.D. from one machine and putting it in other work, because the setup, drivers & other parameters are set at install and would have to pretty much match exactly for that to work.

---

### Post by AfrikaDietmar on 2014-05-07
That's already been dealt with here: [http://ubuntuforums.org/showthread.php?t=2146906](http://ubuntuforums.org/showthread.php?t=2146906) as whatever options are selected will lead to the black screen with the blinker even with minimal ubuntu it will crash when it comes to the part of loading [COLOR=#000000]"Detecting disks and other hardware" there it just hangs/freezes and stops. But 10.10 works though, I wonder why Ubuntu 14.04 doesn't and if next releases will ever do...[/COLOR]

---

### Post by AfrikaDietmar on 2014-05-08
So, considering that the mainboard is the culprit what do you think could be the change in the newer versions that leads them not to accept or to crash while the older ubuntus such as 10.10 will tolerate and run on such a mainboard? (Ref: [COLOR=#000000]ASUS P8H61-PRO (Intel H61 Chipset)[/COLOR] )

---

### Post by sudodus on 2014-05-08
There is probably some hardware driver, that lost the compatibility with your hardware when it was modified to work with newer hardware.

In such cases, you might have better luck with some other linux distro. Particularly because your computer is fairly new, you could have better luck with another distro. The first alternative I would try is ***Knoppix***, which is known to be good at recognizing hardware.

---

### Post by AfrikaDietmar on 2014-05-22
Thanks for the Knoppix tip but that will not do. I need Ubuntu itself to work as I need another large series of other associated programs to run with it. Is there no was we can get Ubuntu to reinclude the drivers for that mainoard for the october 14.10 release?

---

### Post by sudodus on 2014-05-22
OK, it is important to run Ubuntu. Then I suggest that you explore the method with boot options. Try with both 12.04 LTS and 14.04 LTS.

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Try all the suggested boot options suggest at F6, but also some other boot options that you find at the end of the link above or at this link

[Kernel Parameters]("http://www.kernel.org/doc/Documentation/kernel-parameters.txt") - An exhaustive list of kernel boot parameters from kernel.org

---

### Post by AfrikaDietmar on 2014-05-22
Those versions don't work. I only got 10.04 to work. Tried for weeks a lot of options. I also inserted once a hard drive with ubuntu 14.04 already installed on it. That didn't work. A driver must be missing or not working with the main board but I don't know how to fix that.

---

### Post by sudodus on 2014-05-22
> **AfrikaDietmar said:**
> Thanks for the Knoppix tip but that will not do. I need Ubuntu itself to work as I need another large series of other associated programs to run with it. Is there no was we can get Ubuntu to reinclude the drivers for that mainoard for the october 14.10 release?

The developers seldom read threads at the Ubuntu Forums. You can reach them via IRC or via bug reports at Launchpad.

> **AfrikaDietmar said:**
> Those versions don't work. I only got 10.04 to work. Tried for weeks a lot of options. I also inserted once a hard drive with ubuntu 14.04 already installed on it. That didn't work. A driver must be missing or not working with the main board but I don't know how to fix that.

That is too bad. What programs do you need? If you list them, we might be able to suggest how you can try running them in another linux distro or try some alternative program.

There is also another option:

- Make a dual boot system with Ubuntu 10.04 LTS and a current linux distro that works in your computer (Knoppix?)

. Use Ubuntu 10.04 LTS for the Ubuntu specific programs that you need, but do not connect to the internet, or at least be very careful, because some of the program packages (the desktop ones) are no longer supported. The basic Ubuntu packages in common with Ubuntu Server are supported until April 2015.

. Use the current linux distro when you want to connect to the internet.

---

### Post by fantab on 2014-05-23
> **AfrikaDietmar said:**
> Thanks for the Knoppix tip but that will not do. I need Ubuntu itself to work as I need another large series of other associated programs to run with it. Is there no was we can get Ubuntu to reinclude the drivers for that mainoard for the october 14.10 release?

Knoppix is a good recommendation. Try it. If it recognizes your hardware and boots then 'other' distros may work as well.
Keep this Knoppix '[cheat sheet]("ftp://ftp.uni-kl.de/pub/linux/knoppix/knoppix-cheatcodes.txt")' handy. And try the options in case knoppix doesn't boot.

AFAIK there is no 'ubuntu specific' software out there. If you can boot and install any other latest OS, then why not?

For the life of me I couldn't install Ubuntu 11.04 on my same desktop which has had Ubuntu 9.10 to 14.04. So it could be just one of those things. 
Have you tried updating BIOS?... BIOS updates solve many harware issues. Check the Mobo website for newer versions of BIOS...
Can you look in the BIOS and tell us what mode is SATA set to? It should be AHCI.

---

